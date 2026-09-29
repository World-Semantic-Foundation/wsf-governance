# ADR-WSF-38 ; Closed Loop Semantic Grounding ; Tier 3 Baseline

**Status:** Deprecated
**Date:** 2026-09-27
**Deciders:** eaojnr
**Phase:** Tier 3 ; Foundational
**Authority:** WSF

## 1. Context

The Recon-ES-008 (Closed Loop Grounding Question, filed 2026-09-27) established that Closed Loop has distinct semantic content (sense-decide-act-learn with feedback) that is materially different from Workflow (no feedback requirement) and Operations (no loop requirement). It warrants WSF-level foundation treatment per the foundation-first rule.

## 2. Canonical Definition

A Closed Loop is a control structure with four stages:

- sense (observe the state of a target)
- decide (select an action based on observed state and policy)
- act (execute the action)
- learn (update policy based on the effect of the action)

connected by feedback such that the output of act influences subsequent sense iterations.

Variant formulations (OODA, PDCA) are accommodated as profile families over Closed Loop, not as separate concepts.

## 3. Boundary

Closed Loop is NOT reducible to:

- Workflow (which has no feedback requirement ; a workflow may not feed act back into sense)
- Operations (which has no loop requirement ; operations may be one-time)
- Process (which is a sequence without feedback)

Closed Loop IS:

- a control-theory concept ; semantically independent of any technology
- a structure that can be realized with humans, machines, or both
- capable of being learned from or not (so learning is a property, not a definition requirement)

## 4. AI Boundary

Closed Loop does not require AI. An AI closed loop is a Closed Loop with AI realization, not a different concept. Per the cardinal AI boundary rule, "AI Closed Loop" is not a canonical concept ; it is realized as an example over Closed Loop + AI realization.

## 5. Specialization Discipline

Any specialization of Closed Loop MUST reference wsf:ClosedLoop as the parent. The Autonomous Closed Loop candidate (CR-ES-022 section 4) gates on this ADR landing at Baseline.

## Baseline Promotion Metadata

- promotion_date: 2026-09-27
- promotion_trigger: wsf-spec PR #2 MERGED (; enables ES-035 integration pair)
- prior_status: Proposed
- final_status: Baseline
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Demotion Notice ; 2026-09-28

**Status change:** Baseline -> Deprecated

**Trigger:** per user-authoritative model (2026-09-28), Closed Loop is realized as
ES-canonical behavioral_pattern (ES-034) + ES-canonical behavioral_pattern
specialization (ES-035 Autonomous Closed Loop). WSF retains the minimal
kernel only. Closed Loop is no longer Tier 3 Baseline at WSF, it is
ES-side behavioral pattern. This ADR is Deprecated and remains as a
historical decision record. ES-034/035 are the canonical places.

**Cross-program impact:**
- ES-031 (Agentic Network) remains canonical specialization of ES:CONCEPT:network (ES-side)
- ES-032 (Autonomous Network) remains canonical specialization of ES:CONCEPT:network (ES-side)
- ES-034 (Closed Loop) remains canonical behavioral_pattern (ES-side)
- ES-035 (Autonomous Closed Loop) remains canonical behavioral_pattern_specialization (ES-side)
- WSF wsf-vocabulary.ttl demotes wsf:Network + wsf:ClosedLoop (Tier 3 Baseline -> removed)
- WSF retains wsf:Entity as the generic foundation for Network specialization
- WSF minimal kernel unchanged

**Author:** Emmanuel A. Otchere (cardinal user-authoritative model, 2026-09-28)

**Cross-references:**
- ADR-WSF-17 Foundational Semantic Architecture (kernel unchanged)
- ADR-WSF-19 Semantic Relationship Model (specializes+of preserved)
- ES-031 / ES-032 / ES-034 / ES-035 (canonical at ES)
- authority-chain.md (cross-program authority chain)
