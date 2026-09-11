# ADR-WSF-28: Ecosystem as Tier 3 Worked Example

> **Status:** Proposed
> **Decision Type:** Domain Extension (foundational domain specialisation)
> **Scope:** Ecosystem domain (business ecosystems, digital ecosystems, platform ecosystems)
> **Supersedes:** None
> **Depends On:** ADR-WSF-17, ADR-WSF-04, ADR-WSF-09, ADR-WSF-20, ADR-WSF-07
> **Related:** ADR-WSF-19 (Semantic Relationship Model), ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention)

---

## 1. Context

The World Semantic Foundation has established, across ADR-WSF-01 through ADR-WSF-27, a foundational semantic architecture comprising twelve Tier 1 primitives, nine Tier 2 supporting constructs, and sixteen Tier 3 specialisations, plus the worked example `wsf:Capability`. The architecture is now positioned to admit domain extensions: foundations that specialise Tier 1 primitives for a specific domain while inheriting, without modification, the foundational semantics.

The Ecosystem domain is the first such extension candidate. The vocabulary required to describe ecosystems (actors, platforms, value dynamics, governance, lifecycle, health) is large, coherent, and commercially consequential. Without an explicit ADR, the vocabulary has no authoritative home, no governed namespace, and no basis for federation with the broader semantic-web ecosystem (Schema.org, SKOS, TM Forum).

This ADR establishes the formal basis for the Ecosystem domain within WSF. It defines the root concept, its parent in the foundational taxonomy, its worked-example designation, and the namespace prefix reserved for its relational properties. It defers the actor taxonomy, the value-dynamics vocabulary, and the structural primitives to ADR-WSF-30 and ADR-WSF-31 respectively, each of which depends on this ADR reaching Baseline.

## 2. Decision

WSF shall establish the Ecosystem domain as a governed domain extension of the foundational semantic architecture. The domain is anchored by the concept `wsf:Ecosystem`, defined as follows.

### 2.1 Root concept

`wsf:Ecosystem` is a Tier 3 worked example, specialisation of `wsf:System`, with classification `Tier 3 (Worked Example)`.

**Definition (short).** A system of interacting entities exhibiting emergent properties through mutual influence within a shared context.

**Definition (long).** An Ecosystem is a complex, adaptive system composed of multiple interacting Entities (organisations, individuals, or digital agents) that exchange Value, share a Context, exhibit mutual influence, and produce emergent, system-level properties that none of the constituent entities produces alone. An Ecosystem is bounded by the set of entities whose behaviour materially affects and is affected by the other entities within the system.

**Necessary conditions.**

1. Multiplicity of entities. The system MUST involve more than one Entity.
2. Interaction. Entities MUST interact through Value Exchange, Assertion, or other Relationship kinds.
3. Mutual influence. The behaviour of each entity MUST materially affect and be affected by the others.
4. Shared context. All entities MUST operate within a Context (organisational, technological, regulatory, geographic, or market).
5. Emergence. The system MUST exhibit properties (Network Effects, Lock-In, Ecosystem Health, Lifecycle stage) that are not attributable to any single entity.

**Sufficient conditions.** A set of entities is an Ecosystem if and only if all five necessary conditions hold, AND the relations among entities carry semantic content expressible in WSF relational properties (per ADR-WSF-19).

### 2.2 Worked-example designation

The Tier 3 worked-example designation follows the precedent of `wsf:Capability` (ADR-WSF-07). The designation rests on four observations.

1. Ecosystem is the root concept of an entire domain vocabulary. All other domain concepts (actors, platforms, value dynamics, governance, lifecycle, health) specialise from or relate to it.
2. Ecosystem demonstrates the full specialisation chain. Tier 1 (`wsf:System`) to Tier 3 worked example (Ecosystem) to further Tier 3 specialisations (Business Ecosystem, Digital Business Ecosystem) and onward to actor taxonomy, structural primitives, and value dynamics.
3. Ecosystem requires a relational layer. The domain requires fifteen object properties (filed under the `wsf-rel-eco:` namespace prefix per §2.4) with six modelling rules. No other Tier 3 concept in WSF requires a relational layer of comparable scale.
4. Ecosystem carries the explanatory load of the entire domain. The worked-example treatment ensures the concept receives the rigour of ADR-WSF-20 §14 metadata, full positive, negative, and borderline cases, and a canonical instance drawn from the OTCHERE example vocabulary.

The worked-example designation does not exempt `wsf:Ecosystem` from the change-control discipline. Status progression (Candidate, Investigating, Proposed, Baseline, Final, Deprecated, Retired) applies per the Semantic Status Model.

### 2.3 Tier-1 and Tier-2 rejection (audit trail)

Per Foundational Principle 2 (Minimal Foundation), concepts are admitted to the foundational tier only when their semantics cannot be adequately derived from other WSF primitives without loss of meaning. `wsf:Ecosystem` fails the irreducibility test for Tier 1: it composes from `wsf:Entity`, `wsf:Relationship`, `wsf:Context`, `wsf:Disposition`, `wsf:State`, `wsf:Event`, and `wsf:Time` without loss of meaning. It is therefore correctly placed at Tier 3.

Per ADR-WSF-20 §12, Tier 2 is reserved for epistemic and identification scaffolding (identifier, namespace, term, definition, validity, evidence, provenance, authority). `wsf:Ecosystem` is not a scaffolding construct; it is a domain concept. Tier 2 placement is therefore rejected.

The full tier-classification matrix for the Ecosystem domain, with per-concept validation checks, is maintained in the ecosystem repository at `governance/TIER-CLASSIFICATION-MATRIX.md`.

### 2.4 Namespace reservation

The namespace prefix `wsf-rel-eco:` is reserved for relational properties (object properties, predicates) of the Ecosystem domain. The reservation is global: any ADR or CR proposing a relational property whose domain or range is an Ecosystem concept SHALL use this prefix.

The initial set of fifteen predicates, with domain, range, mathematical properties, and modelling rules, is filed in the ecosystem repository at `concepts/relationships/ecosystem-relational-properties.md`. Subsequent ADRs in the Ecosystem series (ADR-WSF-30, ADR-WSF-31) MAY add to this set, subject to the Change Control Lifecycle.

The reservation does not constrain the `semantic_id` of class concepts. Class concepts continue to use the standard `wsf:` prefix.

### 2.5 Authorisation of dependent ADRs

This ADR authorises the following dependent ADRs as the formal vocabulary of the Ecosystem domain. Each is filed separately and proceeds through the Change Control Lifecycle independently. None of these ADRs is authorised by this ADR; they are listed here so the dependency is visible.

| Dependent ADR | Subject | Status at this ADR |
|---|---|---|
| ADR-WSF-30 | Ecosystem Actor Taxonomy | Awaiting ADR-WSF-28 Baseline |
| ADR-WSF-31 | Ecosystem Value Dynamics | Awaiting ADR-WSF-30 Baseline |
| ADR-WSF-32 | Ecosystem Structural Primitives (Platform and Boundary Resources) | Awaiting ADR-WSF-30 Baseline |
| ADR-WSF-33 | Ecosystem Lifecycle and Health Metrics | Awaiting ADR-WSF-30 and ADR-WSF-31 Baseline |

ADR-WSF-30 through ADR-WSF-33 are reserved slots per the Domain-Extension Numbering Convention (ADR-WSF-29). Re-numbering of any dependent ADR, if required by subsequent governance decisions, does not invalidate this ADR.

## 3. Definition (canonical metadata)

```yaml
concept:
  semantic_id: wsf:Ecosystem
  preferred_name: Ecosystem
  aliases:
    - Ecosystem (general)
    - System-of-Systems
  status: Baseline (pending ADR-WSF-28 acceptance)
  version: 0.1.0
  defined_by: ADR-WSF-28
  classification: Tier 3 (Worked Example)
  parent: wsf:System
  domain: Condition (Emergent properties)

  definition:
    short: "A system of interacting entities exhibiting emergent properties through mutual influence within a shared context."
    long: "An Ecosystem is a complex, adaptive system composed of multiple interacting Entities (organisations, individuals, or digital agents) that exchange Value, share a Context, exhibit mutual influence, and produce emergent, system-level properties that none of the constituent entities produces alone."
    intent: "To provide the foundational domain primitive for ecosystem ontology: a concept that can ground the entire ecosystem vocabulary without requiring the foundation to absorb every domain construct."
    intuition: "What exists when the relationships between entities become as consequential as the entities themselves."

  conditions:
    necessary:
      - "Multiplicity of entities"
      - "Interaction (Value Exchange, Assertion, or other Relationship kinds)"
      - "Mutual influence among entities"
      - "Shared context"
      - "Emergent system-level properties"
    sufficient:
      - "All five necessary conditions hold, AND"
      - "Relations among entities carry semantic content expressible in WSF relational properties."

  constraints:
    inclusion:
      - "MUST involve distinguishable entities with identity."
      - "MUST have interaction patterns assertable as WSF Assertions."
    exclusion:
      - "MUST NOT be a synonym for wsf:System (an Ecosystem is a kind of System, not equivalent)."
      - "MUST NOT be a synonym for Market or Industry (these are analytical lenses)."
      - "MUST NOT collapse into a single Organisation."
    boundary:
      - "Distinguished from wsf:System by (a) agency of components, (b) mutual-influence requirement, (c) expectation of emergence."

  relationships:
    specialises: wsf:System
    specialised_by:
      - wsf:Business Ecosystem
      - wsf:Digital Business Ecosystem
    related_to:
      - wsf:Entity (members)
      - wsf:Relationship (interactions)
      - wsf:Context (shared context)
      - wsf:Disposition (emergent properties)

  examples:
    positive:
      - "A mobile platform with developers, users, advertisers, and device manufacturers."
      - "A healthcare ecosystem with providers, payers, patients, regulators, and pharmaceutical companies."
      - "An open-source software ecosystem with maintainers, contributors, packagers, and end users."
    negative:
      - "A single company with internal departments."
      - "A market segment (analytical lens, not a system of agents)."
      - "A static list of companies in the same industry."
    borderline:
      - "A consortium with shared legal vehicle but minimal operational interaction (qualifies if interactions exceed mere co-membership)."
      - "A supply chain with one-directional flow (qualifies if feedback loops create mutual influence)."

  governance:
    authority: WSF
    adr: ADR-WSF-28
    history:
      - "v0.1.0: Proposed (this ADR)."

  provenance:
    source:
      - "Moore, J. F. (1993), Predators and Prey: A New Ecology of Competition, Harvard Business Review."
      - "Iansiti, M., and Levien, R. (2004), The Keystone Advantage."
      - "Gawer, A., research on platforms and boundary resources."
      - "Rochet, J. C., and Tirole, J., two-sided market theory."
      - "Brandenburger, A., and Nalebuff, B., Coopetition."
    asserted_by: WSF Ecosystem Working Group
    evidence:
      - "Cross-discipline convergence on the construct."
      - "Demonstrated utility in strategy and engineering."
      - "Consistent with WSF Tier 1 primitives."
    references:
      - "VOCAB-000 v2.0 §2.1 (Ecosystem definition)."
      - "ADR-CONCEPTS-01 §1 (ecosystem ontology framing)."
```

## 4. Why this ADR is necessary

The Ecosystem domain vocabulary is already in active use (Moore 1993, Iansiti and Levien 2004, Gawer's research, Rochet and Tirole's two-sided market theory). It is used across strategy consulting, platform economics, public policy, and the design of digital business systems. Three problems arise from the absence of an explicit ADR.

1. **No authoritative home.** Concept definitions in the literature are mutually inconsistent (Moore's lifecycle differs from Adner's ecosystem-as-set-of-firms differs from Iansiti and Levien's keystone-advantage framing). Without an ADR, there is no single authoritative version.
2. **No governed namespace.** Federations with Schema.org, SKOS, and TM Forum cannot be authored because there is no canonical `semantic_id` for ecosystem concepts to federate against.
3. **No worked-example precedent at domain scale.** The `Capability` worked example (ADR-WSF-07) demonstrates a single concept's worked-example treatment. Ecosystem demonstrates the full worked-example treatment of an entire domain. Without this ADR, the pattern is unproven.

The ADR resolves all three. It authorises the root concept, reserves the namespace, and establishes the worked-example pattern at domain scale.

## 5. Consequences

### 5.1 Positive

- The Ecosystem domain gains an authoritative home within WSF.
- The vocabulary becomes citable, federatable, and versionable.
- The worked-example designation demonstrates that the Tier 3 specialisation chain can ground an entire domain without foundation bloat.
- Federation with Schema.org, SKOS, and TM Forum becomes possible (subject to ADR-WSF-25's federation pattern).
- The 12 Foundational Principles and ADR-WSF-17's tier discipline are demonstrated to scale, not just to handle Tier 1 primitives.

### 5.2 Cost

- Fifteen relational properties (filed under `wsf-rel-eco:`) require registration in `wsf-spec/` (Turtle, JSON Schema, Protobuf, OpenAPI).
- Twenty-four Tier 3 classes require registration in `wsf-spec/turtle/wsf-vocabulary.ttl` and `wsf-spec/protobuf/wsf-semantic-engine.proto`.
- SHACL shapes must be authored for the relational properties and the closed-shape constraints documented in ADR-WSF-20 §6.
- Conformance test additions are required in `wsf-software/tests/`.
- The Ecosystem Working Group becomes a standing concern of the foundation, with lifecycle governance obligations.

These costs are accepted consequences of the foundation's decision to admit domain extensions.

### 5.3 Implementation gate

This ADR authorises the change request `CR-WSF-28-Rev.1` (per ADR-WSF-29 sub-numbering convention) to execute the implementation steps listed in §5.2. The CR is filed separately and proceeds through the Change Control Lifecycle.

This ADR does NOT authorise the dependent ADRs (ADR-WSF-30 through ADR-WSF-33). Each dependent ADR is filed separately with its own context, decision, and consequences.

## 6. Alternatives rejected

### A. Flat vocabulary

Rejected because terminology without formal semantic relationships cannot reliably support semantic interoperability. The ecosystem literature is full of related-but-inconsistent terms (network effect vs. network externality; keystone vs. orchestrator vs. focal firm; platform vs. ecosystem). Flat vocabulary preserves the inconsistency.

### B. Universal class hierarchy

Rejected because it forces fundamentally different semantic categories (entities, events, states, relationships, propositions, dispositions) into an inappropriate single taxonomy. ADR-WSF-17 explicitly rejects this alternative.

### C. Domain-first ontology

Rejected because it would make WSF dependent on a particular domain (here, ecosystem theory). The foundation must remain domain-agnostic; domains extend the foundation; the foundation does not extend domains.

### D. Ecosystem as Tier 1

Rejected because Ecosystem composes from Tier 1 primitives without loss of meaning. Tier 1 placement would violate Foundational Principle 2 (Minimal Foundation).

### E. Ecosystem as Tier 2

Rejected because Tier 2 is reserved for epistemic and identification scaffolding (per ADR-WSF-20 §12). Ecosystem is a domain concept, not a scaffolding construct.

### F. Defer the worked-example designation to a later ADR

Rejected because the worked-example designation is structurally inseparable from the root concept decision. Treating them as two ADRs would force the root concept through Baseline without the rigour the worked-example designation requires, then re-open the question.

## 7. Implementation implications

Upon acceptance of this ADR, subsequent CRs and dependent ADRs SHALL proceed as follows.

1. **CR-WSF-28-Rev.1:** Implement the additions to `wsf-spec/` (Turtle vocabulary, JSON Schema, Protobuf messages, OpenAPI endpoints, SHACL shapes).
2. **CR-WSF-28-Rev.2:** Implement the conformance test additions in `wsf-software/tests/`.
3. **ADR-WSF-30:** File the Ecosystem Actor Taxonomy ADR, depending on ADR-WSF-28.
4. **ADR-WSF-31:** File the Ecosystem Value Dynamics ADR, depending on ADR-WSF-30.
5. **ADR-WSF-32:** File the Ecosystem Structural Primitives ADR, depending on ADR-WSF-30.
6. **ADR-WSF-33:** File the Ecosystem Lifecycle and Health Metrics ADR, depending on ADR-WSF-30 and ADR-WSF-31.
7. **Mirror the OTCHERE Platform Ecosystem worked example to `wsf-examples/`** for cross-repo consistency.

## 8. Decision summary

The decision can be reduced to one sentence.

> `wsf:Ecosystem` is established as a Tier 3 worked example specialisation of `wsf:System`, the namespace prefix `wsf-rel-eco:` is reserved for Ecosystem relational properties, and the Ecosystem Working Group is authorised to file dependent ADRs (ADR-WSF-30 through ADR-WSF-33) subject to the Domain-Extension Numbering Convention (ADR-WSF-29).

This ADR establishes the Ecosystem domain within WSF. Implementation proceeds through subsequent CRs and dependent ADRs.

## 9. References

- ADR-WSF-01 through ADR-WSF-27: the foundational and implementational decisions on which this ADR depends.
- ADR-WSF-29 (paired submission): Domain-Extension Numbering and Categorisation Convention.
- VOCAB-000 v2.0 §2.1, §3.1, §3.3, §3.5, §3.6.
- ADR-CONCEPTS-01 §1, §2, §3, §4, §5, §6, §7.
- The ecosystem repository at `World-Semantic-Foundation/wsf-ecosystem` for the full lineage record.

---

*This ADR establishes the Ecosystem domain within the World Semantic Foundation. Implementation proceeds through subsequent CRs and dependent ADRs.*
