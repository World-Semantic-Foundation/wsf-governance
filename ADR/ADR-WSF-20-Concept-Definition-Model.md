# ADR-WSF-20 — Concept Definition Model

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-19 — Semantic Relationship Model
Related: ADR-WSF-01, ADR-WSF-09, ADR-WSF-10, ADR-WSF-11, ADR-WSF-18, ADR-WSF-19
Decision Type: Foundational Semantic Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **Concept Definition Model** that governs how semantic concepts are formally specified, including their definition structure, necessary and sufficient conditions, scope, constraints, and documentation requirements.

The governing principle is:

> **A WSF concept is more than a name and a paragraph; it is a structured, machine-readable specification that supports validation, reasoning, and integration.**

The Concept Definition Model therefore:

- Defines the structural components of a Concept Definition;
- Distinguishes necessary conditions from sufficient conditions;
- Specifies how constraints are expressed;
- Establishes documentation requirements;
- Enables machine-readable concept specifications.

---

## 2. Why This Decision Is Necessary

The investigation showed that semantic concepts vary widely in their definition quality:

- Some concepts are defined by a single paragraph;
- Some have structured definitions with sections;
- Some have formal axioms;
- Some have no formal definition at all.

This inconsistency makes it difficult to:
- Validate that a specialization is correct;
- Reason over concepts automatically;
- Ensure concept specifications are complete;
- Compare concepts across systems;
- Maintain concepts over time.

A Concept Definition Model provides a consistent structure that all WSF concepts follow.

---

## 3. Decision Drivers

The Concept Definition Model must provide:

- **Consistent structure**: Every concept has the same definition structure.
- **Human readability**: Concepts are understandable by humans.
- **Machine readability**: Concepts are processable by machines.
- **Validation support**: Definitions support validation.
- **Reasoning support**: Definitions support controlled reasoning.
- **Comparison**: Concepts can be compared consistently.
- **Evolution**: Concepts can evolve while maintaining structure.
- **Documentation**: Concepts include sufficient documentation.
- **Composition**: Concepts can be composed to define new concepts.

---

## 4. Concept Definition Structure

A WSF Concept Definition SHALL have the following structure:

```yaml
concept_definition:
  # Identification (per ADR-WSF-18)
  identity:
    semantic_id: wsf:<concept-name>
    preferred_name: Human-readable name
    aliases: [Alternative names]
    type: Foundational | Domain | Mechanism | Governance
    status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
    version: Semantic Version

  # Classification (per ADR-WSF-09)
  classification:
    tier: 1 | 2 | 3
    category: Foundational | Domain | Mechanism | Governance
    parent_concept: wsf:<parent-concept>  # if specialized

  # Core Definition
  definition:
    short: One-sentence definition
    long: Detailed multi-paragraph definition
    intent: The purpose of this concept
    intuition: What this concept intuitively captures

  # Conditions (formal)
  conditions:
    necessary: [Conditions that MUST hold]
    sufficient: [Conditions that, together, imply the concept]
    constraints: [Constraints on what is/isn't included]

  # Relationships
  relationships:
    specializes: [Parent concepts]
    specialized_by: [Child concepts]
    related_to: [Related concepts]
    inverse: [Inverse concepts]

  # Examples
  examples:
    positive: [Examples that ARE this concept]
    negative: [Examples that are NOT this concept]
    borderline: [Edge cases]

  # Context
  context_applicability:
    universal: boolean
    contexts: [List of applicable contexts]

  # Governance
  governance:
    authority: Who governs this concept
    adr: The ADR that established this concept
    history: Version history

  # Provenance
  provenance:
    source: Where the concept originated
    asserted_by: Who established it
    evidence: Supporting evidence
    references: [External references]
```

---

## 5. Necessary vs Sufficient Conditions

### Necessary Conditions

Conditions that MUST hold for something to be this concept. If any necessary condition fails, the thing is NOT this concept.

Example for `Capability`:
- MUST involve an Entity (as bearer)
- MUST involve a kind of effect or outcome
- MUST involve potential or grounded possibility

### Sufficient Conditions

Conditions that, when all met, imply that something IS this concept.

Example for `Capability`:
- An Entity has Capacity for something AND
- The Entity has Ability to perform it AND
- The Capacity and Ability combine to produce a grounded potential

A concept definition SHOULD include both necessary and sufficient conditions where possible.

---

## 6. Constraints

Constraints describe what is/isn't included:

```yaml
constraints:
  inclusion:
    - "MUST be a distinguishable entity"
    - "MUST have identity"
  exclusion:
    - "MUST NOT be a synonym for another concept"
    - "MUST NOT be a vague catch-all"
  boundary:
    - "Distinguished from Entity by abstract nature"
    - "Distinguished from Relationship by being a node, not an edge"
```

---

## 7. Documentation Requirements

Every concept definition SHALL include:

1. **Short definition**: One sentence capturing the essence.
2. **Long definition**: Multi-paragraph detailed explanation.
3. **Intent**: Why this concept exists.
4. **Intuition**: What this concept intuitively captures.
5. **Examples**: Positive, negative, borderline.
6. **Relationships**: How it relates to other concepts.
7. **Distinctions**: What it is NOT (boundary markers).

These documentation requirements are non-negotiable for Normative concepts.

---

## 8. Formal vs Informal Specifications

WSF recognizes that concepts may have:

- **Informal specification**: Human-readable, prose-based.
- **Formal specification**: Machine-readable, axiom-based.

A concept MAY have:
- Informal only (during early stages);
- Both informal and formal (at Normative stage).

For Normative concepts, both informal AND formal specifications are RECOMMENDED.

---

## 9. Composition of Concepts

Concepts can be defined through composition:

```
Entity = Disposition (potential to exist) + Identity (distinguishability)
Capability = Capacity + Ability + Context
Role = Entity participation pattern + Behavioral expectations
```

Composition enables:
- Concepts to be defined in terms of other concepts;
- Composition to be checked for consistency;
- New concepts to be defined from existing ones.

---

## 10. Specialization Patterns in Definitions

When a concept specializes another:

```yaml
specialization:
  parent: wsf:Capability
  added_conditions:
    - "Bounded by enterprise context"
    - "Provides business value"
  added_constraints:
    - "Satisfies enterprise value criteria"
  added_relationships:
    - "Enables business outcome"
  specialization_of: wsf:Capability
```

This pattern (per ADR-WSF-04) ensures specializations:
- Inherit parent meaning;
- Add only additional content;
- Remain semantically conformant.

---

## 11. Concept Definition Validation

A concept definition SHALL be validated for:

1. **Completeness**: All required sections present.
2. **Consistency**: No internal contradictions.
3. **Non-circularity**: Definitions don't refer to themselves.
4. **Sufficient disambiguation**: Concept is distinguished from similar concepts.
5. **Examples coverage**: At least positive and negative examples.
6. **Status compliance**: Status appropriate for definition quality.

---

## 12. Required Definition Templates

Per ADR-WSF-09, certain concept categories require additional sections:

### Foundational Concepts (Tier 1)

REQUIRED:
- 6-question ontological test answers
- Distinction from all other Tier 1 concepts
- Universality evidence

### Domain Concepts (Tier 2)

REQUIRED:
- Foundational concepts used
- Domain context
- Specialization pattern (if specialized)

### Mechanism Concepts (Tier 3)

REQUIRED:
- Triggering event/condition
- Effects
- Applicable contexts

---

## 13. Concept Specification Format

The machine-readable specification format SHALL support:

- YAML (human-readable, version-controllable);
- JSON-LD (linked data, web-compatible);
- RDF/Turtle (semantic web);
- OWL XML (formal ontology) — where applicable.

Per ADR-WSF-23 (forthcoming), the representation strategy is decided.

---

## 14. Concept Definition Metadata Schema

The complete metadata schema (consolidated):

```yaml
- concept_definition:
  # ===== Identification =====
  semantic_id: wsf:<concept-name>
  preferred_name: <Human-readable name>
  aliases: [<Alternative names>]
  
  # ===== Classification =====
  tier: 1 | 2 | 3
  category: Foundational | Domain | Mechanism | Governance
  parent: wsf:<parent-concept>
  
  # ===== Status =====
  status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
  version: <semantic version>
  authority: <governance authority>
  
  # ===== Definition =====
  short_definition: <one sentence>
  long_definition: <detailed>
  intent: <purpose>
  intuition: <intuitive meaning>
  
  # ===== Conditions =====
  necessary_conditions:
    - <condition>
  sufficient_conditions:
    - <condition>
  
  # ===== Constraints =====
  inclusion_constraints:
    - <inclusion rule>
  exclusion_constraints:
    - <exclusion rule>
  
  # ===== Relationships =====
  specializes: [<parent concepts>]
  specialized_by: [<child concepts>]
  related_to: [<related concepts>]
  
  # ===== Examples =====
  positive_examples:
    - <example>
  negative_examples:
    - <counter-example>
  borderline_examples:
    - <edge case>
  
  # ===== Context =====
  universal: <boolean>
  applicable_contexts:
    - <context>
  
  # ===== Governance =====
  governing_adr: <ADR reference>
  established_date: <date>
  last_modified_date: <date>
  
  # ===== Provenance =====
  source: <origin>
  asserted_by: <agent>
  evidence: [<evidence>]
  references: [<reference>]
```

---

## 15. Concept Definition Lifecycle

```
1. Concept candidate identified
       ↓
2. Initial definition drafted (informal)
       ↓
3. Conditions and constraints specified
       ↓
4. Examples gathered (positive/negative/borderline)
       ↓
5. Relationships mapped
       ↓
6. Definition reviewed for completeness
       ↓
7. Definition status: Proposed
       ↓
8. Formal specification added (if applicable)
       ↓
9. Definition status: Normative
       ↓
10. Definition evolves (semantic evolution per ADR-WSF-16)
```

---

## 16. Implementation Implications

Upon Acceptance, subsequent CRs SHALL:

1. **CR-WSF-20.1**: Apply Concept Definition Model to all existing WSF concepts (Entity, Concept, Identity, Capability, Relationship).
2. **CR-WSF-20.2**: Establish YAML/JSON-LD specification formats.
3. **CR-WSF-20.3**: Define validation algorithms for concept completeness.
4. **CR-WSF-20.4**: Document templates for each concept category.

---

## 17. Consequences

### Positive

- Concepts are consistently structured.
- Validation is possible.
- Reasoning is enabled.
- Comparison is consistent.
- Evolution is governed.
- Documentation is complete.

### Negative

- More upfront work per concept.
- Validation overhead.
- Schema must be maintained.
- Concepts may resist neat categorization.

These are accepted consequences.

---

## 18. Rejected Alternatives

### A — Free-form Definitions

Rejected. Inconsistent, hard to validate.

### B — Pure Formal Definitions

Rejected. Excludes human readability.

### C — Definition by Example

Rejected. Insufficient rigor.

### D — Definition by Extension

Rejected. Cannot enumerate all instances.

### E — Definition by Negation

Rejected. Defines what something isn't, not what it is.

### F — No Definition

Rejected. Cannot be reasoned over.

---

## 19. Explicit Non-Decisions

This ADR does NOT decide:

- The exact serialization format (governed by ADR-WSF-23).
- The reasoning algorithm details (subsequent CRs).
- The complete concept definitions (each concept authored through subsequent CRs).

---

## 20. Decision Summary

The decision can be reduced to one sentence:

> **Every WSF concept is defined through a structured specification that includes identity, classification, definition, conditions, constraints, relationships, examples, context, governance, and provenance — supporting both human understanding and machine processing.**

This is the foundation for valid, comparable, evolvable concept definitions.

---

## 21. Required Follow-On ADRs

The natural next steps are:

```
ADR-WSF-20 Concept Definition Model (this ADR)
       │
       ▼
ADR-WSF-21 Namespace and Reference Model
       │
       ▼
ADR-WSF-22 Assertion and Provenance Model
       │
       ▼
ADR-WSF-23 Semantic Representation Architecture
```

---

*This ADR establishes the model for Concept Definitions in WSF. Implementation proceeds through subsequent CRs.*
