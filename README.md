# WSF Governance

> **Where WSF is governed — architectural decision records, change requests, lifecycle, authority, and the investigation record.**

This repository (`wsf-governance/`) contains the governance artifacts of the World Semantic Foundation. The architectural baseline, lifecycle models, status semantics, change control, and the full investigation record are maintained here.

---

## Repository Structure

```
wsf-governance/
├── README.md                          (this file)
├── ADR/                               Architectural Decision Records
│   ├── README.md                      ADR index
│   └── ADR-WSF-NN-<decision>.md       Individual ADRs
├── CR/                                Change Requests
│   ├── README.md                      CR index
│   └── CR-WSF-NN-<change>.md          Individual CRs
├── GOVERNANCE/
│   ├── CHANGE-CONTROL-LIFECYCLE.md    The 8-stage lifecycle
│   └── SEMANTIC-STATUS-MODEL.md       The 6-stage semantic status
├── RESEARCH/
│   └── INVESTIGATION-RECORD.md        The 10 investigations behind the ADRs
└── templates/
    ├── ADR-TEMPLATE.md                Template for new ADRs
    └── CR-TEMPLATE.md                 Template for new CRs
```

---

## What This Repository Provides

The governance layer provides:

| Artifact | Purpose |
|---|---|
| **Architectural Decision Records (ADRs)** | Authoritative architectural statements. Each captures context, decision, consequences, and rejected alternatives. |
| **Change Requests (CRs)** | Implementation change requests. Each implements one or more ADRs with explicit scope. |
| **Change Control Lifecycle** | The 8-stage process every semantic change goes through: Investigation → Finding → Synthesis → ADR → CR → Implementation → Validation → Release. |
| **Semantic Status Model** | The 6-stage status of every semantic artifact: Candidate → Investigating → Baseline → Final → Deprecated → Retired. |
| **Investigation Record** | The 10 investigations that produced the foundational semantic architecture, preserved as historical research lineage. |
| **Templates** | Standard formats for new ADRs and CRs to ensure consistency. |

---

## Current State

- **22 ADRs** total (1 final, 21 baseline)
- **1 CR** (CR-WSF-17 Rev.1 — Establish WSF Product Foundation)
- **2 governance documents** (lifecycle + status)
- **1 investigation record** (10 investigations)
- **2 templates** (ADR + CR)

---

## How to Use This Repository

### To understand the WSF architecture

1. Start with the [ADR README](ADR/README.md) to see the canonical ADR sequence.
2. Read ADRs in dependency order: 01 → 02 → 03 → ...
3. Cross-reference with the [Investigation Record](RESEARCH/INVESTIGATION-RECORD.md) for the research lineage.

### To contribute

1. Read [CONTRIBUTING.md](../.github/CONTRIBUTING.md) for the contribution process.
2. Use the [ADR template](templates/ADR-TEMPLATE.md) for architectural decisions.
3. Use the [CR template](templates/CR-TEMPLATE.md) for implementation changes.
4. Follow the [8-stage lifecycle](GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md).
5. Apply the [Semantic Status Model](GOVERNANCE/SEMANTIC-STATUS-MODEL.md) for status tracking.

---

## Architectural Principles

The governance operates under these architectural principles (full list in [12 Foundational Principles](../wsf-docs/conceptual/FOUNDATIONAL-PRINCIPLES.md)):

1. **Semantic Primacy** — Meaning precedes representation.
2. **Minimal Foundation** — The architecture provides the smallest sufficiently expressive foundation.
3. **Explicit Specialization** — Domain concepts specialize; they do not redefine.
4. **Versioned Evolution** — Changes are governed through the lifecycle.
5. **Authoritative Provenance** — Sources are tracked.
6. **Governance First** — Architecture precedes implementation.
7. **Layered Realization** — Multiple levels, distinct concerns.
8. **Traceable Rationale** — Decisions document their reasoning.
9. **Constrained Extensibility** — Extensions follow the governance model.
10. **Verifiable Conformance** — Claims are demonstrable.
11. **Identity by Meaning** — Identity persists through change.
12. **Investigation-Driven** — Architectural decisions follow research.

---

## Related Repositories

- [wsf/](../wsf/) — Canonical semantic assets
- [wsf-spec/](../wsf-spec/) — Normative specifications
- [wsf-examples/](../wsf-examples/) — Reference applications
- [wsf-docs/](../wsf-docs/) — Conceptual documentation
- [wsf-software/](../wsf-software/) — Semantic Engine
- [wsf-connectors/](../wsf-connectors/) — Integration adapters
- [wsf-visuals/](../wsf-visuals/) — Visual semantic assets

---

*The governance provides the authority and lifecycle framework upon which WSF's semantic foundation is built and evolved.*
