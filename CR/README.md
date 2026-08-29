# Change Requests (CRs)

> **The Change Requests that implement WSF ADRs.**

CRs are the implementation vehicles for ADRs. Each CR implements one or more ADRs through concrete deliverables in the 8 WSF repositories.

---

## CR Index

| CR | Title | Status | Implements | Date |
|---|---|---|---|---|
| [CR-WSF-17 Rev.1](./CR-WSF-17-Rev.1-Establish-WSF-Product-Foundation.md) | Establish WSF Product Foundation | **Accepted** | ADR-WSF-17 | 2026-08-29 |
| CR-WSF-17 Rev.0 | Establish WSF Foundational Semantic Architecture | **Superseded** | ADR-WSF-17 | 2026-08-29 |

---

## Pending CRs (Future Implementation)

Per CR-WSF-17 Rev.1 §31, the next sequence of ADRs and CRs is:

| Future CR | Future ADR | Scope |
|---|---|---|
| CR-WSF-XX | ADR-WSF-18 | Concept Identity |
| CR-WSF-XX | ADR-WSF-19 | Semantic Relationship Model |
| CR-WSF-XX | ADR-WSF-20 | Concept Definition Model |
| CR-WSF-XX | ADR-WSF-21 | Namespace And Reference Model |
| CR-WSF-XX | ADR-WSF-22 | Assertion And Provenance Model |
| CR-WSF-XX | ADR-WSF-23 | Semantic Representation Architecture |
| CR-WSF-XX | ADR-WSF-24 | WSF Software Architecture |
| CR-WSF-XX | ADR-WSF-25 | WSF Integration Architecture |
| CR-WSF-XX | ADR-WSF-26 | WSF Visualization Architecture |
| CR-WSF-XX | ADR-WSF-27 | WSF Digital Twin and Simulation Architecture |

> **The final ADR/CR numbering shall be reconciled against the existing WSF ADR register before committing these identifiers to prevent numbering collisions.**

---

## 8-Repository Architecture (per CR-WSF-17 Rev.1 §19)

CRs create and maintain content in these 8 repositories:

```
World-Semantic-Foundation/
├── wsf             ← Canonical semantic assets
├── wsf-spec        ← Normative semantic & conformance specifications
├── wsf-governance  ← ADRs, CRs, governance, lifecycle, authority
├── wsf-examples    ← Reference semantic applications
├── wsf-software    ← Deployable WSF Semantic Engine
├── wsf-connectors  ← Integration adapters and semantic mappings
├── wsf-visuals     ← Reproducible visual semantic assets
└── wsf-docs        ← Conceptual & implementation documentation
```

---

## How to Add a New CR

1. Use the [CR Template](../templates/CR-TEMPLATE.md)
2. Place in `wsf-governance/CR/` with sequential number
3. Update this index
4. Reference the ADR(s) being implemented
5. Specify deliverables, acceptance criteria, explicit non-goals
6. Status begins as `Proposed`
7. Transition through `Candidate → Investigating → Proposed → Implemented`

---

## CR Lifecycle

Per the [Change Control Lifecycle](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md):

```
Investigation → Finding → Synthesis → ADR → CR → Implementation → Validation → Release
```

CRs sit at the implementation entry point:

```
ADR (architectural decision)
   ↓
CR (implementation proposal)
   ↓
Implementation
   ↓
Validation
   ↓
Release
```

---

## CR Status States

| Status | Description |
|---|---|
| **Proposed** | Formally proposed, awaiting decision |
| **Accepted** | Approved for implementation |
| **In Progress** | Implementation underway |
| **Implemented** | All deliverables complete |
| **Validated** | Acceptance criteria verified |
| **Released** | Normative content published |
| **Superseded** | Replaced by a later CR |
| **Withdrawn** | Cancelled before implementation |

---

## Conflict Resolution

When CRs appear to conflict:
1. **Implementation order** follows the ADR dependency chain
2. **Related CRs** should be coordinated (sequential or parallel)
3. **Unresolved conflicts** require a new ADR to reconcile

---

## Related Documents

- [GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md) — The 8-stage lifecycle
- [GOVERNANCE/SEMANTIC-STATUS-MODEL.md](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md) — Status model for artifacts
- [RESEARCH/INVESTIGATION-RECORD.md](../RESEARCH/INVESTIGATION-RECORD.md) — Investigation lineage
- [ADR/README.md](../ADR/README.md) — ADR index
- [templates/CR-TEMPLATE.md](../templates/CR-TEMPLATE.md) — Template for new CRs

---

*CRs are the implementation vehicles for WSF. They translate architectural decisions into concrete deliverables.*
