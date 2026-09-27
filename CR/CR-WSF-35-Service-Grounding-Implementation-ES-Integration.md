---
cr-id: CR-WSF-35
title: Service Grounding Implementation (ES Integration)
status: baseline
date: 2026-09-26
implements: ADR-WSF-35
related-crs: [CR-WSF-33, CR-WSF-34]
phase: foundation-integration
---

# CR-WSF-35 ; Service Grounding Implementation (ES Integration)

> Cross-reference: WSF-CR-SERVICE-001 (subject-namespace alias)

## 1. Intent

Implement ADR-WSF-35: formalize wsf:Service as the governed authoritative foundation for Service specializations in downstream programs.

## 2. Scope

1. Confirm the wsf:Service vocabulary declaration (Tier 3, Baseline, parent wsf:Function) as the canonical record ; no vocabulary change needed (already Baseline in wsf-spec)
2. This CR records the governance formalization ; the vocabulary artefact already exists
3. Notify downstream integration: Enterprise-Semantics files its integration ADR/CR pair

## 3. Acceptance Criteria

1. ADR-WSF-35 filed and promoted to Baseline
2. wsf:Service declaration cross-referenced from the ADR
3. ES-side integration pair filed (ES-ADR-031 + ES-CR-031)
4. ES base Service concept record created as WSF reference (authority: WSF)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

---

## Baseline Promotion Metadata

- promotion_date: 2026-09-26
- promotion_trigger: Change Control Lifecycle Stage 6 (Publish) ; wsf:Service vocabulary declaration confirmed
- prior_status: Proposed
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
- downstream_unblocked: ES integration ADR/CR pairs (ES-031 Service, ES-032 Product) + retroactive satisfaction of ES-014/015/016/017 dependency gates
