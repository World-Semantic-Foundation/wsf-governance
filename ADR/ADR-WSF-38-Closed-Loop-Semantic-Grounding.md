# ADR-WSF-38 ; Closed Loop Semantic Grounding ; Tier 3 Baseline

**Status:** Proposed
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

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
