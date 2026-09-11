# ADR-WSF-33: Ecosystem Lifecycle and Health Metrics

> **Status:** Proposed (Pre-Baseline)
> **Decision Type:** Domain Extension (lifecycle and health specialisation)
> **Scope:** Ecosystem domain lifecycle stages, health metrics, derived states
> **Supersedes:** None
> **Depends On:** ADR-WSF-28, ADR-WSF-30, ADR-WSF-31, ADR-WSF-32, ADR-WSF-20, ADR-WSF-04, ADR-WSF-09, ADR-WSF-17
> **Related:** ADR-WSF-29 (Domain-Extension Numbering and Categorisation Convention)
> **Paired submission:** This ADR is filed in a Draft PR. Its parents (ADR-WSF-30 and ADR-WSF-31) are at status Proposed in PR #4 and PR #5 respectively. ADR-WSF-32 (also a parent) is at status Proposed in PR #6. The transition of this ADR to Baseline is contingent on ADR-WSF-30 and ADR-WSF-31 reaching Baseline. ADR-WSF-32 is a structural grounding parent and is required for the health-metrics vocabulary to be applicable.

---

## 0. Pre-Baseline caveat

This ADR is filed as a Draft PR. Its parent decisions are:

| Parent | Status | Location |
|---|---|---|
| ADR-WSF-28 (Ecosystem as Tier 3 Worked Example) | Baseline | merged via PR #1 |
| ADR-WSF-30 (Ecosystem Actor Taxonomy) | Proposed | PR #4 (ready for review) |
| ADR-WSF-31 (Ecosystem Value Dynamics) | Proposed | PR #5 (Draft, Pre-Baseline) |
| ADR-WSF-32 (Ecosystem Structural Primitives) | Proposed | PR #6 (Draft, Pre-Baseline) |

The natural-language dependency chain is:

```
ADR-WSF-28 (Ecosystem as Tier 3 Worked Example, parent)
    |
    +-- ADR-WSF-30 (Actor Taxonomy, dimension)   <-- parent of ADR-WSF-33
    |       |
    |       +-- ADR-WSF-32 (Structural Primitives, dimension) <-- parent of ADR-WSF-33
    |
    +-- ADR-WSF-31 (Value Dynamics, dimension)   <-- parent of ADR-WSF-33
            |
            +-- ADR-WSF-33 (Lifecycle and Health, derived)   <-- THIS ADR
```

Per the Semantic Status Model and ADR-WSF-17, an ADR reaches Baseline only after governance review. Until its parents reach Baseline, this ADR is grounded in non-ratified parents.

The convention established by ADR-WSF-29 permits this filing pattern. This ADR:

1. Cites all parents as **Proposed** or **Baseline**, with ADR-WSF-30, -31, -32 still pre-ratification.
2. Is filed as a **Draft PR**.
3. Documents, in §1 Context, the precise conditions under which this ADR transitions to Baseline.
4. Will be re-evaluated for revision if any parent's review surfaces changes that affect the lifecycle or health vocabulary.

## 1. Context

ADR-WSF-28 establishes the Ecosystem domain as a governed WSF extension. ADR-WSF-30, -31, -32 establish the actor taxonomy, value dynamics, and structural primitives. This ADR completes the Ecosystem domain by establishing:

1. The lifecycle vocabulary: four canonical lifecycle stages and the events that transition between them.
2. The health-metrics vocabulary: four canonical health indicators and the dispositions they measure.
3. The lifecycle state space: a phase diagram mapping health quadrants to lifecycle transitions.

The lifecycle and health vocabulary is grounded in the Iansiti-Levien framework (2004) and refined through the lens of the WSF tier discipline. The substantive modelling departures from the upstream sources are documented in §5 (alternatives rejected) and §2 (applied intelligence).

## 2. Decision

### 2.1 Tier 1 and Tier 2 rejection (audit trail)

Per Foundational Principle 2 (Minimal Foundation), concepts are admitted to the foundational tier only when their semantics cannot be adequately derived from other WSF primitives without loss of meaning. None of the lifecycle stages or health metrics is irreducible: each composes from Tier 1 primitives without loss of meaning. Tier 1 placement is rejected for all.

Per ADR-WSF-20 §12, Tier 2 is reserved for epistemic and identification scaffolding. The lifecycle and health concepts are domain concepts, not scaffolding constructs. Tier 2 placement is rejected for all.

The full tier-classification matrix is maintained in `wsf-ecosystem/governance/TIER-CLASSIFICATION-MATRIX.md`.

### 2.2 The lifecycle vocabulary

#### 2.2.1 `wsf:Ecosystem Lifecycle Stages`

- **Classification:** Tier 3 (Specialisation, abstract collection)
- **Parent:** `wsf:Disposition`
- **Domain:** Lifecycle
- **Definition (short):** The canonical four-stage progression that characterises an ecosystem's maturation from inception to renewal or dissolution.
- **Definition (long):** The Ecosystem Lifecycle Stages are the canonical four-stage progression that characterises an ecosystem's maturation. The four stages are: Birth, Expansion, Leadership, and Self-Renewal or Death. Each stage has distinguishing observable characteristics and transition conditions. The lifecycle is not strictly linear: ecosystems may oscillate between stages, skip stages under specific conditions, or fail to transition at all (death).
- **Necessary conditions:**
  1. All `wsf:Disposition` necessary conditions (inherited).
  2. **Canonical progression.** MUST be characterised by Birth, Expansion, Leadership, Self-Renewal or Death.
- **Boundary markers:** Distinguished from `wsf:Ecosystem Health` (a four-axis measurement vocabulary) by being a stage progression rather than a measurement. Distinguished from `wsf:Ecosystem Health Indicator` (individual metrics) by being the disposition that organises them.

#### 2.2.2 `wsf:Ecosystem Birth`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Ecosystem Lifecycle Stages` (or directly `wsf:State`)
- **Domain:** Lifecycle
- **Definition (short):** The initial stage of an ecosystem, characterised by uncertainty, platform formation, and complementor recruitment.
- **Definition (long):** Ecosystem Birth is the initial stage where the platform is being constructed, the initial complementor set is being recruited, and the value proposition is unproven. The transition condition to Expansion is sustained complementor activity and initial value capture.
- **Necessary conditions:**
  1. All lifecycle-stage necessary conditions (inherited).
  2. **Platform formation.** A `wsf:Platform` MUST be in construction or early operation.
  3. **Complementor recruitment.** Initial complementor activity MUST be observable.
- **Boundary markers:** Distinguished from `wsf:Ecosystem Expansion` by the absence of validated value capture.

#### 2.2.3 `wsf:Ecosystem Expansion`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Ecosystem Lifecycle Stages`
- **Domain:** Lifecycle
- **Definition (short):** The growth stage, characterised by accelerating complementor participation, network-effect formation, and standard consolidation.
- **Definition (long):** Ecosystem Expansion is the growth stage where complementor participation accelerates, network effects form and strengthen, and the platform's standards consolidate. The transition condition to Leadership is dominance in a defensible niche and stabilising network effects.
- **Necessary conditions:**
  1. All lifecycle-stage necessary conditions (inherited).
  2. **Accelerating complementor participation.** Complementor activity MUST show sustained acceleration.
  3. **Network-effect formation.** Direct or indirect network effects MUST be observable.
- **Boundary markers:** Distinguished from `wsf:Ecosystem Birth` by validated value capture. Distinguished from `wsf:Ecosystem Leadership` by the absence of dominant niche occupation.

#### 2.2.4 `wsf:Ecosystem Leadership`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Ecosystem Lifecycle Stages`
- **Domain:** Lifecycle
- **Definition (short):** The maturity stage, characterised by dominant niche occupation, stabilising governance, and complementor lock-in.
- **Definition (long):** Ecosystem Leadership is the maturity stage where the platform occupies a dominant niche in its market, governance has stabilised, and complementors are locked in via switching costs and network effects. The transition condition to Self-Renewal is successful adaptation to disruptive change; the transition condition to Death is failure to adapt.
- **Necessary conditions:**
  1. All lifecycle-stage necessary conditions (inherited).
  2. **Dominant niche occupation.** The platform MUST occupy a dominant position in a defensible niche.
  3. **Stabilising governance.** Governance patterns MUST be stable and predictable.
- **Boundary markers:** Distinguished from `wsf:Ecosystem Expansion` by dominant niche occupation. Distinguished from `wsf:Ecosystem Self-Renewal or Death` by the absence of adaptation pressure.

#### 2.2.5 `wsf:Ecosystem Self-Renewal or Death`

- **Classification:** Tier 3 (Specialisation, terminal stage)
- **Parent:** `wsf:Ecosystem Lifecycle Stages`
- **Domain:** Lifecycle
- **Definition (short):** The terminal stage, characterised by adaptive response (Self-Renewal) or failure to adapt (Death) to disruptive change.
- **Definition (long):** Ecosystem Self-Renewal or Death is the terminal stage where the ecosystem either adapts successfully to disruptive change (Self-Renewal, returning to Leadership or Expansion under a new configuration) or fails to adapt (Death, dissolving the ecosystem). The terminal-stage characterisation captures both outcomes as alternative dispositions; the actual outcome is contingent on the adaptation response.
- **Necessary conditions:**
  1. All lifecycle-stage necessary conditions (inherited).
  2. **Adaptive pressure.** The ecosystem MUST be under adaptive pressure from disruptive change.
- **Boundary markers:** Distinguished from all other stages by being the terminal-stage disposition.

### 2.3 The health-metrics vocabulary

#### 2.3.1 `wsf:Ecosystem Health`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Disposition`
- **Domain:** Health
- **Definition (short):** The aggregate disposition of an ecosystem across four canonical health axes: Productivity, Robustness, Niche Creation, and Innovation Capacity (the Iansiti-Levien framework).
- **Definition (long):** Ecosystem Health is the aggregate disposition of an ecosystem across four canonical health axes. Each axis is measured by one or more health indicators. Health is not a single number; it is a vector of indicator values that, taken together, characterise the ecosystem's current state.
- **Necessary conditions:**
  1. All `wsf:Disposition` necessary conditions (inherited).
  2. **Multi-axis measurement.** MUST be measurable across at least three of the four canonical axes.

#### 2.3.2 `wsf:Productivity`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Health Indicator`
- **Domain:** Health (output axis)
- **Definition (short):** The efficiency with which an ecosystem converts inputs (capital, attention, labour) into outputs (complementor offerings, user value, transactions).
- **Definition (long):** Productivity is the output-per-input ratio for the ecosystem. High-productivity ecosystems generate substantial complementor offerings and user value per unit of orchestrator investment. Indicators include: complementor offering count per unit time, transaction throughput per unit platform cost, time-to-market for new offerings.
- **Necessary conditions:**
  1. All `wsf:Health Indicator` necessary conditions (inherited).
  2. **Measurability.** MUST be measurable via at least one quantitative indicator.
- **Boundary markers:** Distinguished from `wsf:Robustness` (a stability axis) by being an output axis.

#### 2.3.3 `wsf:Robustness`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Health Indicator`
- **Domain:** Health (stability axis)
- **Definition (short):** The ability of an ecosystem to maintain function in the face of shocks (complementor departure, technology change, demand shifts).
- **Definition (long):** Robustness is the stability axis of ecosystem health. Robust ecosystems maintain function despite complementor departures, technology shifts, and demand changes. Indicators include: complementor retention rate, time-to-recovery after shocks, diversity of complementor offerings.
- **Necessary conditions:**
  1. All `wsf:Health Indicator` necessary conditions (inherited).
  2. **Shock-resistance evidence.** MUST be assessable via either observed shock-recovery or simulated stress test.
- **Boundary markers:** Distinguished from `wsf:Productivity` (an output axis) by being a stability axis.

#### 2.3.4 `wsf:Niche Creation`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Health Indicator`
- **Domain:** Health (innovation axis, narrow)
- **Definition (short):** The rate at which the ecosystem generates new niches for complementor occupation.
- **Definition (long):** Niche Creation is the rate at which new niches (specialised roles, market segments, use cases) emerge within the ecosystem and are filled by complementors. High niche creation indicates the ecosystem is expanding the space of value-creation opportunities.
- **Necessary conditions:**
  1. All `wsf:Health Indicator` necessary conditions (inherited).
  2. **Niche observability.** Niche creation MUST be observable as new complementor entry into previously unoccupied specialisations.
- **Boundary markers:** Distinguished from `wsf:Innovation Capacity` (the broader axis) by being narrow (entry into existing niches). Distinguished from `wsf:Productivity` by being an innovation axis.

#### 2.3.5 `wsf:Innovation Capacity`

- **Classification:** Tier 3 (Specialisation)
- **Parent:** `wsf:Health Indicator`
- **Domain:** Health (innovation axis, broad)
- **Definition (short):** The capacity of the ecosystem to generate fundamentally new offerings, technologies, or market categories.
- **Definition (long):** Innovation Capacity is the broad innovation axis of ecosystem health. It captures the ecosystem's ability to generate genuinely new value-creation modes, not just entry into existing niches. Indicators include: rate of patent filings by ecosystem participants, emergence of entirely new complementor categories, frequency of platform-API introductions enabling new use cases.
- **Necessary conditions:**
  1. All `wsf:Health Indicator` necessary conditions (inherited).
  2. **Novelty observability.** Innovation MUST be observable as genuinely new categories (not just incremental improvement within existing categories).

### 2.4 The lifecycle state space

The four health axes combine with the four lifecycle stages to define a state space. The state of an ecosystem at a given moment is characterised by:

1. Its current lifecycle stage (Birth, Expansion, Leadership, Self-Renewal or Death).
2. Its position on each health axis (low/medium/high or a continuous measurement).
3. The trajectory implied by recent state history (improving, stable, declining).

The state space is documented in `wsf-ecosystem/diagrams/lifecycle-state-space.md` (Mermaid) and formalised as a SHACL shape in the downstream CR.

### 2.5 Relational properties for lifecycle and health

The relational properties connecting lifecycle and health to actor, structural, and value-dynamics concepts:

| Predicate | Domain | Range | Notes |
|---|---|---|---|
| `wsf-rel-eco:in_stage` | `wsf:Ecosystem` | `wsf:Ecosystem Lifecycle Stages` | Per ecosystem, per time |
| `wsf-rel-eco:measured_by` | `wsf:Ecosystem Health` | `wsf:Health Indicator` | Per axis |
| `wsf-rel-eco:exits_via` | `wsf:Ecosystem Lifecycle Stages` | `wsf:Ecosystem Lifecycle Stages` | For transition events |
| `wsf-rel-eco:degrades_into` | `wsf:Orchestrator` | `wsf:Dominator` | Per ADR-WSF-30 §2.2.3 (the keystone-to-dominator drift) |

### 2.6 Namespace and serialisation

The lifecycle and health concepts use the standard `wsf:` namespace prefix. The relational properties use the `wsf-rel-eco:` namespace reserved by ADR-WSF-28 §2.4.

Serialisation in `wsf-spec/` (Turtle, JSON Schema, Protobuf, OpenAPI) is authorised through the downstream CR (Issue #4 in `wsf-ecosystem`, gated on this ADR reaching Baseline).

## 3. Why this ADR is necessary

The lifecycle and health vocabulary completes the Ecosystem domain. Without this ADR:

1. There is no formal vocabulary for ecosystem maturation, leaving downstream analytics without a measurement framework.
2. There is no formal vocabulary for ecosystem health, leaving governance and intervention without a diagnostic vocabulary.
3. The keystone-to-dominator drift (per ADR-WSF-30 §2.2.3) cannot be expressed as a state transition with provenance.
4. The downstream CR (Issue #4) cannot register lifecycle and health concepts in `wsf-spec/`.
5. The OTCHERE Platform Ecosystem worked example (`wsf-ecosystem/examples/otchere-ecosystem/`) cannot fully instantiate the Ecosystem domain.

## 4. Consequences

### 4.1 Positive

- The Ecosystem domain gains an authoritative lifecycle and health vocabulary.
- Ecosystem state is expressible as a four-axis health vector crossed with a four-stage lifecycle progression.
- The keystone-to-dominator drift is expressible as a state transition with provenance, supporting governance intervention.
- Downstream applications (governance, analytics, intervention design) gain a measurement framework.

### 4.2 Cost

- Nine concepts require registration in `wsf-spec/`.
- SHACL shapes must be authored for the lifecycle and health vocabulary.
- Conformance tests are required for the lifecycle stage transition conditions and health-indicator measurements.
- The lifecycle state space requires a Mermaid diagram in `wsf-ecosystem/diagrams/` (already drafted) and a SHACL shape in `wsf-spec/`.

### 4.3 Implementation gate

The transition of this ADR to Baseline is contingent on ADR-WSF-30, ADR-WSF-31, and ADR-WSF-32 reaching Baseline. Until all three parents reach Baseline, this ADR remains at status Proposed (Pre-Baseline) and is not citable as authoritative.

## 5. Alternatives rejected

### A. Linear lifecycle (Birth, Growth, Maturity, Decline)

Rejected. The Iansiti-Levien framework's Self-Renewal or Death terminal stage captures the bifurcation at the end of Leadership: ecosystems may renew or die. A linear Decline stage loses this distinction and forces the analyst to choose a single outcome.

### B. Tier 1 placement for lifecycle or health concepts

Rejected. All nine concepts compose from Tier 1 primitives without loss of meaning.

### C. Tier 2 placement for lifecycle or health concepts

Rejected. Tier 2 is reserved for epistemic and identification scaffolding.

### D. Fold Self-Renewal or Death into two separate stages (Self-Renewal and Death)

Rejected. The bifurcation is observed at the same lifecycle moment (the response to adaptive pressure). Modelling them as a single stage with two terminal dispositions preserves the temporal co-location.

### E. Fold Innovation Capacity into Niche Creation

Rejected. Innovation Capacity is the broad innovation axis (entirely new categories); Niche Creation is the narrow innovation axis (entry into existing niches). The distinction is observed in practice: ecosystems may have high niche creation (filling existing roles) but low innovation capacity (failing to generate new categories).

### F. Health as a single composite score

Rejected. A single composite score loses the multi-axis information. Ecosystems may be high-productivity and low-robustness, or low-productivity and high-niche-creation. A single score hides the diagnostic value of the axes.

### G. Defer the lifecycle and health vocabulary to a later ADR

Rejected. The lifecycle and health vocabulary is required by downstream applications (governance, intervention, analytics) and by the OTCHERE worked example.

## 6. Decision summary

The decision can be reduced to one sentence.

> Nine Tier 3 specialisations (four lifecycle stages parented to `wsf:Disposition`, four health indicators parented to a Tier 3 `wsf:Health Indicator` concept, one aggregate `wsf:Ecosystem Health` parented to `wsf:Disposition`) are established as the Ecosystem domain lifecycle and health vocabulary, with the Self-Renewal or Death stage capturing the bifurcation at the Leadership-to-terminal transition.

This ADR is filed as a Draft PR. Its transition to Baseline is contingent on ADR-WSF-30, ADR-WSF-31, and ADR-WSF-32 reaching Baseline.

## 7. Required follow-on actions

1. Author SHACL shapes for the nine concepts and the four relational properties.
2. Mirror the lifecycle and health concept files from `wsf-ecosystem/concepts/lifecycle/` and `wsf-ecosystem/concepts/health/` to `wsf-examples/`.
3. Update `wsf-ecosystem/examples/otchere-ecosystem/OTCHERE-Platform-Ecosystem.md` to instantiate the lifecycle and health vocabulary.

## 8. References

- ADR-WSF-04 (Semantic Inheritance): specialisation rules.
- ADR-WSF-09 (Foundational Concept Taxonomy): tier-classification framework.
- ADR-WSF-17 (Foundational Semantic Architecture): tier discipline, derivation rules.
- ADR-WSF-20 (Concept Definition Model): §14 metadata schema.
- ADR-WSF-28 (Ecosystem as Tier 3 Worked Example): root parent.
- ADR-WSF-30 (Ecosystem Actor Taxonomy): immediate parent for actor dimension.
- ADR-WSF-31 (Ecosystem Value Dynamics): immediate parent for value-dynamics dimension.
- ADR-WSF-32 (Ecosystem Structural Primitives): immediate parent for structural dimension.
- VOCAB-000 v2.0 §3.4: source vocabulary.
- ADR-CONCEPTS-01 §4: source concept catalogue (lifecycle and health).
- Iansiti, M., and Levien, R. (2004), *The Keystone Advantage*: the four-axis health framework.

### Source artifacts in `wsf-ecosystem`

- `concepts/lifecycle/lifecycle-stages.md`, `birth.md`, `expansion.md`, `leadership.md`, `self-renewal-or-death.md`.
- `concepts/health/ecosystem-health.md`, `productivity.md`, `robustness.md`, `niche-creation.md`, `innovation-capacity.md`.
- `diagrams/lifecycle-state-space.md`: Mermaid diagram of the lifecycle state space.
- `research/01-source-reconciliation/FINDING-Source-Reconciliation.md`: source-to-concept lineage.
- `research/02-tier-classification/FINDING-Tier-Classification.md`: tier-classification rationale.
- `governance/TIER-CLASSIFICATION-MATRIX.md`: per-concept tier matrix.

---

*This ADR completes the Ecosystem domain with the lifecycle and health vocabulary. Its transition to Baseline is contingent on ADR-WSF-30, ADR-WSF-31, and ADR-WSF-32 reaching Baseline.*
