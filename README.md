# Forward Deployed Engineer: A Practical Guide

> A Forward Deployed Engineer (FDE) works directly with a customer, department or operations team.
> They observe the real workflow, understand the constraints, build the solution, and stay until it is
> in real use.

This is a working guide for engineers who want to move into FDE roles. It is opinionated, written from
the engineering side, and updated as I learn. Status: **v0.1, living document.**

**Contents**

1. [What an FDE actually does](#1-what-an-fde-actually-does)
2. [FDE vs adjacent roles](#2-fde-vs-adjacent-roles)
3. [The skill map](#3-the-skill-map)
4. [A 12-week roadmap](#4-a-12-week-roadmap)
5. [Portfolio projects that prove it](#5-portfolio-projects-that-prove-it)
6. [Templates: discovery and scoping](#6-templates-discovery-and-scoping)
7. [Interview loops and how to prepare](#7-interview-loops-and-how-to-prepare)
8. [Anti-patterns](#8-anti-patterns)
9. [Reading list](#9-reading-list)

---

## 1. What an FDE actually does

The job is a loop, not a handoff:

```text
Observe  →  Scope  →  Build  →  Deploy  →  Measure  →  Iterate
   ▲                                                       │
   └───────────────────────────────────────────────────────┘
```

| Stage | What it means in practice |
|---|---|
| **Observe** | Sit with the people doing the work. Watch the real workflow, not the one in the slide deck. |
| **Scope** | Turn a vague pain ("our follow-ups are a mess") into a narrow, testable problem with a success metric. |
| **Build** | Ship the smallest useful version fast. Prototype in days, not quarters. |
| **Deploy** | Get it into the customer's actual environment: their auth, their data, their messy systems. |
| **Measure** | Define "working" with numbers: time saved, error rate, adoption, tickets avoided. |
| **Iterate** | Fix what real usage exposes. Feed patterns back to the core product team. |

The defining trait: **you own the outcome, not the ticket.** A feature that ships but is not used is a failure.

## 2. FDE vs adjacent roles

| Role | Primary output | Relationship to code | Relationship to customer |
|---|---|---|---|
| **Software Engineer** | Product features | Owns the codebase | Indirect, via product and support |
| **Solutions / Sales Engineer** | Demos, POCs, technical wins | Light, throwaway code | Pre-sale, then hands off |
| **Consultant** | Recommendations, decks | Rarely writes production code | Advisory, short engagement |
| **Product Engineer** | Product features with product judgment | Owns the codebase | Talks to users, mostly via PM |
| **Forward Deployed Engineer** | Working systems in production at the customer | Writes real code, often in customer's environment | Embedded, owns the result after launch |

Titles vary: *Forward Deployed Engineer, Deployment Strategist, Applied AI Engineer, Customer Engineer,
Technical Solutions Engineer.* Read the job description, not the title. Look for: customer-facing,
ships production code, owns outcomes.

Palantir popularized the role. Many AI and enterprise-software companies now hire for it, and the demand
has grown with LLM products that need integration into messy real-world workflows.

## 3. The skill map

Be strong in two columns and credible in the rest.

### Engineering (the floor)
- One full-stack path end to end (for example TypeScript + React/Next.js + Node/NestJS, or Python + FastAPI)
- SQL and relational modeling, indexes, migrations
- REST, webhooks, OAuth/JWT auth, idempotency, retries
- Docker, CI/CD, one cloud provider, logs and monitoring
- Reading and debugging code you did not write

### AI systems
- LLM APIs, prompt design, structured output
- Tool calling and agent loops
- RAG: chunking, embeddings, retrieval quality
- **Evaluation**: golden sets, regression checks, failure analysis
- Guardrails, human-in-the-loop, cost and latency control

### Integration
- Third-party APIs, rate limits, pagination, flaky vendors
- Messaging and document pipelines (WhatsApp, email, forms, PDFs)
- Workflow automation (n8n, Zapier, queues, cron)
- Data mapping between systems that disagree about what a "customer" is

### Customer-facing
- Discovery interviews: ask about past behavior, not opinions
- Scoping and saying no
- Writing: status updates, one-pagers, postmortems
- Live demos that survive things going wrong
- Managing expectations when the data is worse than promised

### Operations
- Runbooks, alerting, incident response
- Rollouts, feature flags, rollback plans
- Handover: leaving the customer able to run it without you

## 4. A 12-week roadmap

### Weeks 1–4: Build the engineering floor
- [ ] Ship one authenticated CRUD service with migrations, tests and CI. A reference implementation is in [fastapi-postgres-api](https://github.com/abhishekbhartiind/fastapi-postgres-api).
- [ ] Add a webhook receiver with signature verification, retries and idempotency keys
- [ ] Containerize and deploy it somewhere real, with logs you can read
- [ ] Write a runbook for it: how it fails, how to tell, how to fix

### Weeks 5–8: Build AI systems that survive contact with reality
- [ ] Build a tool-calling agent that completes a multi-step task via real APIs
- [ ] Build a RAG pipeline over messy documents (scanned PDFs, mixed formats)
- [ ] Create an evaluation set of at least 30 cases and track pass rate across prompt changes
- [ ] Add human-in-the-loop review for low-confidence outputs

### Weeks 9–12: Practice the customer loop
- [ ] Find a real user (a small business, a friend's team) and run 3 discovery interviews
- [ ] Write a one-page scope with a success metric, then build it in under 2 weeks
- [ ] Deploy it into their actual workflow and measure for 2 weeks
- [ ] Write a case study: problem, constraints, decisions, results, what you would change

## 5. Portfolio projects that prove it

Employers cannot see your private work. Build public artifacts that show the same thinking.

| Project | What it proves | "Done" means |
|---|---|---|
| **Document-collection agent** (chat channel → request, chase, validate, store) | Integration + AI + ops | Handles missing, wrong and late documents; has an audit log |
| **Workflow automation pack** (3–4 sanitized n8n flows with READMEs) | Pragmatic automation, failure handling | Each README covers the problem, flow diagram, failure modes |
| **Backend reference service** | Engineering floor | Auth, migrations, tests on the real database, CI green |
| **Case study** (README-only repo) | Customer thinking | Problem, architecture diagram, trade-offs, what you would redo |

Rule: **every project README answers "what problem, for whom, how do you know it worked?"**

## 6. Templates: discovery and scoping

### Discovery questions
Ask about the past, not the hypothetical.

1. Walk me through the last time this happened. What did you do first?
2. What did that cost you (time, money, mistakes)?
3. What have you already tried? Why did it not stick?
4. Who else touches this process? Where does it break between people?
5. If this were fixed, what would you stop doing?
6. How will you know in a month that it worked?

### One-page scope

```markdown
## Problem
One paragraph, in the customer's words.

## Users and workflow today
Who does what, with which tools, how often.

## Success metric
A number and a date. Example: "Cut document chasing from 6 hrs/week to 1."

## In scope / Out of scope
Bullets. Out of scope matters more.

## Integrations and data
Systems, access needed, who owns each.

## Risks and assumptions
What would invalidate this plan?

## Rollout and handover
Pilot group, rollback plan, who runs it after launch.
```

## 7. Interview loops and how to prepare

Typical stages (they vary by company):

| Stage | What they test | How to prepare |
|---|---|---|
| **Recruiter screen** | Motivation for customer-facing engineering | A crisp story of a time you owned an outcome beyond the code |
| **Coding** | Fundamentals, pragmatism | Practice API-style problems: parsing, integration, data munging, not just puzzles |
| **Ambiguous problem / decomposition** | Scoping and judgment | Given a vague customer problem, ask questions, define metrics, propose a phased plan |
| **System design** | Integration and reliability | Webhooks, queues, retries, idempotency, failure handling |
| **Customer scenario / role-play** | Communication under pressure | Practice: angry customer, bad data, impossible deadline |
| **Behavioral** | Ownership, conflict, ambiguity | 5 stories, each with a number and a lesson |

Practice prompts:
- "A logistics company loses hours every day reconciling delivery documents. Where do you start?"
- "Your LLM extraction is 85% accurate. The customer needs 99%. What now?"
- "The customer's API goes down mid-demo. Walk me through the next five minutes."

## 8. Anti-patterns

- **Building before observing.** The workflow in the brief is rarely the workflow in reality.
- **Custom-everything.** If you build the same thing for three customers, tell the product team.
- **No success metric.** You cannot defend the work without one.
- **Demo-ware.** Works on your laptop with perfect data. Production has neither.
- **Heroics without handover.** If only you can run it, you built a dependency, not a solution.
- **Overselling AI.** State accuracy honestly, and design for the failures.

## 9. Reading list

- *The Mom Test*, Rob Fitzpatrick: how to ask customer questions that return truth
- *Designing Data-Intensive Applications*, Martin Kleppmann: how systems actually fail
- *Release It!*, Michael Nygard: stability patterns for production software
- *The Pragmatic Programmer*, Hunt and Thomas: habits for shipping reliably

---

## About

Maintained by [Abhishek Bharti](https://abhishekbharti.com). 9 years building production web platforms,
now focused on AI systems and forward-deployed engineering.
[LinkedIn](https://www.linkedin.com/in/imabhishekbharti/) · [Portfolio](https://abhishekbharti.com)

Corrections and additions welcome: open an issue or a pull request.