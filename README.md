# HTOKEN Standard

**A Communication Standard for Human-AI Work Accounting**

HTOKEN is an open standard that gives AI systems and human leadership a shared vocabulary for measuring, logging, verifying, and comparing work -- regardless of who (or what) performed it.

> *"If AI has token counts, cost-per-task, and deterministic logs -- humans should too."*

---

## Why This Exists

### The Origin: Expensive Labor in a Captured Market

HTOKEN was born in the legal industry, where the cost asymmetry between AI and human labor is extreme. Big Law partners bill at $2,000/hour. A small bankruptcy firm pays associates $150-300/hour. Meanwhile, an AI can draft the same document for $2.50.

The question was never "Can AI do this work?" -- it was **"How do you prove what AI did, what the human did, what it cost, and that the licensed professional actually reviewed it?"**

In law, that proof isn't optional. Unauthorized Practice of Law (UPL) means if you can't demonstrate a licensed attorney performed the legal judgment, you're committing a crime. HTOKEN was built to solve this: a single ledger where AI work and human work sit side by side, with verification that the human actually did their part.

But the problem HTOKEN solves isn't unique to law.

### The Bigger Problem: No Common Language

Every AI system already produces granular cost data: compute milliseconds, token counts, per-task spend, deterministic logs. When an AI drafts a document, you know exactly what it cost -- down to the fraction of a cent.

But when a human reviews that document, signs it, files it, or calls the client about it? The cost is invisible. The time is self-reported. The completion is assumed. The comparison is impossible.

**HTOKEN is a communication standard.** It gives:
- **AI systems** a structured way to report their work (model, tokens, cost, compute time)
- **Human workers** a structured way to log their work (hours, rate, role, verification)
- **Leadership** a unified view of both (savings, blended cost, pending verifications)
- **Regulators** an audit trail proving who did what (verification protocol, routing justification)

Without a shared vocabulary, organizations are left guessing. HTOKEN standardizes the terms so that LLMs, dashboards, CFOs, and compliance teams are all reading from the same ledger.

### The Measurement Crisis

This is the **measurement crisis** of AI-augmented organizations:

| Dimension | AI Systems | Human Workers |
|-----------|-----------|---------------|
| Cost per task | Precise (tokens x rate) | Unknown or estimated |
| Execution time | Millisecond-accurate | Self-reported or absent |
| Audit trail | Deterministic logs | Fragmented or nonexistent |
| Verification | Output is proof | Assumed until challenged |
| Comparison | Easy (model A vs. B) | Impossible (no baseline) |

This asymmetry creates three failures:

1. **Invisible labor costs** -- You can't optimize what you can't measure
2. **Unverifiable execution** -- Human work is assumed complete without proof
3. **Irrational automation decisions** -- Without comparable metrics, organizations either over-automate (removing humans where they add value) or under-automate (keeping humans where AI is sufficient)

HTOKEN solves all three.

---

## What HTOKEN Does

HTOKEN treats human labor as a measurable, auditable execution unit -- priced, timed, task-linked, and verified -- placed on the **same ledger** as AI output.

```
savings = human_only_cost - (ai_cost + htoken_cost)
```

One ledger. Both sides. **Economic symmetry.**

### The Core Loop

```
1. Task arrives
2. Route: Can AI handle this alone, or does it need a human?
3. Execute: AI does its part, human does theirs
4. Log: Both costs hit the same ledger -- side by side
5. Verify: AI work auto-confirms. Human work stays PENDING until proven.
6. Compare: What did this cost vs. what it would have cost without AI?
```

### What You Get

- **True cost visibility** -- Every task shows AI cost, human cost, and blended cost
- **Verification accountability** -- Human work isn't "done" until there's proof
- **Honest savings math** -- Real numbers, not marketing estimates
- **Automation intelligence** -- Data-driven decisions about what to automate next
- **Compliance protection** -- Proves a licensed human did the regulated work (UPL, HIPAA, SOX)

---

## Real-World Examples

### Legal Services
A law firm uses AI to draft a bankruptcy petition. An attorney reviews it.

| Component | Cost |
|-----------|------|
| AI drafts document | $2.50 |
| Attorney reviews (0.5 hr x $300/hr) | $150.00 |
| **Blended cost** | **$152.50** |
| Human-only cost (attorney drafts from scratch, 2 hrs) | $600.00 |
| **Savings** | **$447.50 (74.6%)** |

The ledger proves the attorney reviewed the work. UPL protection built into the accounting.

### Financial Services
An advisory firm uses AI to research SEC filings. An analyst verifies findings.

| Component | Cost |
|-----------|------|
| AI researches 50 SEC filings | $8.00 |
| Analyst verifies key findings (4 hrs x $50/hr) | $200.00 |
| **Blended cost** | **$208.00** |
| Human-only cost (2 analysts, 3 days) | $4,800.00 |
| **Savings** | **$4,592.00 (95.7%)** |

### Software Engineering
AI writes the initial implementation. A developer reviews, tests, and deploys.

| Component | Cost |
|-----------|------|
| AI writes code | $5.00 |
| Developer reviews + deploys (0.5 hr x $150/hr) | $75.00 |
| **Blended cost** | **$80.00** |
| Human-only cost (4 hrs x $150/hr) | $600.00 |
| **Savings** | **$520.00 (86.7%)** |

### Healthcare Administration
AI suggests medical codes from clinical notes. A certified coder verifies.

| Component | Cost |
|-----------|------|
| AI suggests ICD-10 codes | $0.50 |
| Certified coder verifies (0.5 hr x $50/hr) | $25.00 |
| **Blended cost** | **$25.50** |
| Human-only cost (2 hrs x $50/hr) | $100.00 |
| **Savings** | **$74.50 (74.5%)** |

Regulatory compliance: a certified coder (required by law) verified all codes.

---

## Key Concepts

### Economic Symmetry
Human and AI contributions measured with equal precision. Neither is privileged; both are auditable. This does NOT mean humans and AI are interchangeable -- it means their contributions are **equally visible**.

### Unified Ledger
A single data store where every unit of work -- human or AI -- is recorded. No separate spreadsheets. No hidden costs. One ledger, one truth.

### Verification Protocol
AI work auto-confirms (deterministic execution = proof). Human work defaults to `PENDING` and requires external evidence to become `CONFIRMED`. This closes the accountability gap.

```
PENDING --> CONFIRMED    (proof provided)
    |-----> STALE        (7 days, no verification)
    |-----> DISPUTED     (verification challenged)
    |-----> WITHDRAWN    (task was not completed)
```

Escalation is built in:
- 24 hours: reminder to assigned worker
- 72 hours: escalate to supervisor
- 7 days: flag as STALE on dashboard
- 30 days: require manual resolution

### AI-First Routing Protocol
Every task hits a decision tree:

```
CAN AI DO THIS ALONE?
|
+-- YES --> AI executes, log cost, auto-confirm
|
+-- NO --> Why does it need a human?
    |
    +-- Licensed judgment (legal, medical, financial)
    +-- Physical action (mail, court, notarization)
    +-- Relationship action (client call, negotiation)
    +-- Creative judgment (brand approval, design review)
    +-- Compliance (audit sign-off, regulatory filing)
    +-- Blended (AI preps, human finishes)
    |
    Each --> assign minimum qualified human, log both costs, PENDING
```

**Minimum Qualified Human**: Assign the lowest-cost person qualified for the task. Don't route a $50/hr task to a $300/hr professional.

### Comparative Cost Analysis
Every ledger entry records three cost scenarios:

| Scenario | What It Measures |
|----------|-----------------|
| `ai_cost` | What the AI actually spent |
| `human_only_cost` | What a human would charge without AI |
| `blended_cost` | What it actually cost (AI + human) |

```
savings     = human_only_cost - blended_cost
savings_pct = (savings / human_only_cost) x 100
```

These numbers power proposals, board reports, and automation decisions. They must be honest -- no inflated baselines.

---

## Specification

**[HTOKEN-SPEC-v1.0.md](./HTOKEN-SPEC-v1.0.md)** -- The full 19-section standard specification.

Covers:
- Definitions and core principles
- Measurement dimensions (time, cost, task linkage, verification)
- Unified ledger schema (25+ fields)
- AI-first routing protocol with decision tree
- Verification protocol with escalation timelines
- Comparative cost analysis methodology
- Compliance and ethical constraints (7 prohibitions)
- API contract (CRUD + analytics + worker portal)
- Implementation requirements
- Security considerations and access control
- Four industry use cases

---

## Ledger Schema (Summary)

The full schema is in the spec. Here's the structure:

```
Ledger Entry
|
+-- Identity:     id, created_at, date, entry_type, task_description, workflow
|
+-- AI Side:      ai_model, ai_provider, ai_compute_ms, ai_token_count, ai_cost_usd
|
+-- Human Side:   htoken_worker_id, htoken_role, htoken_hours, htoken_hourly_rate, htoken_cost_usd
|
+-- Verification: verification_status, verified_at, verified_by, verification_proof
|
+-- Comparison:   ai_only_cost_usd, human_only_cost_usd, blended_cost_usd*, savings_usd*, savings_pct*
                  (* = computed)
```

Entry types: `AI_ONLY`, `HUMAN_ONLY`, `BLENDED`, `COMPARISON`

---

## API Contract (Summary)

Conforming implementations expose these endpoints:

### Ledger Operations
```
POST   /htoken/ledger           -- Create entry
GET    /htoken/ledger           -- List (filter by days, workflow, status, worker)
GET    /htoken/ledger/{id}      -- Get single entry
PUT    /htoken/ledger/{id}      -- Update entry
DELETE /htoken/ledger/{id}      -- Remove entry
PUT    /htoken/ledger/{id}/verify  -- Verify (PENDING --> CONFIRMED)
```

### Analytics
```
GET    /htoken/summary          -- Totals, savings, counts
GET    /htoken/comparison       -- Cost analysis by workflow
GET    /htoken/trends           -- Time-series for dashboards
```

### Worker Self-Service (Optional)
```
GET    /htoken/worker/profile   -- Worker's own profile
GET    /htoken/worker/tasks     -- Assigned tasks
PUT    /htoken/worker/tasks/{id} -- Self-report on progress
```

All write operations require authentication (API key minimum, OAuth 2.0 recommended).

---

## Conformance Levels

| Level | Name | What It Requires |
|-------|------|-----------------|
| 1 | **HTOKEN Basic** | Unified ledger, CRUD operations, verification tracking, CSV/JSON export |
| 2 | **HTOKEN Standard** | Level 1 + AI/human fields + comparison fields + routing protocol + analytics + real-time events |
| 3 | **HTOKEN Complete** | Level 2 + worker portal + verification escalation + multi-tenant + immutable audit trail + rate history |

---

## Compliance and Ethics

HTOKEN includes seven non-negotiable prohibitions:

1. **Never hide human labor cost** -- If a human touched it, log their time and rate
2. **Never assume human execution without proof** -- PENDING until CONFIRMED
3. **Never substitute AI judgment for licensed human judgment** -- Legal, medical, and financial decisions require humans
4. **Never collapse AI and human costs** -- Always separate tracks on the ledger
5. **Never represent AI as providing professional advice** -- UPL protection is non-negotiable
6. **Never inflate human_only_cost** -- Honest baselines only. The real numbers are impressive enough.
7. **Never skip logging due to small magnitude** -- A $0.01 entry proves the system works

Individual AI-vs-human performance comparisons SHOULD NOT be used punitively.

---

## Who Should Implement HTOKEN

- **Law firms** using AI for document drafting, research, or client intake
- **Financial services** firms using AI for analysis, compliance, or reporting
- **Healthcare organizations** using AI for coding, scheduling, or clinical support
- **Software companies** using AI for code generation, testing, or documentation
- **Consulting firms** tracking blended AI/human project costs
- **Any organization** that needs to answer: "What does this actually cost when humans are involved?"

---

## FAQ

**Q: Is HTOKEN just time tracking?**
No. Time tracking records hours. HTOKEN records hours AND compares them to AI cost, AND verifies completion, AND calculates savings. Traditional time tracking has no concept of an AI counterpart.

**Q: Does HTOKEN replace my time tracking software?**
It can, or it can sit alongside it. HTOKEN adds the AI cost comparison and verification layers that time tracking tools don't have.

**Q: What if I don't use AI yet?**
HTOKEN still works as a human-only labor accounting system. When you add AI, the comparison data starts flowing automatically.

**Q: How do I estimate human_only_cost?**
Use published rates, industry benchmarks, or your own internal rate table. Be conservative -- when uncertain, use the lower estimate. The spec requires honest baselines.

**Q: What about privacy? Do I have to expose worker names?**
No. Worker identities can be anonymized in external reports (e.g., "Senior Attorney -- $300/hr" instead of a name). The spec requires GDPR/CCPA compliance.

**Q: Can I use HTOKEN commercially?**
Yes. CC BY 4.0 allows commercial use. Just credit Iron Noodle Technologies LLC as the original author.

---

## License

The HTOKEN specification is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** -- copy and redistribute in any medium or format
- **Adapt** -- remix, transform, and build upon for any purpose, including commercially

Under the following terms:
- **Attribution** -- Credit **Iron Noodle Technologies LLC** as the original author

Reference implementations are licensed under [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

---

## Origin

Created by **Roberto Stanley** at [Iron Noodle Technologies LLC](https://ironnoodle.com) in 2026.

### Built for Law, Designed for Everything

HTOKEN started as the internal accounting layer for a bankruptcy law firm's AI operating system. The firm needed to:

1. **Prove compliance** -- Show that licensed attorneys reviewed AI-generated work (UPL protection)
2. **Measure real savings** -- Demonstrate to the managing partner that AI reduced operating costs by 74-95% on specific workflows
3. **Verify human execution** -- Court filings, client calls, and notarizations can't be faked. The ledger had to prove they happened.
4. **Route intelligently** -- Decide which tasks go to AI, which require humans, and which need both

The result was a system where a $2.50 AI draft and a $150 attorney review appeared on the same ledger, with verification that the attorney actually reviewed it, and a comparison showing what it would have cost without AI.

That system worked. Then it became clear the vocabulary wasn't law-specific at all.

### The Universal Problem

Every industry deploying AI alongside humans faces the same questions:
- What did this actually cost?
- Who did what?
- Was the human work verified?
- Are we saving money or just adding complexity?

Healthcare needs to prove certified coders reviewed AI-suggested diagnoses. Financial services needs to show analysts verified AI research. Engineering teams need to track whether AI-generated code was reviewed before deployment. The vocabulary is the same everywhere.

**HTOKEN is that vocabulary.** It standardizes the terms -- `PENDING`, `CONFIRMED`, `BLENDED`, `AI_ONLY`, `routing_reason`, `verification_proof` -- so that any organization, in any industry, can account for human-AI collaboration with the same precision.

### Why Open Source

Standards that live behind paywalls don't become standards. They become products. We open-sourced HTOKEN under CC BY 4.0 because the value isn't in the spec -- it's in being the organization that wrote it, deploys it in production, and certifies others against it. Every implementation of HTOKEN carries Iron Noodle's name in the attribution. That's better than a patent.

---

## Contributing

This is a living standard. To propose changes:

1. Open an issue describing the problem or gap
2. Submit a pull request with your proposed spec change
3. Include rationale and, if possible, a real-world use case

All contributions must maintain backward compatibility with the current spec version.

---

## Contact

- **Website:** [ironnoodle.com](https://ironnoodle.com)
- **Email:** rs@ironnoodle.com
- **Standard Author:** Iron Noodle Technologies LLC, Phoenix, AZ
