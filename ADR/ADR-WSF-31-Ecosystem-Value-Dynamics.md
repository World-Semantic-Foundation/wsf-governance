# ADR-WSF-31: Ecosystem Value Dynamics

> **Status:** Proposed (Pre-Baseline)
> **Decision Type:** Domain Extension (value-dynamics specialisation)
> **Scope:** Ecosystem domain value dynamics, network effects, value flow, exit friction
> **Supersedes:** None
> **Depends On:** ADR-WSF-28, ADR-WSF-30, ADR-WSF-20, ADR-WSF-04, ADR-WSF-09
> **Related:** ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention)
> **Paired submission:** This ADR is filed in a Draft PR. Its parents (ADR-WSF-28 and ADR-WSF-30) are at status Proposed in PR #1 and PR #2 respectively. The transition of this ADR to Baseline is contingent on both parents reaching Baseline.

---

## 0. Pre-Baseline caveat

This ADR is filed as a Draft PR. Its parent decisions are:

| Parent | Status | Location |
|---|---|---|
| ADR-WSF-28 (Ecosystem as Tier 3 Worked Example) | Proposed | `wsf-governance` PR #1 |
| ADR-WSF-30 (Ecosystem Actor Taxonomy) | Proposed (Pre-Baseline) | `wsf-governance` PR #2 |

Per the Semantic Status Model and ADR-WSF-17, an ADR reaches Baseline only after governance review. Until both parents reach Baseline, this ADR is grounded in non-ratified parents.

The convention established by ADR-WSF-29 permits this filing pattern. This ADR:

1. Cites both parents as **Proposed (Pre-Baseline)**, not as ratified.
2. Is filed as a **Draft PR**.
3. Documents, in §1 Context, the precise conditions under which this ADR transitions to Baseline.
4. Will be re-evaluated for revision if either parent's review surfaces changes that affect the value-dynamics vocabulary.

## 1. Context

ADR-WSF-28 establishes the Ecosystem domain as a governed WSF extension. ADR-WSF-30 establishes six Tier 3 actor concepts (Orchestrator, Complementor, Dominator, Gatekeeper, Prosumer, Boundary Spanner) and the Overlapping Roles principle. The value-dynamics vocabulary captures how value is created, exchanged, captured, lost, and locked within ecosystems.

The vocabulary surfaced by the source literature splits naturally into three layers:

1. **Phenomena:** Network Effects (with Direct and Indirect subtypes), Value Co-creation, Value Exchange, Value Slippage, Switching Costs, Lock-In.
2. **Compositional structure:** Network Effects are emergent properties of the actor network, not attributes of any single actor. Lock-In is an emergent state produced by switching costs combined with network effects. Value Slippage is an occurrence by which value escapes capture.
3. **Modelling rules:** The relational property `exhibits` attaches Network Effects to the actor network (not to a single actor). The composition of switching costs + network effects → Lock-In is captured as a derived state in the inference engine, per CR-WSF-17 Rev.1 §17.

This ADR establishes eight Tier 3 specialisations across the value-dynamics domain. Seven parented to Tier 1 primitives; one (Network Effect) parented to `wsf:Disposition` and further specialised into Direct and Indirect subtypes. Two modelling decisions are documented as applied intelligence: Network Effect as `Disposition` of the actor network (not as actor attribute), and Lock-In as emergent state (not as mechanism).

## 2. Decision

### 2.1 Tier 1 and Tier 2 rejection (audit trail)

Per Foundational Principle 2 (Minimal Foundation), concepts are admitted to the foundational tier only when their semantics cannot be adequately derived from other WSF primitives without loss of meaning. None of the eight value-dynamics concepts is irreducible: each composes from Tier 1 primitives without loss of meaning. Tier 1 placement is rejected for all eight.

Per ADR-WSF-20 §12, Tier 2 is reserved for epistemic and identification scaffolding. The value-dynamics concepts are domain phenomena, not scaffolding constructs. Tier 2 placement is rejected for all eight.

The full tier-classification matrix is maintained in `wsf-ecosystem/governance/TIER-CLASSIFICATION-MATRIX.md`.

### 2.2 The eight concepts

#### 2.2.1 `wsf:Network Effect`

- **Classification:** Tier 3 (Specialisation, disposition)
- **Parent:** `wsf:Disposition`
- **Subtypes:** `wsf:Direct Network Effect`, `wsf:Indirect Network Effect` (§2.2.2, §2.2.3)
- **Domain:** Value Dynamics
- **Definition (short):** The phenomenon where a product or service gains additional value as more actors use it, modelled as an emergent property of the relationships between actor classes.
- **Definition (long):** A Network Effect is a disposition of the actor network (Platform + Complementors + Users + their interrelationships) such that the value the network provides to each participant depends on the number and composition of the other participants. Network Effects are emergent properties of the network, not attributes of any single actor or firm.
- **Necessary conditions:**
  1. All `wsf:Disposition` necessary conditions (inherited).
  2. **Multi-actor dependency.** Value MUST depend on the number and composition of actors participating.
  3. **Relational grounding.** MUST be a property of the actor network, not of any single actor.
- **Boundary markers:** Distinguished from `wsf:Value Co-creation` (a proposition about value generation) by being a disposition (a tendency, not a claim). Distinguished from `wsf:Switching Costs` by being value-increasing with participation, not exit-friction-increasing.
- **Lineage:** Rochet and Tirole (two-sided market theory); Katz and Shapiro (1985); ADR-CONCEPTS-01 §3; VOCAB-000 v2.0 §3.3.1.
- **Modelling decision (applied intelligence):** Network Effects are modelled as a `Disposition` of the actor network, not as an attribute of any single firm. The relational property `exhibits` attaches the effect to the network (or to the Platform-as-relationship). See Rule R3 in `wsf-ecosystem/research/03-relationship-grammar/`.

#### 2.2.2 `wsf:Direct Network Effect` (alias: Same-Side Network Effect)

- **Classification:** Tier 3 (Specialisation, subtype)
- **Parent:** `wsf:Network Effect`
- **Domain:** Value Dynamics
- **Definition (short):** A subtype of Network Effect in which value grows as users of the same type join.
- **Definition (long):** A Direct Network Effect exists when each additional user of type X increases the value of the network to existing users of type X. The canonical example is the telephone network: more users on the telephone network makes the telephone more valuable to each user.
- **Necessary conditions:**
  1. All `wsf:Network Effect` necessary conditions (inherited).
  2. **Same-type dependency.** Value growth MUST depend on additional users of the same actor type.
- **Boundary markers:** Distinguished from `wsf:Indirect Network Effect` by same-type vs. different-type dependency.
- **Lineage:** Katz and Shapiro (1985); ADR-CONCEPTS-01 §3.1; VOCAB-000 v2.0 §3.3.1 (subtypes).

#### 2.2.3 `wsf:Indirect Network Effect` (alias: Cross-Side Network Effect)

- **Classification:** Tier 3 (Specialisation, subtype)
- **Parent:** `wsf:Network Effect`
- **Domain:** Value Dynamics
- **Definition (short):** A subtype of Network Effect in which value grows as users of different types join.
- **Definition (long):** An Indirect Network Effect exists when each additional user of type Y increases the value of the network to existing users of type X (and vice versa). The canonical example is the App Store: more developers attract more users, and more users attract more developers. Cross-side effects require balancing both sides: a classic cold-start problem.
- **Necessary conditions:**
  1. All `wsf:Network Effect` necessary conditions (inherited).
  2. **Cross-type dependency.** Value growth MUST depend on additional users of a different actor type.
- **Boundary markers:** Distinguished from `wsf:Direct Network Effect` by cross-type vs. same-type dependency. Indirect effects MAY be negative (congestion, dilution).
- **Lineage:** Rochet and Tirole (2003); Parker and Van Alstyne (2005); ADR-CONCEPTS-01 §3.1; VOCAB-000 v2.0 §3.3.1 (subtypes).

#### 2.2.4 `wsf:Value Co-creation`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Proposition`
- **Domain:** Value Dynamics
- **Definition (short):** The proposition that value is generated jointly by multiple actors through a platform, not produced upstream and passed downstream.
- **Definition (long):** Value Co-creation is the multi-actor, generative counterpart to transactional Value Exchange. It captures the proposition that the value produced within an ecosystem is created through the joint activity of the Orchestrator, Complementors, and Users (including Prosumers), rather than produced by the Orchestrator alone and transmitted to Consumers.
- **Necessary conditions:**
  1. All `wsf:Proposition` necessary conditions (inherited).
  2. **Multi-actor generation.** Value MUST be generated through the joint activity of two or more actor classes.
  3. **Platform mediation.** The joint activity MUST occur through a platform or shared substrate.
- **Boundary markers:** Distinguished from `wsf:Value Exchange` (a bilateral flow) by being a multi-actor proposition about value generation. Distinguished from `wsf:Network Effect` (a disposition) by being a claim about value creation.
- **Lineage:** Prahalad and Ramaswamy (2004); Vargo and Lusch (2004); ADR-CONCEPTS-01 §3.2; VOCAB-000 v2.0 §3.3.2.

#### 2.2.5 `wsf:Value Exchange`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Relationship`
- **Domain:** Value Dynamics
- **Definition (short):** The transfer of tangible or intangible value between actors, the fundamental edge of the ecosystem graph.
- **Definition (long):** Value Exchange is a bilateral relationship between two actors through which tangible value (money, goods, services) or intangible value (data, attention, reputation) flows. Value Exchange is the fundamental edge of the ecosystem graph: every edge in an ecosystem representation carries a Value Exchange assertion.
- **Necessary conditions:**
  1. All `wsf:Relationship` necessary conditions (inherited).
  2. **Bilateral flow.** Value MUST flow in both directions (even if asymmetrically).
  3. **Assertability.** The exchange MUST be assertable as a WSF Assertion.
- **Boundary markers:** Distinguished from `wsf:Value Co-creation` by being bilateral (two actors) rather than multi-actor. Distinguished from `wsf:Value Slippage` by being an asserted exchange rather than a leakage occurrence.
- **Lineage:** ADR-CONCEPTS-01 §3 (implicit); VOCAB-000 v2.0 §3.3.3.

#### 2.2.6 `wsf:Value Slippage`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Event`
- **Domain:** Value Dynamics
- **Definition (short):** The occurrence by which value generated within an ecosystem escapes capture by ecosystem participants.
- **Definition (long):** Value Slippage is the occurrence of value leakage: the portion of generated value that escapes capture by Orchestrator, Complementors, and Users, flowing instead to competitors, free-riders, or legacy intermediaries. Value Slippage is the inverse lens on capture: a healthy-looking ecosystem can fail to monetise because of slippage.
- **Necessary conditions:**
  1. All `wsf:Event` necessary conditions (inherited).
  2. **Generated value.** The value slipping MUST have been generated within the ecosystem (not external value).
  3. **Escape from capture.** The value MUST flow to an actor outside the capturing set.
- **Boundary markers:** Distinguished from `wsf:Value Exchange` (an asserted bilateral flow) by being an unasserted leakage. Distinguished from `wsf:Dominator behaviour` (an actor-level pattern) by being an event-level phenomenon.
- **Lineage:** ADR-CONCEPTS-01 §3.2; VOCAB-000 v2.0 §3.3.4.

#### 2.2.7 `wsf:Switching Costs`

- **Classification:** Tier 3 (Specialisation, disposition)
- **Parent:** `wsf:Disposition`
- **Domain:** Value Dynamics
- **Definition (short):** The friction an actor faces when leaving the ecosystem, a primary defensibility mechanism.
- **Definition (long):** Switching Costs is the disposition of an actor-ecosystem relationship such that exiting the ecosystem carries a cost (financial, technical, psychological, social). Switching Costs are a primary mechanism of defensibility, but regulators increasingly scrutinise artificial switching costs.
- **Necessary conditions:**
  1. All `wsf:Disposition` necessary conditions (inherited).
  2. **Exit friction.** The actor MUST face material cost on exit.
  3. **Asymmetry.** The cost MUST be materially greater than zero (otherwise the actor is unmoved).
- **Boundary markers:** Distinguished from `wsf:Lock-In` (an emergent state) by being a disposition (a tendency), not a state. Distinguished from `wsf:Network Effect` by being exit-friction-increasing, not value-increasing.
- **Lineage:** Farrell and Saloner (1985); Klemperer (1987); ADR-CONCEPTS-01 §3.2; VOCAB-000 v2.0 §3.3.5.

#### 2.2.8 `wsf:Lock-In`

- **Classification:** Tier 3 (Specialisation, state)
- **Parent:** `wsf:State`
- **Domain:** Value Dynamics
- **Definition (short):** The emergent state resulting from high switching costs combined with strong network effects, creating high barriers to exit.
- **Definition (long):** Lock-In is the emergent state produced by the composition of two independent dynamics: high Switching Costs and strong Network Effects. Lock-In protects incumbents but breeds complacency and invites disruption at the Self-Renewal or Death lifecycle bifurcation. Lock-In is double-edged.
- **Necessary conditions:**
  1. All `wsf:State` necessary conditions (inherited).
  2. **Switching cost presence.** High Switching Costs MUST be present.
  3. **Network effect presence.** Strong Network Effects MUST be present.
- **Boundary markers:** Distinguished from `wsf:Switching Costs` (a disposition) by being a state (an emergent condition). Distinguished from `wsf:Network Effect` (a disposition) by being a state composed of two dynamics.
- **Lineage:** ADR-CONCEPTS-01 §3.2; VOCAB-000 v2.0 §3.3.6.
- **Modelling decision (applied intelligence):** Lock-In is modelled as an emergent state produced by the composition of Switching Costs and Network Effects, not as a mechanism in its own right. The composition is captured as a derived state in the Semantic Engine, per CR-WSF-17 Rev.1 §17 (Simulation pattern). The reasoning is in `wsf-ecosystem/research/02-tier-classification/FINDING-Tier-Classification.md` and `wsf-ecosystem/concepts/tier-3/lock-in.md`.

### 2.3 Relational properties for value dynamics

The relational properties that connect actor concepts to value-dynamics concepts are documented in `wsf-ecosystem/research/03-relationship-grammar/` and are summarised here for context. Their formal registration in `wsf-spec/` is gated on the downstream CR (Issue #4 in `wsf-ecosystem`, formalised as `CR-WSF-31-Rev.1` per ADR-WSF-29 sub-numbering).

| Predicate | Domain | Range | Symmetric | Notes |
|---|---|---|---|---|
| `wsf-rel-eco:exhibits` | `wsf:Platform` (or actor network) | `wsf:Network Effect` (with subtype) | false | Per Rule R3, the effect attaches to the network, not to a single actor. |
| `wsf-rel-eco:exchanges_value_with` | `wsf:Actor` | `wsf:Actor` | true | Bilateral value flow. |
| `wsf-rel-eco:co_creates_value_through` | `wsf:Actor` set | `wsf:Platform` | false | Multi-actor value generation. |
| `wsf-rel-eco:captures_value_from` | `wsf:Actor` (typically Orchestrator) | `wsf:Value Exchange` | false | Value capture from a flow. |
| `wsf-rel-eco:slips_value_to` | `wsf:Actor` (or ecosystem) | `wsf:Actor` (external) | false | Value leakage to a non-member. |
| `wsf-rel-eco:is_in_state_of` | `wsf:Actor` (or relationship) | `wsf:Lock-In` | false | Asserting lock-in for an actor or relationship. |

The modelling rules (R1 through R6) governing these predicates are documented in `wsf-ecosystem/research/03-relationship-grammar/FINDING-Relationship-Grammar.md`. The composition rule `High Switching Costs ∧ Strong Network Effects ⊢ Lock-In` is a derived state, not a stored predicate.

### 2.4 Namespace and serialisation

The eight value-dynamics concepts use the standard `wsf:` namespace prefix for classes. The relational properties use the `wsf-rel-eco:` namespace prefix reserved by ADR-WSF-28 §2.4. No additional namespace reservation is introduced by this ADR.

Serialisation in `wsf-spec/` (Turtle, JSON Schema, Protobuf, OpenAPI) is authorised through the downstream CR (Issue #4 in `wsf-ecosystem`, gated on this ADR reaching Baseline).

## 3. Why this ADR is necessary

The value-dynamics vocabulary is the analytical core of the Ecosystem domain. Without this ADR:

1. Network Effects have no authoritative modelling pattern. The economics literature treats them as actor attributes; WSF treats them as relational dispositions.
2. Lock-In has no formal composition rule. Without the rule, lock-in is asserted but not derived.
3. Value Co-creation and Value Exchange are conflated. The transactional vs. generative distinction is lost.
4. Value Slippage is absent from the vocabulary. The failure mode of healthy-looking ecosystems that fail to monetise is unmodelled.
5. Downstream ADRs (ADR-WSF-33 Lifecycle and Health) cannot fully ground their health metrics (Productivity, Robustness, Niche Creation) without the value-dynamics vocabulary.

## 4. Consequences

### 4.1 Positive

- The Ecosystem domain gains an authoritative value-dynamics dimension.
- Network Effects are modelled correctly as relational properties, supporting federation with external ontologies (Rochet-Tirole framework).
- Lock-In is expressible as a derived state, supporting analytics and governance intervention.
- The composition rule is captured in the Semantic Engine's inference layer, not asserted manually.
- Downstream ADRs (ADR-WSF-33) gain their value-dynamics parent.

### 4.2 Cost

- Eight concepts require registration in `wsf-spec/`.
- SHACL shapes must be authored for the eight concepts and for the value-dynamics predicates.
- The Lock-In composition rule requires an inference rule in the Semantic Engine, per CR-WSF-17 Rev.1 §17.
- Conformance tests are required for the value-dynamics vocabulary.
- Six relational properties require their own serialisation (Turtle, JSON Schema, Protobuf, OpenAPI).

These costs are accepted consequences of admitting the Ecosystem domain as a foundation extension.

### 4.3 Implementation gate

This ADR authorises the dependent ADR (ADR-WSF-33) and the downstream CR (Issue #4 in `wsf-ecosystem`, formalised as `CR-WSF-31-Rev.1` per the ADR-WSF-29 sub-numbering convention). The transition of this ADR to Baseline is contingent on the transition of both ADR-WSF-28 and ADR-WSF-30 to Baseline.

## 5. Alternatives rejected

### A. Network Effect as Tier 1

Rejected. Network Effects compose from Tier 1 primitives (`wsf:Entity`, `wsf:Disposition`, `wsf:Relationship`, `wsf:Context`) without loss of meaning. Tier 1 placement violates Foundational Principle 2.

### B. Network Effect as an attribute of a single actor or firm

Rejected. The economics literature often treats network effects as a property of platforms or firms. WSF treats them as emergent properties of the actor network. The relational property `exhibits` attaches the effect to the network, not to any actor. Per Rule R3 in `wsf-ecosystem/research/03-relationship-grammar/`.

### C. Lock-In as a mechanism

Rejected. Lock-In is the emergent state produced by the composition of Switching Costs and Network Effects, not a mechanism in its own right. Modelling Lock-In as a mechanism loses the compositional structure.

### D. Fold Value Co-creation into Value Exchange

Rejected. Value Exchange is bilateral (a flow between two actors); Value Co-creation is multi-actor (a proposition about joint value generation). The transactional vs. generative distinction is lost if the two are conflated.

### E. Value Slippage as a quality of Value Exchange

Rejected. Value Slippage is an occurrence (an event), not a property of an exchange. Modelling it as a quality conflates the level of analysis.

### F. Tier 1 placement for any value-dynamics concept

Rejected. All eight concepts compose from Tier 1 primitives without loss of meaning.

### G. Defer the value-dynamics vocabulary to a later ADR

Rejected. The value-dynamics vocabulary is required by ADR-WSF-33 (Lifecycle and Health). Deferring blocks ADR-WSF-33.

## 6. Decision summary

The decision can be reduced to one sentence.

> Eight Tier 3 specialisations of Tier 1 primitives (Network Effect and subtypes parented to `wsf:Disposition`; Value Co-creation parented to `wsf:Proposition`; Value Exchange parented to `wsf:Relationship`; Value Slippage parented to `wsf:Event`; Switching Costs parented to `wsf:Disposition`; Lock-In parented to `wsf:State`) are established as the Ecosystem domain value-dynamics vocabulary, with Network Effects modelled as relational dispositions and Lock-In as a derived state.

This ADR is filed as a Draft PR. Its transition to Baseline is contingent on both ADR-WSF-28 and ADR-WSF-30 reaching Baseline.

## 7. Required follow-on actions

The following actions are required at the next revision cycle. They are not part of this ADR's acceptance gate but are tracked as separate work items.

1. File ADR-WSF-33 (Ecosystem Lifecycle and Health Metrics) as a Draft PR, dependent on this ADR and ADR-WSF-30.
2. Author the Lock-In composition rule as a Semantic Engine inference rule.
3. Author SHACL shapes for the eight concepts and the value-dynamics predicates.
4. Mirror the value-dynamics concept files from `wsf-ecosystem/concepts/tier-3/` to `wsf-examples/` for cross-repo consistency.

## 8. References

- ADR-WSF-04 (Semantic Inheritance): the specialisation rules applied throughout this ADR.
- ADR-WSF-09 (Foundational Concept Taxonomy): the tier-classification framework.
- ADR-WSF-17 (Foundational Semantic Architecture): the tier discipline.
- ADR-WSF-19 (Semantic Relationship Model): the metadata schema for the relational properties.
- ADR-WSF-20 (Concept Definition Model): the §14 metadata schema used for each concept.
- ADR-WSF-28 (Ecosystem as Tier 3 Worked Example): the root parent of this ADR.
- ADR-WSF-30 (Ecosystem Actor Taxonomy): the immediate parent of this ADR.
- ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention): the CR sub-numbering convention used in §4.3.
- VOCAB-000 v2.0 §3.3: the source vocabulary for the value-dynamics concepts.
- ADR-CONCEPTS-01 §3: the source concept catalogue for value dynamics.
- Katz, M., and Shapiro, C. (1985), "Network Externalities, Competition, and Compatibility," *American Economic Review*.
- Rochet, J. C., and Tirole, J. (2003), "Platform Competition in Two-Sided Markets," *Journal of the European Economic Association*.
- Parker, G., and Van Alstyne, M. (2005), "Two-Sided Network Effects: A Theory of Information Product Design," *Management Science*.
- Prahalad, C. K., and Ramaswamy, V. (2004), "Co-Creation Experiences: The Next Practice in Value Creation," *Journal of Interactive Marketing*.
- Vargo, S. L., and Lusch, R. F. (2004), "Evolving to a New Dominant Logic for Marketing," *Journal of Marketing*.
- Farrell, J., and Saloner, G. (1985), "Standardization, Compatibility, and Innovation," *RAND Journal of Economics*.
- Klemperer, P. (1987), "The Competitiveness of Markets with Switching Costs," *RAND Journal of Economics*.

### Source artifacts in `wsf-ecosystem`

- `concepts/tier-3/network-effect.md`, `direct-network-effect.md`, `indirect-network-effect.md`, `value-co-creation.md`, `value-exchange.md`, `value-slippage.md`, `switching-costs.md`, `lock-in.md`.
- `research/01-source-reconciliation/FINDING-Source-Reconciliation.md`: the source-to-concept lineage.
- `research/02-tier-classification/FINDING-Tier-Classification.md`: the tier-classification rationale, including the rejection of Network Effect as Tier 1 and the Lock-In composition rationale.
- `research/03-relationship-grammar/FINDING-Relationship-Grammar.md`: the relational-property metadata and the modelling rules including Rule R3 (Network Effects as relational dispositions).
- `governance/TIER-CLASSIFICATION-MATRIX.md`: the per-concept tier matrix.

---

*This ADR establishes the Ecosystem domain value-dynamics vocabulary. Its transition to Baseline is contingent on ADR-WSF-28 and ADR-WSF-30 reaching Baseline.*
