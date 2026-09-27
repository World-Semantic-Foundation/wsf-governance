---
adr-id: ADR-WSF-35
title: Service Semantic Grounding (ES Integration)
status: baseline
date: 2026-09-26
deciders: eaojnr
related-adrs: [ADR-WSF-33, ADR-WSF-34, ADR-WSF-17]
related-findings: [Recon-ES-006]
related-crs: [CR-WSF-35]
phase: foundation-integration
---

# ADR-WSF-35 ; Service Semantic Grounding (ES Integration)

> Cross-reference: WSF-ADR-SERVICE-001 (subject-namespace alias per LOCKED-PICKS v9)
> Supersedes: none (first canonical WSF Service grounding ADR)
> ES Integration: resolves Recon-ES-006 (Service + Product foundational dependency gap)

## 1. Context

The WSF vocabulary (wsf-spec/turtle/wsf-vocabulary.ttl) declares `wsf:Service` as a Tier 3 concept at Baseline status:

    wsf:Service a wsf:Concept ;
        rdfs:label "Service" ;
        rdfs:comment "A Function exposed by an Entity for consumption by other Entities." ;
        wsf:tier "Tier 3" ;
        wsf:parent wsf:Function ;
        wsf:status "Baseline" ;
        wsf:version "1.0.0"

Enterprise-Semantics has two governed specializations (Agentic Service ES-014, Autonomous Service ES-015) whose concept YAMLs assert inheritance of "WSF Service grounding via the parent Service concept" ; but no WSF ADR formally grounds Service as a governed foundational concept, and no ES-side base Service record exists. Recon-ES-006 (2026-09-26) confirmed the gap via exhaustive branch audit.

This ADR closes the gap by formally grounding WSF Service as the authoritative foundation, following the Culture (ADR-WSF-33) / System (ADR-WSF-34) integration pattern.

## 2. Decision

### 2.1 Canonical Definition

A Service is a Function exposed by an Entity for consumption by other Entities.

Anchored in the WSF vocabulary Tier 3 declaration (parent: wsf:Function, itself grounded as "a purposeful kind of Activity enabled by Capability").

### 2.2 WSF Owns Foundational Meaning

WSF is the semantic authority for Service. Downstream programs (including Enterprise-Semantics) specialize via integration ADRs and SHALL NOT redefine the foundation locally.

### 2.3 ES Integration Contract

Enterprise-Semantics SHALL:

1. Adopt wsf:Service as the authoritative base concept for Agentic Service (ES-014) and Autonomous Service (ES-015)
2. File an ES integration ADR/CR pair adopting this foundation
3. Record the ES-side base Service concept as a WSF reference (authority: WSF), per the culture/system demotion pattern
4. Maintain boundary assertions: specialization requires material agentic/autonomous behavior at the service level ; AI is not required

## 3. Status Lifecycle

Filed at Proposed ; promoted to Baseline upon publication per the Change Control Lifecycle (Stage 6).

## 4. Consequences

### Positive

- The Service foundation gap (Recon-ES-006) is closed at the authoritative layer
- ES-014 + ES-015 dependency gates become satisfiable retroactively
- The foundation-first rule is restored end-to-end for the Service boundary

### Trade-offs

- Retroactive grounding: the specializations predate the foundation ADR (they were filed before the ES-022 dependency-gate discipline). No rework needed ; the specializations are self-consistent.

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

---

## Baseline Promotion Metadata

- promotion_date: 2026-09-26
- promotion_trigger: Change Control Lifecycle Stage 6 (Publish) ; wsf:Service already Tier 3 Baseline in wsf-spec vocabulary (confirmed 2026-09-26)
- prior_status: Proposed
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
- downstream_unblocked: ES integration ADR/CR pairs (ES-031 Service, ES-032 Product) + retroactive satisfaction of ES-014/015/016/017 dependency gates
