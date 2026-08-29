# Change Requests (CRs)

> **The implementation change requests that realize the WSF architectural decisions.**

CRs are the implementation vehicles for ADRs. Each CR implements one or more ADRs through concrete deliverables in the WSF repositories.

---

## Change Request Index

| CR | Title | Status | Implements |
|---|---|---|---|
| [CR-WSF-17 Rev.1](./CR-WSF-17-Rev.1-Establish-WSF-Product-Foundation.md) | Establish WSF Product Foundation | Final | ADR-WSF-17 |

---

## What is a CR?

A Change Request (CR) is an implementation specification that:

- Implements one or more Architectural Decision Records (ADRs)
- Specifies the concrete deliverables (repositories, files, components, configurations)
- Defines the acceptance criteria
- Establishes the verification approach
- Maintains traceability from decision to implementation

CRs are distinct from ADRs in purpose:

| Aspect | ADR | CR |
|---|---|---|
| **What** | Architectural decision | Implementation specification |
| **Why** | Captures context, drivers, rationale | Implements a decision with concrete deliverables |
| **How** | States the chosen architecture | Specifies the artifacts, files, and configuration |
| **Scope** | Architectural concern | Implementation concern |
| **Review** | Architecture review | Implementation review |

---

## CR Lifecycle

CRs follow the [8-stage Change Control Lifecycle](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md):

```
Investigation → Finding → Synthesis → ADR → CR → Implementation → Validation → Release
```

The CR is the bridge between the ADR (architectural decision) and the Implementation (concrete deliverable).

---

## Authoring New CRs

1. Use the [CR Template](../templates/CR-TEMPLATE.md).
2. Reference the ADR(s) being implemented.
3. Specify the concrete deliverables (repositories, files, components).
4. Define acceptance criteria and verification approach.
5. Place in `wsf-governance/CR/` with a sequential number.
6. Update this index.

---

## Related Documents

- [GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md) : The 8-stage lifecycle
- [GOVERNANCE/SEMANTIC-STATUS-MODEL.md](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md) : The 6-stage status model
- [templates/CR-TEMPLATE.md](../templates/CR-TEMPLATE.md) : Template for new CRs

---

*CRs are the implementation specification for the WSF architectural decisions.*
