# ADR-WSF-22 — Assertion and Provenance Model

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-21 — Namespace and Reference Model
Related: ADR-WSF-05, ADR-WSF-06, ADR-WSF-12, ADR-WSF-18, ADR-WSF-19, ADR-WSF-21
Decision Type: Foundational Semantic Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish an **Assertion and Provenance Model** that governs how semantic assertions are constructed, attributed, evidenced, and validated.

The governing principle is:

> **A WSF assertion is a governed, attributed, evidenced claim — not an unverified statement.**

The Assertion and Provenance Model therefore:

- Defines assertion structure (subject, relationship, object, qualifiers);
- Establishes attribution (who asserted, when, with what authority);
- Specifies evidence requirements (what supports the assertion);
- Defines validation framework;
- Distinguishes assertion validity from truth.

---

## 2. Why This Decision Is Necessary

The investigation established that semantic assertions are the bridge between WSF semantics and real-world claims. However:

- Assertions without provenance are unverifiable;
- Assertions without evidence are mere claims;
- Assertions without validation cannot be trusted;
- Assertions conflated with truth produce errors.

A formal Assertion and Provenance Model addresses these issues.

---

## 3. Decision Drivers

The Assertion and Provenance Model must provide:

- **Structured assertions**: Consistent assertion structure.
- **Attribution**: Every assertion is attributed to an agent.
- **Authority**: Assertions are made under recognized authority.
- **Evidence**: Assertions are supported by evidence.
- **Provenance**: Origin and lineage are tracked.
- **Validation**: Assertions can be validated.
- **Trust assessment**: Trust is evaluated, not assumed.
- **Lifecycle**: Assertions have a managed lifecycle.

---

## 4. Assertion Structure

A WSF Assertion SHALL have the following structure:

```yaml
- assertion:
  # Core (required)
  semantic_id: wsf-assertion:<assertion-id>      # Unique identifier
  subject: <Entity or Concept reference>
  relationship: <Relationship reference>
  object: <Entity or Concept reference>
  
  # Optional Qualifiers
  context: <Context reference>
  time: <Time specification>
  conditions: <Conditions under which assertion holds>
  evidence: <Evidence references>
  provenance: <Provenance metadata>
  trust: <Trust assessment>
  
  # Governance
  status: Proposed | Active | Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn
  version: Semantic version
  authority: Governance authority
  created_at: ISO timestamp
  last_modified: ISO timestamp
```

---

## 5. Required vs Optional Components

### Required (MUST be present for a valid assertion)

1. **Semantic Identity**: Stable identifier.
2. **Subject**: What the assertion is about.
3. **Relationship**: How subject relates to object.
4. **Object**: What the subject relates to.
5. **Provenance**: Who asserted it and when.

### Optional (MAY be present)

1. **Context**: The applicable context.
2. **Time**: Temporal validity.
3. **Conditions**: Under what conditions the assertion holds.
4. **Evidence**: Supporting evidence.
5. **Trust**: Trust assessment.

---

## 6. Assertion Lifecycle States

Per ADR-WSF-12, assertions have lifecycle states:

```
Proposed → Active → Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn
```

Each state has specific governance requirements:

| State | Meaning | Governance |
|---|---|---|
| **Proposed** | Newly asserted, awaiting review | Source asserted, awaiting confirmation |
| **Active** | Currently in force | Valid in current context |
| **Confirmed** | Independently verified | Has independent confirming evidence |
| **Disputed** | Contested | Has contradicting evidence |
| **Rejected** | Determined invalid | Has rejecting evidence |
| **Expired** | Past temporal validity | Validity period ended |
| **Superseded** | Replaced by newer assertion | Newer assertion exists |
| **Withdrawn** | Source retracts | Source withdrew assertion |

---

## 7. Truth vs Validity (Critical Distinction)

Per ADR-WSF-12, Assertion is NOT Truth:

- **Assertion**: A semantic claim, valid per its structure.
- **Truth**: Whether the claim corresponds to reality.

An assertion can be:
- Valid (structurally correct) AND True (matches reality);
- Valid AND False (structurally correct, but reality differs);
- Invalid (structurally incorrect).

This distinction is essential for semantic governance.

---

## 8. Provenance Structure

Every assertion SHALL carry provenance:

```yaml
- provenance:
  source: <Source of the assertion>          # Where did this come from?
  asserted_by: <Agent that asserted it>      # Who made this claim?
  asserted_at: <ISO timestamp>                # When was it asserted?
  authority: <Authority for the assertion>    # What gives it weight?
  method: <Method used to assert>             # How was it derived?
  derivation: <Derivation chain if derived>   # If derived, from what?
  references: <External references>          # Supporting references
  last_verified_at: <ISO timestamp>           # Last verification
  last_verified_by: <Agent>                   # Who verified last
```

---

## 9. Evidence Structure

Assertions MAY reference evidence:

```yaml
- evidence:
  - evidence_id: wsf-evidence:<id>
    type: Observation | Measurement | Document | Record | TestResult | ExternalSource
    description: What the evidence shows
    source: Where the evidence came from
    collected_by: Who collected it
    collected_at: When it was collected
    reliability: High | Medium | Low
    confidence: 0.0 to 1.0 (if applicable)
  - ...
```

Evidence types and strength properties are governed separately.

---

## 10. Context in Assertions

Assertions are made in contexts:

```yaml
- assertion:
  ...
  context: wsf-ctx:enterprise-architecture
```

Context applicability follows ADR-WSF-14 (Semantic Context & Boundary).

---

## 11. Time in Assertions

Assertions may have temporal validity:

```yaml
- assertion:
  ...
  time:
    valid_from: ISO timestamp
    valid_until: ISO timestamp or open-ended
    asserted_at: ISO timestamp
    observed_at: ISO timestamp (if observed)
```

Per the Temporal investigation, multiple time dimensions may apply.

---

## 12. Trust Assessment

Assertions MAY carry trust assessment:

```yaml
- assertion:
  ...
  trust:
    level: High | Medium | Low | Unknown
    basis: How trust was assessed
    assessed_by: Who assessed
    assessed_at: When assessed
    independent_verifications: <count>
```

Trust is evaluative, not intrinsic. A high-trust assertion may still be false.

---

## 13. Conditions on Assertions

Assertions MAY be conditional:

```yaml
- assertion:
  subject: OTCHERE Inc
  relationship: possesses
  object: Order Fulfillment Capability
  conditions:
    - if: operational_capacity > 100,000 orders/day
    - if: trained_operators >= 50
```

Conditional assertions are evaluated against current conditions.

---

## 14. Multi-Party Assertions

Some assertions have multiple asserters:

```yaml
- assertion:
  subject: OTCHERE Inc possesses Order Fulfillment Capability
  multi_party_assertion:
    - asserted_by: Kwesi (Enterprise Architect)
    - asserted_by: OTCHERE Inc Board
    - consensus_required: false
    - confidence: High (both agree)
```

Multi-party assertions track agreement and disagreement.

---

## 15. Assertion Validation

Assertions SHALL be validated through:

1. **Structural validation**: Required fields present; correct types.
2. **Identity validation**: All references resolve.
3. **Domain/Range validation**: Subject/object types match relationship.
4. **Context validation**: Context exists and is applicable.
5. **Temporal validation**: Time values are valid.
6. **Evidence validation**: At least one evidence item (for Normative).
7. **Provenance validation**: Source/authority present.

---

## 16. Assertion Validation Levels

| Level | Requirements |
|---|---|
| **Proposed** | Required fields only |
| **Active** | + Context, Provenance |
| **Confirmed** | + At least one evidence item |
| **Verified** | + Independent verification |
| **Normative** | + All validation passes |

Higher levels require more validation.

---

## 17. Assertion Conflicts

When assertions conflict:

```
Assertion A: OTCHERE possesses X
Assertion B: OTCHERE does NOT possess X
   ↓
Conflict detected
   ↓
Resolution paths:
  - Different contexts (no conflict)
  - Different times (no conflict)
  - Different definitions (resolve definition)
  - Genuine disagreement (mark disputed)
  - Error (correct or withdraw)
```

Conflicts are NOT automatically errors; they may reflect legitimate complexity.

---

## 18. Assertion Derivation

Assertions MAY be derived from other assertions:

```yaml
- assertion_X:
  derived_from:
    - assertion_A
    - assertion_B
  derived_using:
    - rule: <derivation rule>
  derivation_method: <method used>
```

Derivation chains preserve provenance.

---

## 19. Assertion Withdrawal

Assertions MAY be withdrawn:

```yaml
- assertion_withdrawal:
  assertion: wsf-assertion:<id>
  withdrawn_by: <agent>
  withdrawn_at: <timestamp>
  reason: <reason for withdrawal>
  superseding_assertion: <new assertion if any>
```

Withdrawn assertions are preserved for history.

---

## 20. Implementation Implications

Upon Acceptance, subsequent CRs SHALL:

1. **CR-WSF-22.1**: Define assertion validation algorithms.
2. **CR-WSF-22.2**: Establish evidence ontology.
3. **CR-WSF-22.3**: Define trust scoring framework.
4. **CR-WSF-22.4**: Establish assertion lifecycle management.

---

## 21. Consequences

### Positive

- Assertions are attributable.
- Evidence is required.
- Validation is possible.
- Trust can be assessed.
- Conflicts can be resolved.
- Derivation is tracked.
- History is preserved.

### Negative

- Validation overhead.
- Evidence collection required.
- Trust assessment complexity.
- Lifecycle management.
- Conflict resolution complexity.

These are accepted consequences.

---

## 22. Rejected Alternatives

### A — Unattributed Assertions

Rejected. Cannot be validated or trusted.

### B — Evidence-Free Assertions

Rejected. Cannot distinguish from mere claims.

### C — Assertion Equals Truth

Rejected. Conflates semantic and epistemic concerns.

### D — Static Assertions

Rejected. Cannot evolve or be superseded.

### E — Implicit Trust

Rejected. Trust must be assessed, not assumed.

---

## 23. Explicit Non-Decisions

This ADR does NOT decide:

- The exact validation algorithms (subsequent CRs).
- The trust scoring specifics (subsequent CRs).
- The full evidence ontology (subsequent CRs).
- The derivation rule language (subsequent CRs).

---

## 24. Decision Summary

The decision can be reduced to one sentence:

> **A WSF assertion is a structured, attributed, evidenced, validatable claim — with explicit provenance, lifecycle, trust assessment, and distinct from truth.**

This is the foundation for trustworthy semantic claims about the world.

---

## 25. Required Follow-On ADRs

The natural next steps are:

```
ADR-WSF-22 Assertion and Provenance Model (this ADR)
       │
       ▼
ADR-WSF-23 Semantic Representation Architecture
       │
       ▼
ADR-WSF-24 WSF Software Architecture
```

---

*This ADR establishes the Assertion and Provenance Model for WSF. Implementation proceeds through subsequent CRs.*
