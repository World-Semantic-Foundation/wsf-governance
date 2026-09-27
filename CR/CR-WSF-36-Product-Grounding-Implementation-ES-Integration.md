---
cr-id: CR-WSF-36
title: Product Grounding Implementation (ES Integration)
status: proposed
date: 2026-09-26
implements: ADR-WSF-36
related-crs: [CR-WSF-33, CR-WSF-34, CR-WSF-35]
phase: foundation-integration
---

# CR-WSF-36 ; Product Grounding Implementation (ES Integration)

> Cross-reference: WSF-CR-PRODUCT-001 (subject-namespace alias)

## 1. Intent

Implement ADR-WSF-36: add wsf:Product to the WSF vocabulary and formalize it as the governed authoritative foundation for Product specializations.

## 2. Scope

1. Add the wsf:Product declaration to wsf-spec/turtle/wsf-vocabulary.ttl (per ADR-WSF-36 section 2.2)
2. Confirm no existing declarations are modified (additive-only change)
3. Notify downstream integration: Enterprise-Semantics files its integration ADR/CR pair

## 3. Acceptance Criteria

1. ADR-WSF-36 filed and promoted to Baseline
2. wsf:Product declaration landed in wsf-spec vocabulary
3. Vocabulary diff is additive-only (no existing term modified)
4. ES-side integration pair filed (ES-ADR-032 + ES-CR-032)
5. ES base Product concept record created as WSF reference (authority: WSF)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
