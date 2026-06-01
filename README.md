# 🕵️ ShadowIntern

> **Train for ONE specific company's exact culture and problems — before you ever apply.**

[![Status](https://img.shields.io/badge/status-in%20development-yellow)](https://github.com)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Built With](https://img.shields.io/badge/built%20with-Claude%20API-blueviolet)](https://anthropic.com)

---

## 🧠 The Core Insight

Every top company has a unique engineering culture — how they write code, what problems they solve, how they review work, what they value in engineers.

> The candidate who walks in already **thinking like a Razorpay engineer** always beats the one who just grinded DSA.

**ShadowIntern makes you that person** — for any company, without knowing anyone inside.

---

## 🚀 How It Works

```
Student enters: "I want to work at Razorpay"
        │
        ▼
┌─────────────────────────────────────┐
│  Agent 1 — Company Intelligence     │
│  Scrapes GitHub repos, tech blogs,  │
│  job descriptions, Glassdoor,       │
│  LinkedIn posts, YouTube talks      │
│  → Returns: "Company DNA"           │
└──────────────┬──────────────────────┘
               │
        ▼
┌─────────────────────────────────────┐
│  Agent 2 — Culture Modeller         │
│  Understands stack, values,         │
│  what they reject, how they think   │
│  → Returns: "Engineer Profile"      │
└──────────────┬──────────────────────┘
               │
        ▼
┌─────────────────────────────────────┐
│  Agent 3 — Task Generator           │
│  Creates REAL intern-level tasks    │
│  based on actual company problems   │
│  → Returns: Daily task assignments  │
└──────────────┬──────────────────────┘
               │
        ▼
┌─────────────────────────────────────┐
│  Agent 4 — Shadow Mentor            │
│  Reviews code like a senior         │
│  engineer AT THAT COMPANY would     │
│  → Returns: Company-style feedback  │
└──────────────┬──────────────────────┘
               │
        ▼
┌─────────────────────────────────────┐
│  Agent 5 — Interview Simulator      │
│  Uses ACTUAL questions their        │
│  interviewers ask, gives verdict    │
│  → Returns: Hire / No-hire + gaps   │
└─────────────────────────────────────┘
```

---

## 📊 Dashboard Preview (Concept)

```
🏢 Shadow Company: Razorpay          📅 Week 3 of 4
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Tasks Completed:     11/14
⭐ Senior Review Score: 74/100
🎯 Interview Readiness: 68%

📋 This Week's Task:
   "Design a webhook retry system that handles
    partial failures gracefully.
    Razorpay processes 5M webhooks/day."

👨‍💼 Mentor Feedback:
   "Your solution works but a Razorpay engineer
    would flag this — you're not handling
    idempotency. That's a P0 bug in payments.
    Redo section 3."

📈 Weak Area:   System Design — Distributed Queues
🔥 Strong Area: API Design, Error Handling
```

---

## 🆚 Why This Is Different

| What Exists | What ShadowIntern Does |
|---|---|
| LeetCode | Generic DSA, no company context |
| Mock interview platforms | Scripted questions, not company-specific |
| Internships | Luck-based, requires connections |
| **ShadowIntern** | **Train for ONE company's exact culture & problems** |

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Agent Framework | CrewAI + LangGraph |
| LLM | Claude API (Anthropic) |
| Scraping | Playwright + GitHub API |
| Code Review Agent | Claude with company style prompts |
| Frontend | React Dashboard |
| Auth + Payments | Supabase + Razorpay *(ironic)* |

---

## 📈 Scale Roadmap

See [ROADMAP.md](ROADMAP.md) for full details.

- **Phase 1** → Top 20 Indian tech companies
- **Phase 2** → Any company globally with public data
- **Phase 3** → ₹500/month per company (student plan)
- **Phase 4** → Companies pay to access pre-trained candidates

---

## 🔬 Research

This project also has an active research component exploring multi-agent frameworks for company-specific engineering culture extraction and task synthesis.

See [`research/ABSTRACT.md`](research/ABSTRACT.md) for the working paper draft.

**Related work:**
- MockLLM (2024) — Multi-agent mock interview generation
- TheAgentCompany (2024) — Benchmarking LLM agents on real workplace tasks
- MetaGPT (2023) — Multi-agent software development simulation

---

## 🗺️ Architecture

See [ARCHITECTURE.md](ARCHITECTURE.md) for the full agent pipeline breakdown.

---

## 🤝 Contributing

This project is in early design phase. See [CONTRIBUTING.md](CONTRIBUTING.md) if you want to collaborate.

**Areas where help is needed:**
- Agent pipeline design
- Company data scraping strategy
- Frontend dashboard mockups
- Research/evaluation methodology

---

## 👤 Author

Built and researched by [@RabbaniHacker](https://github.com/RabbaniHacker)

---

## 📄 License

MIT © 2026 — See [LICENSE](LICENSE)
