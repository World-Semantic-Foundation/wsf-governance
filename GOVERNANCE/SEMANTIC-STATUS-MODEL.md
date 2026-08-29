# Semantic Status Model

> **The 6-stage governance status for every semantic artifact in the World Semantic Foundation.**

Every semantic artifact has an explicit status that determines how it is treated by the architecture and by downstream consumers. The status model establishes the controlled vocabulary of semantic lifecycle states.

---

## The 6 Stages

```
Candidate → Investigating → Proposed → Baseline → Deprecated → Retired
```

The status flow is:

| From | To | Trigger |
|---|---|---|
| Candidate | Investigating | Investigation begins |
| Investigating | Proposed | Synthesis completes |
| Proposed | Baseline | Architectural decision recorded (ADR) |
| Baseline | Final | Implementation verified (CR) |
| Baseline | Deprecated | Replaced or superseded |
| Baseline | Retired | Withdrawn or obsolete |
| Deprecated | Retired | Historical record complete |

**Note**: Not all artifacts progress through all stages. Some retire early, others skip stages when appropriate.

---

## Status Definitions

### Candidate

A potential semantic artifact has been identified but not yet investigated. The candidate is provisional and may not survive investigation.

**Properties:**
- Identity may be provisional
- Definition is incomplete or absent
- No authoritative commitment
- May be removed without notice

### Investigating

The semantic artifact is under active investigation. The investigation gathers evidence, considers alternatives, and produces findings.

**Properties:**
- Investigation findings exist
- Definition may be partial
- Authority is the investigation team
- May evolve substantially

### Proposed

The semantic artifact has completed investigation. A synthesis document captures the implications and recommendations.

**Properties:**
- Investigation findings are final
- Synthesis captures implications
- Definition may be partial
- Authority is the synthesis team

### Baseline

The architectural decision has been formalized as an ADR. The semantic artifact is the authoritative baseline for the foundation.

**Properties:**
- ADR exists and references the artifact
- Definition is formalized
- Authority is established
- Downstream consumers may specialize
- Subject to evolution (additive changes possible)
- Versioned per [ADR-WSF-16](../ADR/ADR-WSF-16-Semantic-Evolution-Versioning.md)

### Final

The implementation has been verified. The semantic artifact is the final, production-ready form for the foundation.

**Properties:**
- ADR + CR exist
- Implementation is verified
- Conformance is validated
- Production-ready
- Subsequent changes trigger new artifact identities

### Deprecated

The semantic artifact is no longer recommended for new use. It remains available for existing references but should not be used for new specializations.

**Properties:**
- Replaced by a successor or superseded
- Existing references remain valid
- New specializations discouraged
- Migration guidance provided

### Retired

The semantic artifact is no longer in active use. It is preserved for historical reference but is not maintained.

**Properties:**
- Preserved for audit trail
- Historical interpretability maintained
- No further evolution
- Reading-only

---

## Status Transitions

### Forward Transitions

Forward transitions are governed by the [Change Control Lifecycle](./CHANGE-CONTROL-LIFECYCLE.md).

### Backward Transitions

Backward transitions are permitted only with explicit governance:

| Transition | Allowed | Governance |
|---|---|---|
| Investigating → Candidate | Yes | Investigation abandoned |
| Proposed → Investigating | Yes | New evidence requires re-investigation |
| Baseline → Proposed | Limited | Breaking change requires re-decision |
| Final → Baseline | Limited | Defect correction with governance |
| Deprecated → Baseline | Yes | Deprecation rescinded |
| Retired → (any) | No | Retirement is terminal |

---

## Status in Semantic Assertions

Semantic assertions reference their underlying concepts at specific statuses:

```yaml
- assertion:
  subject: wsf-cap:OrderFulfillment
  status_at_assertion: Baseline  # The concept was at Baseline status when this assertion was made
```

This preserves the historical validity of assertions even after concept status changes.

---

## Status in Repositories

Each repository declares the status of its artifacts. The status metadata travels with the artifact through its lifecycle.

```yaml
- concept:
  semantic_id: wsf:Entity
  status: Baseline
  version: 1.0.0
  ...
```

---

## Related Documents

- [CHANGE-CONTROL-LIFECYCLE.md](./CHANGE-CONTROL-LIFECYCLE.md) — The 8-stage lifecycle
- [../ADR/ADR-WSF-16-Semantic-Evolution-Versioning.md](../ADR/ADR-WSF-16-Semantic-Evolution-Versioning.md) — Versioning model
- [../ADR/ADR-WSF-15-Semantic-Authority-Governance.md](../ADR/ADR-WSF-15-Semantic-Authority-Governance.md) — Authority model

---

*The Semantic Status Model is the controlled vocabulary of semantic lifecycle states.*
