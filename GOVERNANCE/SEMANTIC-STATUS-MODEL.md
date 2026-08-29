# Semantic Status Model

> **The 6-stage governance status for every semantic artifact in WSF.**

Per CR-WSF-17 Rev.1 §14, every semantic construct has an explicit status. The status determines how the construct may be used.

---

## The 6-Stage Status Model

```
Candidate → Investigating → Proposed → Normative → Deprecated → Retired
```

| Status | Description | Allowed Uses |
|---|---|---|
| **Candidate** | Initial consideration, no formal review | Internal exploration only |
| **Investigating** | Under formal investigation | Research and discussion |
| **Proposed** | Formally proposed, awaiting decision | ADRs, draft specs |
| **Normative** | Accepted and authoritative | Reference, extension, conformance |
| **Deprecated** | No longer recommended, replacement available | Existing implementations only |
| **Retired** | Formally withdrawn | Historical reference only |

---

## Status Transitions

```
Candidate ──────► Investigating ──────► Proposed ──────► Normative
                                                                      │
                                                                      ▼
                                                                Deprecated
                                                                      │
                                                                      ▼
                                                                   Retired
```

- Each transition requires governance approval
- Status changes are recorded as ADRs or governance decisions
- Deprecated artifacts retain their identity for backward compatibility
- Retired artifacts may retain historical identity but are no longer authoritative

---

## Per-Artifact Status

Each semantic artifact (concept, relationship, assertion type, etc.) has its own status. The WSF kernel is **initially Candidate** and progresses through stages as the implementation matures.

### Initial Status Assignments (Tier 1 — 12 Foundational Candidates)

| Concept | Initial Status | Notes |
|---|---|---|
| Entity | Proposed | Foundation across all 3 foundations |
| Concept | Proposed | Semantic Modeling Foundation |
| Relationship | Proposed | Disposition/Structural/Temporal/Causal/Dispositional |
| Event | Proposed | Occurrence domain |
| State | Proposed | Condition domain |
| Disposition | Proposed | New foundational category |
| Proposition | Proposed | Pre-assertion semantic content |
| Assertion | Proposed | Semantic claims with qualifiers |
| Identity | Proposed | Distinct from Identifier/Name/Reference |
| Context | Proposed | Semantic qualification |
| Time | Proposed | Temporal dimension |
| Space | Proposed | Spatial dimension |

### Initial Status Assignments (Tier 2 — 9 Supporting Constructs)

| Construct | Initial Status |
|---|---|
| Identifier | Proposed |
| Reference | Proposed |
| Namespace | Proposed |
| Term | Proposed |
| Definition | Proposed |
| Validity | Proposed |
| Evidence | Proposed |
| Provenance | Proposed |
| Authority | Proposed |

---

## Status Decision Authority

| Transition | Authority |
|---|---|
| Candidate → Investigating | WSF Working Group |
| Investigating → Proposed | WSF Working Group + ADR |
| Proposed → Normative | ADR Accepted by WSF Governance |
| Normative → Deprecated | ADR Accepted + Replacement Defined |
| Deprecated → Retired | ADR Accepted + Notice Period |

---

## Status Indicators in Repositories

When a semantic artifact is documented in any WSF repository, its status should be indicated:

```yaml
---
semantic_id: <URI>
preferred_name: <name>
status: <Candidate | Investigating | Proposed | Normative | Deprecated | Retired>
version: <semver>
defined_by: <ADR-WSF-XX>
superseded_by: <ADR-WSF-YY> (if applicable)
last_reviewed: <YYYY-MM-DD>
---
```

---

## Status vs Lifecycle

**Status** (this document): Where the artifact is in the governance progression (Candidate → Normative → Retired).

**Lifecycle**: The operational lifecycle (Draft → Active → Superseded → Archived) of a specific version.

These are distinct concepts:
- An artifact can be **Normative** in status but its **Lifecycle** version can be **Deprecated** (a new normative version exists)
- An artifact can be **Candidate** in status but **Active** in lifecycle (being actively worked on)

---

## Migration and Backward Compatibility

When a Normative artifact transitions to Deprecated:
- Its identity is preserved
- A replacement MUST be defined
- Existing implementations continue to work
- New implementations SHOULD use the replacement
- A deprecation period is established

When an artifact transitions to Retired:
- Its identity is preserved for historical reference
- Existing implementations continue to work
- New implementations MUST NOT use it
- Retired artifacts may be physically retained (per Principle 7 — Provenance)

---

## Example Status Lifecycle

```
Day 0:  Status: Candidate       (internal exploration)
Day 7:  Status: Investigating   (formal investigation begins)
Day 30: Status: Proposed        (ADR drafted, awaiting decision)
Day 60: Status: Normative       (ADR accepted, artifact is authoritative)
Day 730: Status: Deprecated    (replacement defined, new work uses replacement)
Day 1095: Status: Retired      (no longer authoritative, but identity preserved)
```

---

*This status model is established per CR-WSF-17 Rev.1 §14. The exact semantics and transition rules shall be refined by a subsequent governance ADR.*
