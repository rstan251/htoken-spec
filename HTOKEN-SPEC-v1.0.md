# HTOKEN Standard Specification v1.0

**Human-Token Labor Accounting for AI-Augmented Organizations**

---

**Specification Version:** 1.0.0
**Status:** Draft
**Date:** 2026-03-14
**Author:** Roberto Stanley, Iron Noodle Technologies LLC
**License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — Attribution required

---

> **"If AI has token counts, cost-per-task, and deterministic logs — humans should too."**

---

## Table of Contents

1. [Abstract](#1-abstract)
2. [Problem Statement](#2-problem-statement)
3. [Core Principle: Economic Symmetry](#3-core-principle-economic-symmetry)
4. [Definitions](#4-definitions)
5. [HTOKEN Measurement Dimensions](#5-htoken-measurement-dimensions)
6. [The Unified Ledger](#6-the-unified-ledger)
7. [Routing Protocol](#7-routing-protocol)
8. [Verification Protocol](#8-verification-protocol)
9. [Comparative Cost Analysis](#9-comparative-cost-analysis)
10. [Compliance & Ethical Constraints](#10-compliance--ethical-constraints)
11. [Ledger Schema](#11-ledger-schema)
12. [API Contract](#12-api-contract)
13. [Implementation Requirements](#13-implementation-requirements)
14. [Conformance Levels](#14-conformance-levels)
15. [Security Considerations](#15-security-considerations)
16. [Use Cases](#16-use-cases)
17. [Glossary](#17-glossary)
18. [License](#18-license)
19. [Acknowledgments](#19-acknowledgments)

---

## 1. Abstract

HTOKEN (Human-Token) is an open communication standard that provides a shared vocabulary for measuring, logging, verifying, and comparing human labor alongside AI compute within hybrid human-AI workflows.

HTOKEN was originally developed for the legal industry, where the cost asymmetry between AI and human labor is extreme and the compliance requirements are absolute — distinguishing AI-generated work from attorney-verified work is not optional, it is a legal requirement. The standard was designed to be industry-agnostic from inception, providing the same structured vocabulary for any domain where AI augments expensive human labor.

In modern AI-augmented organizations, AI systems already produce granular cost data: compute time, token counts, per-task spend, and deterministic execution logs. Human labor, historically, produces none of these. HTOKEN closes this gap by treating human labor as a measurable, auditable execution unit — priced, timed, task-linked, and verified — placed on the same ledger as AI output.

HTOKEN serves as a **communication standard** between three audiences:
- **AI systems** — structured output format for reporting work performed (model, tokens, cost, compute time)
- **Human leadership** — unified dashboard language for cost visibility, savings analysis, and verification status
- **Regulatory and compliance bodies** — audit trail proving who performed what work and whether licensed professionals completed required steps

This creates **economic symmetry**: a single source of truth where every unit of work — whether performed by a human or an AI — is tracked with equal rigor.

---

## 2. Problem Statement

Organizations deploying AI alongside human workers face a measurement crisis:

| Dimension | AI Systems | Human Workers |
|-----------|-----------|---------------|
| Cost per task | Precise (tokens x rate) | Unknown or estimated |
| Execution time | Millisecond-accurate | Self-reported or absent |
| Audit trail | Deterministic logs | Fragmented or nonexistent |
| Verification | Output is proof | Assumed until challenged |
| Comparison | Easy (model A vs. model B) | Impossible (no baseline) |

This asymmetry creates three critical failures:

1. **Invisible labor costs** — Organizations cannot determine the true cost of human involvement in AI-assisted workflows
2. **Unverifiable execution** — Human work is assumed complete without proof, creating accountability gaps
3. **Irrational automation decisions** — Without comparable metrics, organizations either over-automate (removing humans where they add value) or under-automate (keeping humans where AI is sufficient)

HTOKEN solves all three by establishing a unified accounting standard.

---

## 3. Core Principle: Economic Symmetry

HTOKEN is built on one principle:

> **Every unit of work — human or AI — MUST be measured with equal precision, logged on the same ledger, and subject to the same verification standards.**

This means:
- Human labor gets timestamps, cost rates, and task linkage — just like AI compute
- AI output and human output appear side-by-side in the same ledger
- Neither is privileged; both are auditable
- Comparison between the two is always possible

Economic symmetry does NOT mean humans and AI are interchangeable. It means their contributions are **equally visible**.

---

## 4. Definitions

### 4.1 HTOKEN (Human-Token)

A discrete unit of human labor contribution to an operational workflow. An HTOKEN is defined by four dimensions: time, cost, task linkage, and verification status.

### 4.2 AI Token

A discrete unit of AI compute contribution, measured in model-specific tokens (input + output), with associated compute time and cost.

### 4.3 Unified Ledger

A single data store where both HTOKEN entries and AI token entries are recorded, enabling side-by-side comparison.

### 4.4 Blended Cost

The total cost of a task that involved both human and AI labor:
```
blended_cost = ai_cost_usd + htoken_cost_usd
```

### 4.5 Human-Only Cost

The estimated cost if the same task were performed entirely by a human, without AI assistance. This is the baseline for calculating savings.

### 4.6 Verification

The process of confirming that human work was actually performed. Unlike AI execution (which is deterministic and self-proving), human execution requires external proof.

### 4.7 Routing Decision

The determination of whether a task should be executed by AI alone, by a human alone, or by a blend of both. HTOKEN defines a standard routing protocol (Section 7).

---

## 5. HTOKEN Measurement Dimensions

Every human labor contribution MUST be measured across four dimensions:

### 5.1 Time
- **Start timestamp** — When the human began work (ISO 8601)
- **End timestamp** — When the human completed work (ISO 8601)
- **Duration** — Total hours (decimal), e.g., `1.5` for 90 minutes
- **Precision:** Minimum 15-minute increments; RECOMMENDED 6-minute increments (0.1 hr) for professional services

### 5.2 Cost
- **Hourly rate** — The human's rate in the organization's base currency (USD recommended)
- **Total cost** — `duration_hours x hourly_rate`
- **Rate source** — Where the rate comes from: `contract`, `market`, `internal`, `custom`
- Rates MUST be stored in a canonical rate table, not hard-coded per entry

### 5.3 Task Linkage
- Every HTOKEN entry MUST be linked to a specific task, case, ticket, or workflow
- Cross-reference IDs SHOULD map to the organization's task management system
- Orphan entries (no task linkage) are permitted but SHOULD be flagged

### 5.4 Verification
- Human work is **not confirmed until verified**
- Default status: `PENDING`
- Verification requires: proof type, verifier identity, verification timestamp
- See Section 8 for the full verification protocol

---

## 6. The Unified Ledger

The core data structure of HTOKEN is the **Unified Ledger** — a single table (or equivalent data store) where every unit of work is recorded.

### 6.1 Ledger Entry Types

| Type | Description | Verification |
|------|-------------|-------------|
| `AI_ONLY` | Task performed entirely by AI | Auto-confirmed on completion |
| `HUMAN_ONLY` | Task performed entirely by a human | Requires verification |
| `BLENDED` | Task performed by AI + human collaboration | Human portion requires verification |
| `COMPARISON` | Entry that records all three cost scenarios for analysis | N/A (analysis record) |

### 6.2 Ledger Invariants

1. **No hidden labor** — If a human touched a task, their time and cost MUST appear in the ledger
2. **No collapsed costs** — AI cost and human cost MUST be separate fields, never summed into a single opaque number
3. **No assumed execution** — Human entries default to `PENDING` until verified
4. **No inflated baselines** — `human_only_cost` estimates MUST be honest and defensible
5. **No minimum threshold** — A $0.01 entry is valid. All work counts.

---

## 7. Routing Protocol

HTOKEN defines a standard decision tree for determining whether a task requires human involvement.

### 7.1 AI-First Routing

```
1. CAN AI PERFORM THIS TASK FULLY?
   |
   +-- YES --> AI executes
   |           Log: ai_cost, human_only_cost (as baseline)
   |           Status: CONFIRMED (AI is self-verifying)
   |
   +-- NO or PARTIALLY --> WHY does it require a human?
       |
       +-- Licensed judgment
       |   (legal advice, medical decision, financial advice, regulatory sign-off)
       |   --> HTOKEN-REQUIRED --> Assign minimum qualified human
       |   --> Status: PENDING until verified
       |
       +-- Physical action
       |   (mail, court appearance, notarization, in-person delivery)
       |   --> HTOKEN-REQUIRED --> Assign operations/admin
       |   --> Status: PENDING until proof of completion
       |
       +-- Relationship action
       |   (client call, negotiation, sales close, conflict resolution)
       |   --> HTOKEN-REQUIRED --> Assign relationship owner
       |   --> Status: PENDING until CRM/call log confirmation
       |
       +-- Creative judgment
       |   (brand approval, design review, editorial decision)
       |   --> HTOKEN-REQUIRED --> Assign creative lead
       |   --> Status: PENDING until written approval
       |
       +-- Compliance/regulatory
       |   (audit sign-off, regulatory filing, ethics review)
       |   --> HTOKEN-REQUIRED --> Assign compliance officer
       |   --> Status: PENDING until filing confirmation
       |
       +-- AI does prep, human does final step
           --> BLENDED --> Log BOTH ai_cost AND htoken_cost
           --> Status: PENDING until human step verified
```

### 7.2 Minimum Qualified Human

When routing to a human, assign the **minimum qualified** person for the task. This means:
- Don't assign a $300/hr attorney to file a document a $50/hr clerk can file
- Don't assign a senior developer to a task a junior can handle
- The rate table determines cost; the qualification determines assignment

### 7.3 Routing Justification

Every routing decision SHOULD include a `routing_reason` field:
- `licensed_judgment` — Requires professional license
- `physical_action` — Requires physical presence
- `relationship` — Requires human relationship skills
- `creative` — Requires subjective judgment
- `compliance` — Requires regulatory authority
- `blended` — AI assists, human completes

---

## 8. Verification Protocol

### 8.1 Verification States

```
PENDING --> CONFIRMED
    |
    +--> STALE (after configurable threshold, default 7 days)
    |
    +--> DISPUTED (verification challenged)
    |
    +--> WITHDRAWN (task was not actually completed)
```

### 8.2 Verification Requirements by Work Type

| Work Type | Required Proof | Acceptable Evidence |
|-----------|---------------|-------------------|
| Court filing | Filing receipt | Case number, timestamp, docket entry |
| Document execution | Signed copy | Notary stamp, witness signature, e-signature log |
| Client communication | Activity log | Call recording, CRM note with duration, email thread |
| Payment collection | Transaction receipt | Payment confirmation, processor receipt |
| Physical delivery | Tracking proof | Tracking number, delivery confirmation, photo |
| Campaign launch | Platform confirmation | Screenshot, campaign ID, platform dashboard |
| Design approval | Written approval | Email, chat message, signed-off mockup |
| Code deployment | System confirmation | Deployment log, URL verification, CI/CD output |
| Data entry | System confirmation | Screenshot, API response, database diff |

### 8.3 Verification Escalation

Implementations SHOULD support configurable escalation timelines:

| Threshold | Action |
|-----------|--------|
| 24 hours without verification | Send reminder to assigned human |
| 72 hours without verification | Escalate to supervisor |
| 7 days without verification | Mark as `STALE`, flag on dashboard |
| 30 days without verification | Require manual resolution |

### 8.4 AI Work Verification

AI-only tasks are **self-verifying**: if the AI completed the task and produced output, the entry is `CONFIRMED` automatically. This is because AI execution is deterministic and logged.

Exception: If an AI task produces output that requires human review before being acted upon (e.g., a drafted legal document), the task is `BLENDED`, and the human review step requires verification.

---

## 9. Comparative Cost Analysis

### 9.1 The Three Costs

Every ledger entry SHOULD include three cost dimensions:

| Cost | Definition | Source |
|------|-----------|--------|
| `ai_cost` | Actual AI compute cost (tokens x rate + any API fees) | AI provider billing |
| `human_only_cost` | Estimated cost if a human performed the entire task without AI | Rate table x estimated hours |
| `blended_cost` | Actual total cost (AI cost + any human involvement) | `ai_cost + htoken_cost` |

### 9.2 Savings Calculation

```
savings = human_only_cost - blended_cost
savings_pct = (savings / human_only_cost) x 100
```

### 9.3 Estimation Guidelines for human_only_cost

The `human_only_cost` field is an estimate. It MUST be:
- **Honest** — Do not inflate to make AI look better. Real numbers are sufficient.
- **Defensible** — Based on published rates, industry benchmarks, or documented internal rates
- **Conservative** — When uncertain, use the lower estimate
- **Documented** — Include the basis for the estimate (role, hours, rate source)

### 9.4 Aggregate Reporting

Implementations SHOULD support aggregate analysis:
- Total savings by time period (daily, weekly, monthly, quarterly)
- Savings by workflow category
- Savings by department
- Verification rate (confirmed vs. pending)
- Average task cost (AI vs. human vs. blended)

---

## 10. Compliance & Ethical Constraints

### 10.1 Prohibitions (NON-NEGOTIABLE)

1. **Never hide human labor cost** — If a human contributed, their time and rate MUST be logged
2. **Never assume human execution without proof** — `PENDING` until `CONFIRMED`
3. **Never substitute AI judgment for licensed human judgment** — Legal advice, medical decisions, financial advice, and regulatory sign-offs REQUIRE human execution
4. **Never collapse AI and human costs** — Always maintain separate tracks on the ledger
5. **Never represent AI as providing professional advice** — Unauthorized Practice of Law (UPL), unlicensed medical advice, and similar violations are non-negotiable
6. **Never inflate human_only_cost** — Honest baselines only
7. **Never skip logging due to small magnitude** — All work counts. A $0.01 entry proves the system works.

### 10.2 Regulatory Considerations

HTOKEN implementations in regulated industries MUST:
- Maintain audit trails for the minimum period required by applicable regulations
- Support data export in standard formats (CSV, JSON) for regulatory review
- Clearly distinguish between AI-generated and human-generated work products
- Comply with labor law requirements regarding employee time tracking
- Not be used to set unreasonable productivity expectations based on AI baselines

### 10.3 Privacy

- HTOKEN rate tables MAY be anonymized in external reports (e.g., "Senior Attorney — $300/hr" instead of naming the individual)
- Individual performance comparisons against AI baselines SHOULD NOT be used for punitive purposes
- Implementations MUST comply with applicable data protection regulations (GDPR, CCPA, etc.)

---

## 11. Ledger Schema

### 11.1 Required Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | STRING | YES | Unique entry identifier (UUID recommended) |
| `created_at` | TIMESTAMP | YES | Entry creation time (ISO 8601) |
| `date` | DATE | YES | Work date (YYYY-MM-DD) |
| `entry_type` | ENUM | YES | `AI_ONLY`, `HUMAN_ONLY`, `BLENDED`, `COMPARISON` |
| `task_description` | STRING | YES | What was done (specific, auditable) |
| `task_reference` | STRING | NO | External task/ticket/case ID |
| `workflow` | STRING | NO | Category (see 11.3) |

### 11.2 AI Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `ai_model` | STRING | NO | Model identifier (e.g., `claude-opus-4-6`, `gpt-4o`) |
| `ai_provider` | STRING | NO | Provider name (e.g., `anthropic`, `openai`) |
| `ai_compute_ms` | INTEGER | NO | Execution time in milliseconds |
| `ai_token_count` | INTEGER | NO | Total tokens (input + output) |
| `ai_input_tokens` | INTEGER | NO | Input tokens |
| `ai_output_tokens` | INTEGER | NO | Output tokens |
| `ai_cost_usd` | DECIMAL | NO | Actual AI cost in USD |

### 11.3 Human Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `htoken_worker_id` | STRING | NO | Internal identifier for the human worker |
| `htoken_name` | STRING | NO | Human worker name (can be anonymized) |
| `htoken_role` | STRING | NO | Role/title of the human worker |
| `htoken_hours` | DECIMAL | NO | Hours worked (minimum precision: 0.1) |
| `htoken_hourly_rate` | DECIMAL | NO | Hourly rate in USD |
| `htoken_cost_usd` | DECIMAL | NO | `htoken_hours x htoken_hourly_rate` |
| `routing_reason` | STRING | NO | Why human involvement was required (see 7.3) |

### 11.4 Verification Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `verification_status` | ENUM | YES | `PENDING`, `CONFIRMED`, `STALE`, `DISPUTED`, `WITHDRAWN` |
| `verified_at` | TIMESTAMP | NO | When verification occurred |
| `verified_by` | STRING | NO | Who verified |
| `verification_proof` | STRING | NO | Description of evidence |

### 11.5 Comparison Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `ai_only_cost_usd` | DECIMAL | NO | Cost if AI performed the entire task |
| `human_only_cost_usd` | DECIMAL | NO | Cost if a human performed the entire task |
| `blended_cost_usd` | DECIMAL | COMPUTED | `ai_cost_usd + htoken_cost_usd` |
| `savings_usd` | DECIMAL | COMPUTED | `human_only_cost_usd - blended_cost_usd` |
| `savings_pct` | DECIMAL | COMPUTED | `(savings_usd / human_only_cost_usd) x 100` |

### 11.6 Workflow Categories

Implementations SHOULD support at least the following categories:

`engineering`, `legal`, `sales`, `marketing`, `finance`, `operations`, `research`, `communications`, `infrastructure`, `compliance`, `hr`, `support`, `general`

Custom categories are permitted.

---

## 12. API Contract

Conforming implementations MUST expose the following API endpoints (REST, GraphQL, or equivalent):

### 12.1 Ledger Operations

| Operation | Method | Path | Description |
|-----------|--------|------|-------------|
| Create entry | POST | `/htoken/ledger` | Create a new ledger entry |
| List entries | GET | `/htoken/ledger` | Query entries with filters |
| Get entry | GET | `/htoken/ledger/{id}` | Retrieve a single entry |
| Update entry | PUT | `/htoken/ledger/{id}` | Update entry fields |
| Delete entry | DELETE | `/htoken/ledger/{id}` | Remove an entry |
| Verify entry | PUT | `/htoken/ledger/{id}/verify` | Move entry to CONFIRMED |

### 12.2 Query Parameters (List)

| Parameter | Type | Description |
|-----------|------|-------------|
| `days` | INTEGER | Return entries from the last N days |
| `workflow` | STRING | Filter by workflow category |
| `status` | STRING | Filter by verification status |
| `entry_type` | STRING | Filter by entry type |
| `worker_id` | STRING | Filter by human worker |
| `limit` | INTEGER | Maximum results (default: 50) |
| `offset` | INTEGER | Pagination offset |

### 12.3 Analytics Endpoints

| Operation | Method | Path | Description |
|-----------|--------|------|-------------|
| Summary | GET | `/htoken/summary` | Aggregate totals, savings, counts |
| Comparison | GET | `/htoken/comparison` | Side-by-side cost analysis by workflow |
| Trends | GET | `/htoken/trends` | Time-series data for dashboards |

### 12.4 Worker Endpoints (Optional)

| Operation | Method | Path | Description |
|-----------|--------|------|-------------|
| Worker profile | GET | `/htoken/worker/profile` | Worker's own profile and rates |
| Worker tasks | GET | `/htoken/worker/tasks` | Tasks assigned to the authenticated worker |
| Update task | PUT | `/htoken/worker/tasks/{id}` | Worker self-reports on task progress |

### 12.5 Authentication

All write operations MUST require authentication. Implementations SHOULD support:
- API key authentication (minimum)
- OAuth 2.0 (recommended for multi-tenant)
- Worker tokens for limited self-service (see 12.4)

---

## 13. Implementation Requirements

### 13.1 Data Storage

- Ledger entries MUST be stored in a durable data store (relational database recommended)
- Computed fields (`blended_cost_usd`, `savings_usd`, `savings_pct`) MUST be recalculated whenever their source fields change
- All timestamps MUST be stored in UTC with timezone offset

### 13.2 Rate Table

- Implementations MUST maintain a canonical rate table for human workers
- Rates MUST be queried at runtime, not hard-coded per entry
- Rate changes MUST NOT retroactively modify existing ledger entries
- Rate history SHOULD be preserved for audit purposes

### 13.3 Real-Time Updates

- Implementations SHOULD support real-time event broadcasting (SSE, WebSocket, or equivalent)
- Events: `ledger_created`, `ledger_updated`, `ledger_deleted`, `ledger_verified`

### 13.4 Export

- Implementations MUST support CSV and JSON export of ledger data
- Export MUST include all fields, including computed fields
- Export SHOULD support date range filtering

---

## 14. Conformance Levels

### Level 1: HTOKEN Basic

Minimum viable implementation:
- Unified ledger with all required fields (Section 11.1, 11.4)
- Create, read, update, delete operations
- Verification status tracking
- CSV/JSON export

### Level 2: HTOKEN Standard

Full standard compliance:
- All Level 1 requirements
- AI fields (Section 11.2) and human fields (Section 11.3)
- Comparison fields (Section 11.5)
- Routing protocol implementation (Section 7)
- Analytics endpoints (Section 12.3)
- Real-time event broadcasting

### Level 3: HTOKEN Complete

Enterprise-grade implementation:
- All Level 2 requirements
- Worker self-service portal (Section 12.4)
- Verification escalation automation (Section 8.3)
- Multi-tenant support with organization isolation
- Audit trail with immutable append-only log
- Rate history preservation
- Regulatory export templates

---

## 15. Security Considerations

### 15.1 Data Classification

| Data Type | Sensitivity | Handling |
|-----------|------------|---------|
| Worker rates | CONFIDENTIAL | Encrypt at rest, restrict to admin/finance |
| Worker identities | PII | Comply with GDPR/CCPA, support anonymization |
| Task descriptions | INTERNAL | May contain case/client details — access control required |
| Cost aggregates | INTERNAL | Safe for management reporting |
| Savings metrics | PUBLIC-SAFE | Safe for proposals/marketing (anonymized) |

### 15.2 Access Control

- Admin: Full CRUD on all entries, rate management, export
- Manager: Read all entries in their department, verify their team's work
- Worker: Read/update own tasks only (via worker token)
- API consumer: Configurable per integration

### 15.3 Audit Trail

- All ledger modifications MUST be logged (who, when, what changed)
- Deletion SHOULD be soft-delete (mark inactive) rather than hard-delete
- Verification events MUST be immutable once confirmed

---

## 16. Use Cases

### 16.1 Legal Services

A law firm uses HTOKEN to track AI-assisted document drafting alongside attorney review time. The ledger proves:
- AI drafted the document (ai_cost: $2.50)
- An attorney reviewed and approved (htoken_cost: $150 at $300/hr x 0.5 hr)
- Without AI, the attorney would have drafted from scratch (human_only_cost: $600 at $300/hr x 2 hr)
- Savings: $447.50 (74.6%)
- Compliance: The attorney (licensed professional) reviewed all work — UPL protection

### 16.2 Financial Services

An advisory firm uses HTOKEN to track AI research alongside analyst verification:
- AI researched and summarized 50 SEC filings (ai_cost: $8.00)
- Analyst verified key findings and wrote conclusions (htoken_cost: $200)
- Without AI, two analysts would spend 3 days (human_only_cost: $4,800)
- Savings: $4,592 (95.7%)

### 16.3 Software Development

An engineering team uses HTOKEN to measure AI-assisted coding:
- AI wrote initial implementation (ai_cost: $5.00)
- Developer reviewed, tested, and deployed (htoken_cost: $75 at $150/hr x 0.5 hr)
- Without AI, developer would have built from scratch (human_only_cost: $600 at $150/hr x 4 hr)
- Savings: $520 (86.7%)

### 16.4 Healthcare Administration

A hospital uses HTOKEN to track AI-assisted medical coding:
- AI suggested ICD-10 codes from clinical notes (ai_cost: $0.50)
- Certified coder verified codes (htoken_cost: $25 at $50/hr x 0.5 hr)
- Without AI, coder would manually review notes and assign codes (human_only_cost: $100 at $50/hr x 2 hr)
- Savings: $74.50 (74.5%)
- Compliance: Certified coder (required by regulation) verified all codes

---

## 17. Glossary

| Term | Definition |
|------|-----------|
| **AI Token** | A unit of AI model input/output, as defined by the model provider |
| **Blended Cost** | Total cost combining AI compute and human labor for a task |
| **Economic Symmetry** | The principle that human and AI contributions are measured with equal precision |
| **HTOKEN** | Human-Token — a discrete, measurable unit of human labor contribution |
| **Human-Only Cost** | The estimated cost if a task were performed entirely by humans |
| **Minimum Qualified Human** | The least-senior (lowest-cost) person qualified to perform a task |
| **Routing Decision** | The determination of whether AI, human, or both should execute a task |
| **Savings** | The difference between human-only cost and blended cost |
| **Unified Ledger** | A single data store recording both AI and human work entries |
| **Verification** | The process of confirming human work was actually completed |
| **UPL** | Unauthorized Practice of Law — performing legal work without a license |

---

## 18. License

This specification is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose, including commercially

Under the following terms:
- **Attribution** — You must give appropriate credit to **Iron Noodle Technologies LLC** as the original author, provide a link to this specification, and indicate if changes were made.

Reference implementations of this specification are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

---

## 19. Acknowledgments

HTOKEN was created by **Roberto Stanley** at **Iron Noodle Technologies LLC** in 2026.

### Origin

HTOKEN was born from the operational need to account for human labor with the same precision that AI systems account for compute. It was first deployed in production at a bankruptcy law firm, where the distinction between AI-generated work and attorney-verified work is not a nice-to-have — it's a legal requirement (Unauthorized Practice of Law, 18 U.S.C. § 1346 and state equivalents).

In that environment, the cost asymmetry is stark: Big Law partners bill at $2,000+/hour while AI can produce comparable research and drafting for $2-10 per task. Small firms that deploy AI effectively can compete — but only if they can **prove** that licensed professionals performed the regulated work, and **measure** the actual savings with auditable precision.

HTOKEN provided that proof and that measurement. The firm's ledger showed 74-95% cost reduction on specific workflows, with every attorney review verified and every AI contribution logged.

### Why a Standard

The vocabulary HTOKEN introduced — `PENDING`, `CONFIRMED`, `BLENDED`, `AI_ONLY`, `routing_reason`, `verification_proof`, `human_only_cost`, `savings_pct` — turned out to be universal. Healthcare organizations face the same compliance verification requirements (certified coders, licensed practitioners). Financial services needs the same audit trails. Software engineering teams need the same blended cost analysis.

HTOKEN is a **communication standard** — a shared language so that AI systems, human workers, leadership dashboards, and compliance auditors are all reading from the same ledger. Like HTTP standardized how computers communicate, HTOKEN standardizes how organizations account for human-AI collaboration.

### Design Philosophy

Every element of this specification — the routing protocol, the verification escalation, the comparative cost analysis, the conformance levels — exists because a production system needed it. This standard was developed through real-world deployment, not theoretical design.

For questions, contributions, or conformance certification, contact:

- **Standard Author:** Iron Noodle Technologies LLC
- **Website:** ironnoodle.com
- **Repository:** github.com/rstan251/htoken-spec

---

*HTOKEN Standard Specification v1.0 -- 2026 Iron Noodle Technologies LLC. Licensed under CC BY 4.0.*
