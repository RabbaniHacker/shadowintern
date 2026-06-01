# 🏗️ ShadowIntern — Architecture

## Agent Pipeline Overview

ShadowIntern uses a 5-agent sequential pipeline. Each agent builds on the output of the previous one.

---

### Agent 1 — Company Intelligence Agent

**Input:** Company name (e.g. "Razorpay")

**Data Sources:**
- GitHub org repos → coding style, tech choices, PR patterns
- Official tech blog → architectural decisions, scale problems solved
- Job descriptions (last 3 years) → required skills, language, values
- Glassdoor interview reviews → actual questions asked, process details
- LinkedIn posts by engineers → culture signals, what they talk about
- YouTube talks / conference talks → how they explain systems

**Output:** Structured `CompanyDNA` object
```json
{
  "company": "Razorpay",
  "primary_stack": ["Go", "Java", "Kafka", "MySQL", "Redis"],
  "architecture_patterns": ["event-driven", "microservices", "idempotency-first"],
  "scale_context": "5M webhooks/day, 99.99% uptime SLA",
  "known_problems": ["payment retries", "reconciliation", "fraud detection"],
  "culture_signals": ["ownership", "speed", "zero-downtime deploys"],
  "rejection_patterns": ["ignoring edge cases", "no error handling", "poor observability"]
}
```

---

### Agent 2 — Culture Modeller

**Input:** `CompanyDNA` object

**Process:**
- Maps stack → problem domains
- Identifies what the company values (speed vs. correctness vs. scale)
- Builds a "Senior Engineer Persona" for that company
- Identifies common rejection reasons from interview reviews

**Output:** `EngineerProfile` — a prompt-ready persona used by later agents

---

### Agent 3 — Task Generator

**Input:** `EngineerProfile` + week number (1–4)

**Progression:**
- Week 1 → Component-level tasks (build a rate limiter)
- Week 2 → Service-level tasks (design a retry queue)
- Week 3 → System-level tasks (webhook delivery at scale)
- Week 4 → Full system design (end-to-end with failure modes)

**Each task includes:**
- Problem statement (grounded in company's real domain)
- Constraints (matches company's actual scale/SLA)
- Evaluation criteria (what a senior there would check)
- References to real company engineering blog posts where available

---

### Agent 4 — Shadow Mentor

**Input:** Student's code/design + `EngineerProfile`

**Review style mirrors company culture:**
- Razorpay → strict on idempotency, payment edge cases, observability
- Google → strict on complexity, scalability proofs, readability
- Zepto → strict on latency, pragmatic solutions, operational simplicity

**Output:**
- Line-by-line code review in company's style
- Specific flags with severity (P0 / P1 / P2)
- "A [company] engineer would reject this because..." explanations
- Revised task if P0 issues found

---

### Agent 5 — Interview Simulator

**Input:** `EngineerProfile` + student's 4-week work history

**Interview structure:**
- Round 1: DSA (company-calibrated difficulty)
- Round 2: System design (from their actual interview bank)
- Round 3: Behavioural (their actual values, culture fit signals)

**Output:**
- Hire / No-hire verdict
- Specific gaps with scores
- Recommended focus areas before applying

---

## Data Flow Diagram

```
[User Input]
     │
     ▼
[Agent 1: Scraper] ──→ CompanyDNA (JSON)
     │
     ▼
[Agent 2: Modeller] ──→ EngineerProfile (Prompt Persona)
     │
     ▼
[Agent 3: Task Gen] ──→ Weekly Tasks (Markdown + Constraints)
     │
     ▼
[Student Does Task]
     │
     ▼
[Agent 4: Mentor] ──→ Feedback Report (Severity-tagged)
     │         ▲
     └─────────┘  (loop for 4 weeks)
     │
     ▼
[Agent 5: Interviewer] ──→ Final Verdict + Gap Analysis
```

---

## Key Design Decisions

**Why sequential, not parallel?**
Each agent's output directly shapes the next agent's behaviour. Company DNA must be built before tasks can be generated.

**Why Claude API?**
Claude's instruction-following is strong enough to reliably maintain a "persona" (e.g. a strict Razorpay senior engineer) across a long code review without drifting.

**Why CrewAI + LangGraph?**
CrewAI handles role assignment cleanly. LangGraph handles the 4-week feedback loop state management.
