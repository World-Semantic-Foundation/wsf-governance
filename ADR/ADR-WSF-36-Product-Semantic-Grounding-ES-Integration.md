---
adr-id: ADR-WSF-36
title: Product Semantic Grounding (ES Integration)
status: proposed
date: 2026-09-26
deciders: eaojnr
related-adrs: [ADR-WSF-33, ADR-WSF-34, ADR-WSF-35, ADR-WSF-17]
related-findings: [Recon-ES-006]
related-crs: [CR-WSF-36]
phase: foundation-integration
---

# ADR-WSF-36 ; Product Semantic Grounding (ES Integration)

> Cross-reference: WSF-ADR-PRODUCT-001 (subject-namespace alias per LOCKED-PICKS v9)
> Supersedes: none (first canonical WSF Product grounding ADR)
> ES Integration: resolves Recon-ES-006 (Service + Product foundational dependency gap)

## 1. Context

Unlike Service, the WSF vocabulary (wsf-spec/turtle/wsf-vocabulary.ttl, audited 2026-09-26) contains NO `wsf:Product` declaration. Enterprise-Semantics has two governed specializations (Agentic Product ES-016, Autonomous Product ES-017) whose concept YAMLs assert inheritance of "WSF Product grounding via parent Product concept" ; but neither an ES-side base Product record nor a WSF declaration exists. Recon-ES-006 (2026-09-26) confirmed the gap via exhaustive branch audit.

This ADR establishes WSF Product as a canonical Tier 3 concept, following the Culture (ADR-WSF-33) / System (ADR-WSF-34) / Service (ADR-WSF-35) pattern.

## 2. Decision

### 2.1 Canonical Definition

A Product is a coherent, governable bundle of Functions and Services offered by an Entity for exchange, consumption, or value realization by other Entities.

Rationale: WSF grounds Service as "a Function exposed by an Entity for consumption by other Entities" (Tier 3, parent wsf:Function). Product composes Functions and Services into an exchangeable, governable unit. This keeps the vocabulary chain intact: Capability -> Disposition -> Function -> Service -> Product.

### 2.2 Vocabulary Addition

This ADR authorizes the addition of `wsf:Product` to the WSF vocabulary:

    wsf:Product a wsf:Concept ;
        rdfs:label "Product" ;
        rdfs:comment "A coherent, governable bundle of Functions and Services offered by an Entity for exchange, consumption, or value realization by other Entities." ;
        wsf:tier "Tier 3" ;
        wsf:parent wsf:Function ;
        wsf:status "Baseline" ;
        wsf:authority "WSF" ;
        wsf:version "1.0.0"

### 2.3 WSF Owns Foundational Meaning

WSF is the semantic authority for Product. Downstream programs specialize via integration ADRs and SHALL NOT redefine the foundation locally.

### 2.4 ES Integration Contract

Enterprise-Semantics SHALL:

1. Adopt wsf:Product as the authoritative base concept for Agentic Product (ES-016) and Autonomous Product (ES-017)
2. File an ES integration ADR/CR pair adopting this foundation
3. Record the ES-side base Product concept as a WSF reference (authority: WSF)
4. Maintain boundary assertions: specialization requires material agentic/autonomous behavior at the product level ; AI is not required

## 3. Status Lifecycle

Filed at Proposed ; promoted to Baseline upon publication + vocabulary landing per the Change Control Lifecycle (Stage 6).

## 4. Consequences

### Positive

- The Product foundation gap (Recon-ES-006) is closed at the authoritative layer
- ES-016 + ES-017 dependency gates become satisfiable retroactively
- The vocabulary chain Capability -> Disposition -> Function -> Service -> Product is complete

### Trade-offs

- Vocabulary change required (unlike Service, which was already declared). The change is additive-only ; no existing declarations are modified.

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
