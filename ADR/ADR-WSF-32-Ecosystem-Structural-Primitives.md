# ADR-WSF-32: Ecosystem Structural Primitives

> **Status:** Proposed
> **Decision Type:** Domain Extension (structural primitives specialisation)
> **Scope:** Ecosystem domain structural primitives (Platform, Boundary Resources, Modularity, Interoperability Standards, Coupling Level, Marketplace)
> **Supersedes:** None
> **Depends On:** ADR-WSF-28, ADR-WSF-30, ADR-WSF-20, ADR-WSF-04, ADR-WSF-09
> **Related:** ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention), ADR-WSF-31 (Ecosystem Value Dynamics)
> **Paired submission:** This ADR was filed in a Draft PR alongside its parents (ADR-WSF-28 and ADR-WSF-30). Both parents have reached Baseline: ADR-WSF-28 was merged via PR #1 on 2026-09-11; ADR-WSF-30 was merged via PR #4 on 2026-09-13. The section 0 Pre-Baseline caveat is now fully historical; see section 0.1 for the transition record.

---

## 0. Pre-Baseline caveat (historical)

This ADR was originally filed as a Draft PR with a Pre-Baseline caveat citing its parents (ADR-WSF-28 and ADR-WSF-30) at status Proposed. The convention established by ADR-WSF-29 permits this filing pattern: paired or chained submissions may be filed together so reviewers can evaluate the dependency in a single review window.

## 0.1 Status transition record

| Date | Event | Status |
|---|---|---|
| 2026-09-12 (filing) | Draft PR opened on branch `adr-32-structural-primitives` | Proposed (Pre-Baseline) |
| 2026-09-12 | ADR-WSF-28 already Baseline (PR #1 merged 2026-09-11) | Proposed (one parent Baseline, one Proposed) |
| 2026-09-13 | ADR-WSF-30 merged via PR #4, reached Baseline | Proposed (parents all Baseline) |
| 2026-09-14 | Section 0 caveat cleared; status updated to `Proposed`; PR #6 marked ready for review | Proposed (under review) |

ADR-WSF-30 reached Baseline on 2026-09-13 without surfacing changes that affect the structural primitives (no re-parenting of `wsf:Platform`, no Boundary Resources modelling revision, no structural vocabulary change). The Pre-Baseline caveat is therefore cleared. This ADR is now at status **Proposed**, awaiting governance review for transition to Baseline.

## 1. Context## 1. Context

ADR-WSF-28 establishes the Ecosystem domain as a governed WSF extension. ADR-WSF-30 establishes six Tier 3 actor concepts (Orchestrator, Complementor, Dominator, Gatekeeper, Prosumer, Boundary Spanner) and the Overlapping Roles principle. The structural primitives vocabulary captures the substrate on which ecosystem interactions occur.

The vocabulary surfaced by the source literature splits naturally into three layers:

1. **Assets:** Platform, Marketplace, Boundary Resources.
2. **Properties:** Modularity, Interoperability Standards, Coupling Level.
3. **Relationships:** Boundary Resources are provided by the Orchestrator to Complementors; Modularity and Interoperability Standards are properties of the Platform; Coupling Level is a property of actor-actor or actor-platform relationships.

This ADR establishes six Tier 3 specialisations across the structural primitives domain. Five parented to Tier 1 primitives; one (Marketplace) parented to `wsf:Platform`. One modelling decision is documented as applied intelligence: Boundary Resources are modelled as a separate Entity specialisation, not as a kind of Platform, to preserve the operational distinction.

## 2. Decision

### 2.1 Tier 1 and Tier 2 rejection (audit trail)

Per Foundational Principle 2 (Minimal Foundation), concepts are admitted to the foundational tier only when their semantics cannot be adequately derived from other WSF primitives without loss of meaning. None of the six structural primitives is irreducible: each composes from Tier 1 primitives without loss of meaning. Tier 1 placement is rejected for all six.

Per ADR-WSF-20 §12, Tier 2 is reserved for epistemic and identification scaffolding. The structural primitives are domain concepts, not scaffolding constructs. Tier 2 placement is rejected for all six.

The full tier-classification matrix is maintained in `wsf-ecosystem/governance/TIER-CLASSIFICATION-MATRIX.md`.

### 2.2 The six concepts

#### 2.2.1 `wsf:Platform`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Entity`
- **Domain:** Structure
- **Specialisations:** `wsf:Marketplace`, `wsf:Innovation Platform`, `wsf:Data Platform`, `wsf:Services Platform`
- **Definition (short):** The foundational asset upon which ecosystem interactions occur; the locus of value creation and mediation.
- **Definition (long):** A Platform is a technological, brand, or infrastructural asset upon which ecosystem interactions occur. The Platform is the locus of value creation and mediation. The Platform is the asset; the Ecosystem is the community of users + complementors + their interactions. The Platform/Ecosystem distinction is critical: a Platform may exist without an Ecosystem (a built-but-empty platform); an Ecosystem may exist across multiple Platforms.
- **Necessary conditions:**
  1. All `wsf:Entity` necessary conditions (inherited).
  2. **Multi-actor affordance.** MUST enable interaction between multiple actors.
  3. **Foundational role.** MUST function as the substrate (not merely a participant) of the ecosystem.
- **Boundary markers:** Distinguished from `wsf:Ecosystem` by being an asset rather than a community. Distinguished from `wsf:Boundary Resources` by being the asset that provides the resources, not the resources themselves.
- **Lineage:** Gawer and Cusumano (2002, 2014); Rochet and Tirole (2003); ADR-CONCEPTS-01 §2.1; VOCAB-000 v2.0 §3.2.1.

#### 2.2.2 `wsf:Marketplace`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Platform`
- **Domain:** Structure
- **Definition (short):** A multi-sided platform subtype that intermediates transactions between distinct actor groups, monetising via take rates.
- **Definition (long):** A Marketplace is a Platform subtype specialised for transaction intermediation between at least two distinct actor groups (buyers and sellers in the canonical case; or developers and users in the App Store case). The Marketplace monetises via take rates or equivalent per-transaction fees. The Marketplace is a transaction venue, not the ecosystem itself.
- **Necessary conditions:**
  1. All `wsf:Platform` necessary conditions (inherited).
  2. **Multi-sided intermediation.** MUST connect at least two distinct actor groups in a transaction relationship.
  3. **Take-rate monetisation.** MUST extract value via per-transaction fees (or equivalent monetisation mechanism).
- **Boundary markers:** Distinguished from `wsf:Platform` by transaction-intermediation specialisation. Distinguished from `wsf:Ecosystem` by being an asset rather than a community.
- **Lineage:** Rochet and Tirole (2003); ADR-CONCEPTS-01 §2.1 (referenced as implicit); VOCAB-000 v2.0 §3.2.2.

#### 2.2.3 `wsf:Boundary Resources`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Entity` (deliberately, not `wsf:Platform`)
- **Domain:** Structure (Gawer construct)
- **Definition (short):** The tools, interfaces, and documentation provided by the Orchestrator to enable Complementors to build on the platform.
- **Definition (long):** Boundary Resources are concrete, engineered surfaces (APIs, SDKs, sandboxes, developer portals, documentation, design guidelines) provided by the Orchestrator (or a delegated actor) to enable Complementors to build on the platform. Boundary Resources are the operational mechanism by which an Orchestrator enables Complementor activity without reimplementing the platform itself. The design of Boundary Resources is itself a strategic act: too open invites value slippage and dominator risk; too closed prevents complementor investment.
- **Necessary conditions:**
  1. All `wsf:Entity` necessary conditions (inherited).
  2. **Orchestrator provision.** MUST be provided by an Orchestrator (or a delegated actor).
  3. **Complementor enabling.** MUST be designed for and consumable by Complementors.
- **Boundary markers:** Distinguished from `wsf:Platform` by being the interfaces that the Platform provides, not the Platform itself. Distinguished from `wsf:Boundary Spanner` (an actor-class) by being an Entity, not an Actor.
- **Lineage:** Gawer (research on platforms and boundary resources); ADR-CONCEPTS-01 §2.1; VOCAB-000 v2.0 §3.2.3.
- **Modelling decision (applied intelligence):** Boundary Resources are modelled as a separate Entity specialisation (parent `wsf:Entity`), not as a kind of Platform (which would make them identical to the Platform). This preserves the operational distinction: Boundary Resources are the interfaces that the Platform provides, not the Platform itself. The reasoning is recorded in `wsf-ecosystem/research/02-tier-classification/FINDING-Tier-Classification.md` and `wsf-ecosystem/concepts/tier-3/boundary-resources.md`.

#### 2.2.4 `wsf:Modularity`

- **Classification:** Tier 3 (Specialisation, disposition)
- **Parent:** `wsf:Disposition`
- **Domain:** Structure
- **Definition (short):** The architectural property allowing the ecosystem to be decomposed into independent, interchangeable components with defined interfaces.
- **Definition (long):** Modularity is the disposition of the platform such that the system can be decomposed into independently-modifiable components with stable interfaces. High modularity enables parallel innovation by complementors without forcing them to coordinate; low modularity creates coupling risks.
- **Necessary conditions:**
  1. All `wsf:Disposition` necessary conditions (inherited).
  2. **Decomposability.** The system MUST be decomposable into independently-modifiable components.
  3. **Interface definition.** Component interfaces MUST be specified and stable.
- **Boundary markers:** Distinguished from `wsf:Coupling Level` (a descriptive structural property of relationships) by being a disposition of the platform (an architectural property). Distinguished from `wsf:Interoperability Standards` (Rule specifications) by being a tendency, not a specification.
- **Lineage:** Baldwin and Clark (2000); ADR-CONCEPTS-01 §2.1; VOCAB-000 v2.0 §3.2.4.

#### 2.2.5 `wsf:Interoperability Standards`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Rule`
- **Domain:** Structure / Governance
- **Definition (short):** Shared protocols, data formats, and technical rules that allow distinct actors to interact with low friction.
- **Definition (long):** Interoperability Standards are the shared rules (protocols, data formats, schemas, technical conventions) that allow distinct actors to interact with reduced transaction cost. They are the connective tissue of the platform. Standard-setting is political: standards confer power; premature standardisation can freeze inferior designs.
- **Necessary conditions:**
  1. All `wsf:Rule` necessary conditions (inherited).
  2. **Shared adoption.** MUST be adopted by multiple actors.
  3. **Friction reduction.** MUST materially reduce interaction cost.
- **Boundary markers:** Distinguished from `wsf:Modularity` (a disposition) by being a specification. Distinguished from `wsf:Policy` (a higher-level governance construct) by being technical rather than organisational.
- **Lineage:** Standard-setting literature; ADR-CONCEPTS-01 §2.1; VOCAB-000 v2.0 §3.2.5.

#### 2.2.6 `wsf:Coupling Level`

- **Classification:** Tier 3 (Specialisation, descriptive property)
- **Parent:** `wsf:Relationship`
- **Domain:** Structure
- **Definition (short):** A descriptive structural property defining the degree of dependency between actors or between an actor and a platform.
- **Definition (long):** Coupling Level is the descriptive property of an actor-actor or actor-platform relationship, characterising the dependency as **Tight** (deep integration, high dependency) or **Loose** (independent, standardised interaction). Coupling is pairwise, not global: the same actor may be tightly coupled to one platform and loosely coupled to another.
- **Necessary conditions:**
  1. All `wsf:Relationship` necessary conditions (inherited).
  2. **Degree assertion.** MUST specify the degree (Tight or Loose) and the dimension (technical, contractual, data, etc.).
  3. **Pairwise scoping.** MUST be asserted per actor pair (or per actor-platform pair), not globally.
- **Boundary markers:** Distinguished from `wsf:Modularity` (a disposition of the platform) by being a property of a specific relationship. Distinguished from `wsf:Switching Costs` (an exit-friction disposition) by being a present-state description, not an exit-friction tendency.
- **Lineage:** ADR-CONCEPTS-01 §2.1; VOCAB-000 v2.0 §3.2.6.

### 2.3 Relational properties for structural primitives

The relational properties that connect structural primitives to actor concepts and value-dynamics concepts are documented in `wsf-ecosystem/research/03-relationship-grammar/`. The key predicates:

| Predicate | Domain | Range | Symmetric | Notes |
|---|---|---|---|---|
| `wsf-rel-eco:orchestrates` | `wsf:Actor` (Orchestrator) | `wsf:Platform` | false | Per ADR-WSF-30 §2.2.1 |
| `wsf-rel-eco:complements` | `wsf:Actor` (Complementor) | `wsf:Platform` | false | Per ADR-WSF-30 §2.2.2 |
| `wsf-rel-eco:provides` | `wsf:Orchestrator` | `wsf:Boundary Resources` | false | New in this ADR |
| `wsf-rel-eco:exhibits` | `wsf:Platform` | `wsf:Network Effect` | false | Per ADR-WSF-31 §2.2.1 |
| `wsf-rel-eco:is_coupled_with` | `wsf:Actor` (or Relationship) | `wsf:Actor` (or Relationship) | true | Per ADR-WSF-30 §2.3 |

### 2.4 Namespace and serialisation

The six structural primitives use the standard `wsf:` namespace prefix for classes. The relational property `wsf-rel-eco:provides` uses the `wsf-rel-eco:` namespace prefix reserved by ADR-WSF-28 §2.4.

Serialisation in `wsf-spec/` (Turtle, JSON Schema, Protobuf, OpenAPI) is authorised through the downstream CR (Issue #4 in `wsf-ecosystem`, gated on this ADR reaching Baseline).

## 3. Why this ADR is necessary

The structural primitives vocabulary is the substrate on which the actor taxonomy and value dynamics play out. Without this ADR:

1. `wsf:Platform` and `wsf:Boundary Resources` have no authoritative modelling pattern. Without Boundary Resources as a separate Entity, the operational distinction between Platform and its interfaces is lost.
2. `wsf:Modularity` and `wsf:Coupling Level` have no formal modelling pattern. The platform-architecture property and the relationship property are conflated without separate concepts.
3. The downstream CR (Issue #4) cannot register structural primitives in `wsf-spec/`.
4. Downstream ADRs (particularly ADR-WSF-33 Lifecycle and Health) cannot fully ground their health metrics without the structural substrate.

## 4. Consequences

### 4.1 Positive

- The Ecosystem domain gains an authoritative structural primitives dimension.
- Boundary Resources are correctly modelled as a separate Entity, supporting analytics on Platform openness.
- Modularity and Coupling Level are distinguished by ontological category (disposition vs. relationship).
- Downstream ADRs (ADR-WSF-33) gain their structural parent.

### 4.2 Cost

- Six concepts require registration in `wsf-spec/`.
- SHACL shapes must be authored for the six concepts and for the `provides` predicate.
- Conformance tests are required for the structural primitives vocabulary.

### 4.3 Implementation gate

The transition of this ADR to Baseline is contingent on ADR-WSF-30 reaching Baseline. Until then, this ADR remains at status Proposed (Pre-Baseline) and is not citable as authoritative.

## 5. Alternatives rejected

### A. Boundary Resources as a kind of Platform

Rejected. Boundary Resources are the interfaces that the Platform provides, not the Platform itself. Modelling Boundary Resources as a kind of Platform collapses the operational distinction. The reasoning is in `wsf-ecosystem/research/02-tier-classification/FINDING-Tier-Classification.md`.

### B. Tier 1 placement for any structural primitive

Rejected. All six concepts compose from Tier 1 primitives without loss of meaning.

### C. Tier 2 placement for any structural primitive

Rejected. Tier 2 is reserved for epistemic and identification scaffolding.

### D. Fold Modularity into Interoperability Standards

Rejected. Modularity is a disposition of the platform (an architectural tendency); Interoperability Standards are Rules (specifications). Confusing them loses the disposition-vs-specification distinction.

### E. Fold Coupling Level into Modularity

Rejected. Modularity is a property of the platform; Coupling Level is a property of a specific relationship. They operate at different levels of analysis.

### F. Defer the structural primitives to a later ADR

Rejected. The structural primitives are required by ADR-WSF-33 (Lifecycle and Health) for the health-metrics grounding.

## 6. Decision summary

The decision can be reduced to one sentence.

> Six Tier 3 specialisations of Tier 1 primitives (Platform and Boundary Resources parented to `wsf:Entity`; Modularity parented to `wsf:Disposition`; Interoperability Standards parented to `wsf:Rule`; Coupling Level parented to `wsf:Relationship`; Marketplace parented to `wsf:Platform`) are established as the Ecosystem domain structural primitives, with Boundary Resources modelled as a separate Entity specialisation to preserve the operational distinction from Platform.

This ADR is filed as a Draft PR. Its transition to Baseline is contingent on ADR-WSF-30 reaching Baseline.

## 7. Required follow-on actions

1. File ADR-WSF-33 (Ecosystem Lifecycle and Health Metrics) as a Draft PR, dependent on this ADR and ADR-WSF-31.
2. Author SHACL shapes for the six concepts and the `provides` predicate.
3. Mirror the structural primitives concept files from `wsf-ecosystem/concepts/tier-3/` to `wsf-examples/`.

## 8. References

- ADR-WSF-04 (Semantic Inheritance): specialisation rules.
- ADR-WSF-09 (Foundational Concept Taxonomy): tier-classification framework.
- ADR-WSF-17 (Foundational Semantic Architecture): tier discipline.
- ADR-WSF-19 (Semantic Relationship Model): metadata schema for relational properties.
- ADR-WSF-20 (Concept Definition Model): §14 metadata schema.
- ADR-WSF-28 (Ecosystem as Tier 3 Worked Example): root parent.
- ADR-WSF-30 (Ecosystem Actor Taxonomy): immediate parent.
- ADR-WSF-31 (Ecosystem Value Dynamics): sibling ADR (cross-reference for the value-dynamics vocabulary).
- VOCAB-000 v2.0 §3.2: source vocabulary.
- ADR-CONCEPTS-01 §2.1: source concept catalogue.
- Gawer, A., and Cusumano, M. (2002, 2014): platform strategy and boundary resources.
- Baldwin, C. Y., and Clark, K. B. (2000), *Design Rules: The Power of Modularity*.

### Source artifacts in `wsf-ecosystem`

- `concepts/tier-3/platform.md`, `marketplace.md`, `boundary-resources.md`, `modularity.md`, `interoperability-standards.md`, `coupling-level.md`.
- `research/01-source-reconciliation/FINDING-Source-Reconciliation.md`: source-to-concept lineage.
- `research/02-tier-classification/FINDING-Tier-Classification.md`: tier-classification rationale, including the Boundary Resources modelling decision.
- `research/03-relationship-grammar/FINDING-Relationship-Grammar.md`: relational properties and modelling rules.
- `governance/TIER-CLASSIFICATION-MATRIX.md`: per-concept tier matrix.

---

*This ADR establishes the Ecosystem domain structural primitives. Its transition to Baseline is contingent on ADR-WSF-30 reaching Baseline.*
