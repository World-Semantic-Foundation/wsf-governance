# ADR-WSF-30: Ecosystem Actor Taxonomy

> **Status:** Baseline
> **Decision Type:** Domain Extension (actor taxonomy specialisation)
> **Scope:** Ecosystem domain actor roles
> **Supersedes:** None
> **Depends On:** ADR-WSF-28, ADR-WSF-20, ADR-WSF-04, ADR-WSF-09
> **Related:** ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention)
> **Paired submission:** This ADR was filed as a Draft PR alongside its parent (ADR-WSF-28). ADR-WSF-28 has reached Baseline (PR #1 merged 2026-09-11). The §0 Pre-Baseline caveat is now historical; see §0.1 for the transition record.
> **Transition record (2026-09-13):** ADR-WSF-30 reaches Baseline as of the merge of PR #4. Parent ADR-WSF-28 was already Baseline. The §0 Pre-Baseline caveat (which referenced the unratified state of this ADR's parents) is now fully historical. The §0.1 transition record was inserted to preserve the audit trail.

---

## 0. Pre-Baseline caveat (historical)

This ADR was originally filed as a Draft PR with a Pre-Baseline caveat citing its parent (ADR-WSF-28) at status Proposed in PR #1. The convention established by ADR-WSF-29 permits this filing pattern: paired or chained submissions may be filed together so reviewers can evaluate the dependency in a single review window.

## 0.1 Status transition record

| Date | Event | Status |
|---|---|---|
| 2026-09-11 (filing) | Draft PR opened | Proposed (Pre-Baseline) |
| 2026-09-11 | ADR-WSF-28 merged via PR #1, reached Baseline | Proposed (parent Baseline) |
| 2026-09-11 | PR #2 reopened and marked ready for review | Proposed (under review) |

ADR-WSF-28 reached Baseline on 2026-09-11 without surfacing changes that affect the actor taxonomy (no namespace shift, no worked-example designation revision, no parent reassignment). The Pre-Baseline caveat is therefore cleared. This ADR is now at status **Proposed**, awaiting governance review for transition to Baseline.

## 1. Context

ADR-WSF-28 establishes the Ecosystem domain as a governed WSF extension and anchors it with the root concept `wsf:Ecosystem` (Tier 3 worked example, specialisation of `wsf:System`). The ecosystem domain vocabulary surfaced by Moore (1993), Iansiti and Levien (2004), Gawer's research on platforms, Rochet and Tirole's two-sided market theory, and Brandenburger and Nalebuff's coopetition framework includes a coherent set of actor roles that participate in ecosystem dynamics.

The vocabulary distinguishes roles that an entity may assume within an ecosystem. An entity may hold multiple roles simultaneously, and roles are positional rather than fixed: an Orchestrator of one platform may be a Complementor of another, and may be a Competitor of its own Complementors in a different layer. The WSF modelling must capture role overlap without forcing a single-role attribution.

This ADR establishes six Tier 3 specialisations of `wsf:Actor` (one of which is itself a specialisation of another Tier 3 concept) that ground the actor dimension of the ecosystem domain. Each carries full ADR-WSF-20 §14 metadata, parent links to Tier 1 or Tier 3 WSF primitives, and the necessary and sufficient conditions for membership in the role.

## 2. Decision

### 2.1 Tier 1 and Tier 2 rejection (audit trail)

Per Foundational Principle 2 (Minimal Foundation), concepts are admitted to the foundational tier only when their semantics cannot be adequately derived from other WSF primitives without loss of meaning. None of the six actor concepts is irreducible: each composes from `wsf:Entity`, `wsf:Disposition`, `wsf:Relationship`, `wsf:Context`, or some combination thereof, without loss of meaning. Tier 1 placement is therefore rejected for all six.

Per ADR-WSF-20 §12, Tier 2 is reserved for epistemic and identification scaffolding. The actor roles are domain concepts, not scaffolding constructs. Tier 2 placement is rejected for all six.

The full tier-classification matrix is maintained in `wsf-ecosystem/governance/TIER-CLASSIFICATION-MATRIX.md`.

### 2.2 The six actor concepts

#### 2.2.1 `wsf:Orchestrator` (alias: Keystone, Focal Firm)

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Actor`
- **Domain:** Business Ecosystem
- **Definition (short):** The central entity that provides the core platform, sets standards, manages ecosystem health, and shapes the rules of engagement.
- **Definition (long):** An Orchestrator is the actor that provides (or controls) the core platform of an ecosystem, sets the technical and contractual standards that bind actors together, and engages in actions that affect ecosystem-level health (Productivity, Robustness, Niche Creation). The Orchestrator creates shared value rather than merely extracting it; the line between a value-creating Orchestrator and a value-extracting Dominator is behavioural, not categorical, and is captured as a state transition (see §2.2.3).
- **Necessary conditions:**
  1. All `wsf:Actor` necessary conditions (inherited).
  2. **Platform provision.** The actor MUST provide, control, or substantially shape a `wsf:Platform`.
  3. **Standards setting.** The actor MUST set or enforce ecosystem standards (technical, contractual, or normative).
  4. **Ecosystem health engagement.** The actor MUST engage in actions that affect ecosystem-level health.
- **Boundary markers:** Distinguished from a generic `wsf:Actor` by the platform-provision and standards-setting criteria. Distinguished from `wsf:Dominator` by behavioural state (see §2.2.3).
- **Lineage:** Moore (1993); Iansiti and Levien (2004); ADR-CONCEPTS-01 §1.1; VOCAB-000 v2.0 §3.1.2.

#### 2.2.2 `wsf:Complementor` (alias: Niche Player)

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Actor`
- **Domain:** Business Ecosystem
- **Definition (short):** An actor that creates value by adding specialised products, services, or content to the core platform.
- **Definition (long):** A Complementor is an actor whose offerings increase the utility of the core platform to other actors, typically by filling niches the Orchestrator does not serve directly. Complementors depend on the platform yet may compete with the Orchestrator at other layers; this state of simultaneous cooperation and competition is captured by the relational pattern `cooperates_with` and `competes_with` between the same actor pair at different layers (per Rule R2 in `wsf-ecosystem/research/03-relationship-grammar/`).
- **Necessary conditions:**
  1. All `wsf:Actor` necessary conditions (inherited).
  2. **Platform complementarity.** The actor MUST create offerings that increase the platform's value to other actors.
  3. **Independence of offering.** The actor MUST produce offerings not already provided by the Orchestrator.
- **Boundary markers:** Distinguished from `wsf:Orchestrator` by absence of platform-control authority. Distinguished from `wsf:User` by value-creation (rather than value-consumption) activity.
- **Lineage:** Iansiti and Levien (2004); ADR-CONCEPTS-01 §1.1; VOCAB-000 v2.0 §3.1.3.

#### 2.2.3 `wsf:Dominator` (alias: Keystone Competitor)

- **Classification:** Tier 3 (Specialisation, degraded variant)
- **Parent:** `wsf:Orchestrator` (deliberately, not `wsf:Actor`)
- **Domain:** Business Ecosystem
- **Definition (short):** An Orchestrator that has degraded into value-extraction behaviour, capturing disproportionate value and harming long-term ecosystem health.
- **Definition (long):** A Dominator is an Orchestrator that engages in disproportionate value extraction, self-preferencing, scope creep, or excessive fee capture, to the detriment of Complementor viability and the ecosystem's long-term Niche Creation rate. The keystone-to-dominator drift is a behavioural state transition, not a separate taxonomy. The transition from `wsf:Orchestrator` to `wsf:Dominator` is asserted through the lineage-aware relationship grammar with provenance; a Dominator that reforms its behaviour transitions back to Orchestrator.
- **Necessary conditions:**
  1. All `wsf:Orchestrator` necessary conditions (inherited).
  2. **Disproportionate value extraction.** The actor MUST capture a share of value materially exceeding its contribution to ecosystem health.
  3. **Niche stifling.** The actor MUST engage in behaviour that systematically reduces Complementor viability.
- **Boundary markers:** Distinguished from `wsf:Orchestrator` by the value-extraction behavioural state. Distinguished from `wsf:Competitor` (a relational role captured by the `competes_with` predicate, not a class) by being an actor-class with a defined boundary condition.
- **Lineage:** Iansiti and Levien (2004); ADR-CONCEPTS-01 §1.1; VOCAB-000 v2.0 §3.1.4.
- **Modelling decision (applied intelligence):** The Iansiti-Levien framing treats Dominator and Keystone (Orchestrator) as parallel actor types. The WSF modelling deliberately specialises `Dominator ⊂ Orchestrator` (rather than `Dominator ⊂ Actor`) so that the keystone-to-dominator drift is expressible as a state transition with provenance, rather than as a separate taxonomy. The reasoning is recorded in `wsf-ecosystem/research/02-tier-classification/FINDING-Tier-Classification.md` and `wsf-ecosystem/concepts/tier-3/dominator.md`.

#### 2.2.4 `wsf:Gatekeeper` (alias: Curator)

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Actor`
- **Domain:** Governance
- **Definition (short):** The actor responsible for quality control, security, and standards enforcement before a Complementor's offering reaches the end-user.
- **Definition (long):** A Gatekeeper is an actor (human or algorithmic) with delegated authority to admit, reject, or remove offerings on the platform. The Gatekeeper role is typically delegated by the Orchestrator; the Gatekeeper applies quality, security, or compliance criteria to ensure that Complementor offerings meet the platform's standards. Algorithmic Gatekeeping introduces opacity and bias risks that the governance model must address.
- **Necessary conditions:**
  1. All `wsf:Actor` necessary conditions (inherited).
  2. **Standards authority.** The actor MUST have authority to admit, reject, or remove offerings.
  3. **Quality enforcement.** The actor MUST apply quality, security, or compliance criteria.
- **Boundary markers:** Distinguished from `wsf:Orchestrator` by absence of platform-control authority; the Gatekeeper enforces, the Orchestrator sets. Distinguished from `wsf:Trust Mechanisms` (a System) by being an actor-class.
- **Lineage:** Gawer's research on platform governance; ADR-CONCEPTS-01 §1.1; VOCAB-000 v2.0 §3.1.5.

#### 2.2.5 `wsf:Prosumer`

- **Classification:** Tier 3 (Specialisation, hybrid class)
- **Parent:** `wsf:Actor`
- **Domain:** Digital Business Ecosystem
- **Definition (short):** A hybrid actor class representing users who simultaneously produce value, data, or content for the ecosystem.
- **Definition (long):** A Prosumer is an actor that functions as both consumer and producer of value within the same ecosystem. The Prosumer class demonstrates that actor classes are not mutually exclusive: a YouTube creator is a User of the platform and a Producer of content; an Uber driver is a User of the platform infrastructure and a Provider of mobility services. Data-rights and fair value-sharing concerns are acute for Prosumers and require proactive governance.
- **Necessary conditions:**
  1. All `wsf:Actor` necessary conditions (inherited).
  2. **Dual role.** The actor MUST function as both consumer and producer of value within the same ecosystem.
- **Boundary markers:** Distinguished from a single-role User by the dual-role requirement. Distinguished from a Complementor by the absence of independent offerings (Prosumer value is generated through platform-mediated activity, not through standalone products).
- **Lineage:** Toffler (1980); ADR-CONCEPTS-01 §1.1; VOCAB-000 v2.0 §3.1.6.

#### 2.2.6 `wsf:Boundary Spanner`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Actor`
- **Domain:** Governance
- **Definition (short):** An actor responsible for managing interfaces and communication between the ecosystem and external, non-member entities.
- **Definition (long):** A Boundary Spanner is an actor whose role is to translate between ecosystem-internal and ecosystem-external vocabularies and norms, and to manage the ecosystem's interface with regulators, legacy systems, adjacent ecosystems, and other non-member entities. The Boundary Spanner is often under-resourced despite being the ecosystem's primary risk buffer against external shocks.
- **Necessary conditions:**
  1. All `wsf:Actor` necessary conditions (inherited).
  2. **Interface authority.** The actor MUST have authority to engage with external entities on the ecosystem's behalf.
  3. **Boundary management.** The actor MUST translate between ecosystem-internal and ecosystem-external vocabularies and norms.
- **Boundary markers:** Distinguished from a generic `wsf:Actor` by the interface-and-translation function. Distinguished from `wsf:Boundary Resources` (a Platform-provided construct) by being an actor-class.
- **Lineage:** Cross-disciplinary; ADR-CONCEPTS-01 §1.1; VOCAB-000 v2.0 §3.1.7.

### 2.3 Overlapping Roles principle (modelling rule)

The six actor concepts are not mutually exclusive. An entity MAY hold multiple roles simultaneously, and the same actor pair MAY be in different relationships at different layers (cooperating at one layer, competing at another, governed by a Gatekeeper at a third). This is the **Overlapping Roles principle**.

The modelling rules governing this principle are documented in `wsf-ecosystem/research/03-relationship-grammar/` and apply to all actor-role predicates. Specifically:

- **Rule R1:** All actor-role predicates (`orchestrates`, `complements`, `delegates_governance_to`, `provides`) MUST be context-scoped to (platform, layer, time).
- **Rule R2:** Coopetition is modelled as the co-existence of `cooperates_with` and `competes_with` between the same actor pair, scoped per layer.

The principle is not optional. Every actor-role assertion in the Ecosystem domain carries a context triple.

### 2.4 Namespace and serialisation

The six actor concepts use the standard `wsf:` namespace prefix for classes (per ADR-WSF-29 §2.4). No additional namespace reservation is introduced by this ADR.

Serialisation in `wsf-spec/` (Turtle, JSON Schema, Protobuf, OpenAPI) is authorised through the downstream CR (Issue #4 in `wsf-ecosystem`, gated on this ADR reaching Baseline). The CR implements the registration; this ADR authorises it conceptually.

## 3. Why this ADR is necessary

The actor taxonomy is the entry point for the Ecosystem domain vocabulary. Without this ADR:

1. The six actor concepts have no authoritative home in WSF. They appear in `wsf-ecosystem/concepts/tier-3/` as concept files at status Candidate, but Candidate concepts are not authoritative.
2. The keystone-to-dominator drift, which is the most consequential behavioural state in the ecosystem literature, has no formal modelling pattern.
3. The Overlapping Roles principle is documented in the relationship grammar but not authorised as a governance rule.
4. Downstream ADRs (ADR-WSF-31 Value Dynamics, ADR-WSF-32 Structural Primitives, ADR-WSF-33 Lifecycle and Health) cannot reach Baseline without this ADR, because each depends on the actor concepts to ground relational predicates.
5. The CR for `wsf-spec/` registration (Issue #4) cannot proceed without this ADR, because the actor concepts are inputs to the registration.

## 4. Consequences

### 4.1 Positive

- The Ecosystem domain vocabulary gains an authoritative actor dimension.
- The keystone-to-dominator drift is expressible as a state transition with provenance, supporting health analytics and governance intervention.
- The Overlapping Roles principle is formally adopted.
- Downstream ADRs (31, 32, 33) gain their parent.
- Federation with external ontologies (Schema.org, SKOS, TM Forum) gains a coherent actor mapping, subject to ADR-WSF-25's federation pattern.

### 4.2 Cost

- Six concepts require registration in `wsf-spec/` (Turtle, JSON Schema, Protobuf, OpenAPI).
- SHACL shapes must be authored for the six concepts and for the actor-role predicates.
- The keystone-to-dominator state transition requires an inference rule in the Semantic Engine, per CR-WSF-17 Rev.1 §17 (Simulation pattern).
- Conformance tests are required in `wsf-software/tests/` for the actor taxonomy.
- The Overlapping Roles principle requires reviewers to evaluate every actor-role assertion for context-scope compliance.

These costs are accepted consequences of admitting the Ecosystem domain as a foundation extension.

### 4.3 Implementation gate

This ADR authorises the dependent ADRs (ADR-WSF-31, ADR-WSF-32, ADR-WSF-33) and the downstream CR (Issue #4 in `wsf-ecosystem`, formalised as `CR-WSF-30-Rev.1` per the ADR-WSF-29 sub-numbering convention). Each is filed separately and proceeds through the Change Control Lifecycle independently.

The transition of this ADR to Baseline is contingent on the transition of ADR-WSF-28 to Baseline. Until that condition is satisfied, this ADR remains at status **Proposed (Pre-Baseline)** and is not citable as authoritative.

## 5. Alternatives rejected

### A. Parallel keystone/dominator taxonomy (Iansiti-Levien framing)

Rejected. The Iansiti-Levien framing treats Dominator and Keystone (Orchestrator) as parallel actor types. The WSF modelling deliberately specialises `Dominator ⊂ Orchestrator` so that the keystone-to-dominator drift is expressible as a state transition with provenance. The parallel taxonomy would lose the drift transition.

### B. Tier 1 placement for actor concepts

Rejected. Each actor concept composes from Tier 1 primitives without loss of meaning. Tier 1 placement violates Foundational Principle 2 (Minimal Foundation).

### C. Tier 2 placement for actor concepts

Rejected. Tier 2 is reserved for epistemic and identification scaffolding. Actor concepts are domain concepts, not scaffolding constructs.

### D. Defer the actor taxonomy to a later ADR

Rejected. The actor taxonomy is required by ADR-WSF-31 (Value Dynamics), ADR-WSF-32 (Structural Primitives), and ADR-WSF-33 (Lifecycle and Health). Deferring blocks all three downstream ADRs.

### E. Fold the Prosumer class into the User class

Rejected. The Prosumer class demonstrates that actor classes are not mutually exclusive. Folding the Prosumer into the User class loses the dual-role signal that is the Prosumer's defining characteristic.

### F. Fold the Boundary Spanner class into the Orchestrator class

Rejected. The Boundary Spanner role is distinct from the Orchestrator role (interface management vs. platform control). Folding loses the governance separation.

## 6. Decision summary

The decision can be reduced to one sentence.

> Six Tier 3 specialisations of `wsf:Actor` (Orchestrator, Complementor, Gatekeeper, Prosumer, Boundary Spanner) and one Tier 3 specialisation of `wsf:Orchestrator` (Dominator as degraded variant) are established as the Ecosystem domain actor taxonomy, with the Overlapping Roles principle formally adopted as a modelling rule.

This ADR is filed as a Draft PR. Its transition to Baseline is contingent on ADR-WSF-28 reaching Baseline.

## 7. Required follow-on actions

The following actions are required at the next revision cycle. They are not part of this ADR's acceptance gate but are tracked as separate work items.

1. File ADR-WSF-31 (Ecosystem Value Dynamics) as a Draft PR, dependent on this ADR.
2. File ADR-WSF-32 (Ecosystem Structural Primitives) as a Draft PR, dependent on this ADR.
3. File ADR-WSF-33 (Ecosystem Lifecycle and Health Metrics) as a Draft PR, dependent on this ADR and ADR-WSF-31.
4. Author the keystone-to-dominator state transition as an inference rule, per CR-WSF-17 Rev.1 §17.
5. Mirror the actor concept files from `wsf-ecosystem/concepts/tier-3/` to `wsf-examples/` for cross-repo consistency.

## 8. References

- ADR-WSF-04 (Semantic Inheritance): the specialisation rules applied throughout this ADR.
- ADR-WSF-09 (Foundational Concept Taxonomy): the tier-classification framework.
- ADR-WSF-17 (Foundational Semantic Architecture): the tier discipline and the worked-example pattern.
- ADR-WSF-20 (Concept Definition Model): the §14 metadata schema used for each concept.
- ADR-WSF-28 (Ecosystem as Tier 3 Worked Example): the parent of this ADR.
- ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention): the CR sub-numbering convention used in §4.3.
- VOCAB-000 v2.0 §3.1: the source vocabulary for the six actor concepts.
- ADR-CONCEPTS-01 §1.1: the source concept catalogue for the actor taxonomy.
- Moore, J. F. (1993), "Predators and Prey: A New Ecology of Competition," *Harvard Business Review*.
- Iansiti, M., and Levien, R. (2004), *The Keystone Advantage*.
- Brandenburger, A., and Nalebuff, B., *Co-opetition*.

### Source artifacts in `wsf-ecosystem`

- `concepts/tier-3/orchestrator.md`, `complementor.md`, `dominator.md`, `gatekeeper.md`, `prosumer.md`, `boundary-spanner.md`.
- `research/01-source-reconciliation/FINDING-Source-Reconciliation.md`: the source-to-concept lineage.
- `research/02-tier-classification/FINDING-Tier-Classification.md`: the tier-classification rationale.
- `research/03-relationship-grammar/FINDING-Relationship-Grammar.md`: the modelling rules including the Overlapping Roles principle.
- `governance/TIER-CLASSIFICATION-MATRIX.md`: the per-concept tier matrix.

---

*This ADR establishes the Ecosystem domain actor taxonomy. It reached Baseline on 2026-09-13 via PR #4 (parent ADR-WSF-28 was Baseline at that point).*
