# HTOKEN Standard

**Human-Token Labor Accounting for AI-Augmented Organizations**

HTOKEN is an open standard for measuring, logging, verifying, and comparing human labor alongside AI compute in hybrid workflows.

## The Problem

AI systems produce precise cost data: compute time, token counts, per-task spend. Human labor produces none of these. Organizations deploying AI alongside humans cannot answer basic questions:

- What does this task actually cost when a human is involved?
- Was the human work actually completed?
- Should we automate this, or does it need a human?

## The Solution

HTOKEN treats human labor as a measurable, auditable execution unit — priced, timed, task-linked, and verified — placed on the **same ledger** as AI output.

```
savings = human_only_cost - (ai_cost + htoken_cost)
```

One ledger. Both sides. Economic symmetry.

## Specification

[HTOKEN-SPEC-v1.0.md](./HTOKEN-SPEC-v1.0.md) -- The full standard specification.

## Key Concepts

- **Economic Symmetry** -- Human and AI contributions measured with equal precision
- **Unified Ledger** -- Single data store for both AI and human work entries
- **Verification Protocol** -- Human work is PENDING until proven CONFIRMED
- **Routing Protocol** -- AI-first decision tree with human escalation paths
- **Comparative Cost Analysis** -- Every task shows AI-only, human-only, and blended costs

## Conformance Levels

| Level | Name | Scope |
|-------|------|-------|
| 1 | HTOKEN Basic | Ledger + CRUD + verification + export |
| 2 | HTOKEN Standard | + AI/human fields + routing + analytics + real-time events |
| 3 | HTOKEN Complete | + worker portal + escalation + multi-tenant + audit trail |

## License

The HTOKEN specification is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You can use, adapt, and build on it -- just credit **Iron Noodle Technologies LLC** as the original author.

Reference implementations are licensed under [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## Author

Created by **Roberto Stanley** at [Iron Noodle Technologies LLC](https://ironnoodle.com) in 2026.

Born from production deployment at a bankruptcy law firm, where distinguishing AI-generated work from attorney-verified work isn't optional -- it's the law.

## Contributing

This is a living standard. To propose changes:
1. Open an issue describing the problem or gap
2. Submit a pull request with your proposed spec change
3. Include rationale and, if possible, a real-world use case

## Contact

- **Website:** [ironnoodle.com](https://ironnoodle.com)
- **Email:** rs@ironnoodle.com
