# WSF Identifier Reconciliation ; 2026-09-28

> Per LOCKED-PICKS v9 §313-318 and the user-authoritative model (2026-09-28).

## Status

Established. Machine-readable + human-readable identity reconciliation between canonical sequential IDs and subject-namespace aliases.

## Author

Emmanuel A. Otchere (cardinal user-authoritative model, 2026-09-28)

## Background

WSF governance uses two parallel identifier systems:

1. **Canonical sequential IDs**. ADR-WSF-NNN (e.g. ADR-WSF-33) and CR-WSF-NNN (e.g. CR-WSF-33). These are the primary references and authoritative identifiers.
2. **Subject-namespace aliases**. WSF-ADR-<SUBJECT>-<LOCAL> (e.g. WSF-ADR-CULTURE-001) and WSF-CR-<SUBJECT>-<LOCAL>. These were introduced for cross-program traceability when ES-integration tranches were filed.

Per LOCKED-PICKS v9 §313-318, subject-namespace IDs are aliases for github.com canonical sequential IDs. The two systems are reconciled below.

## Resolution rule

- **Canonical references**: always use ADR-WSF-NNN (or CR-WSF-NNN for Change Requests). This is the authoritative identifier.
- **Cross-program references**: subject-namespace aliases are accepted as input but are resolved to the canonical ID for storage, citation, and conformance checks.
- **Inputs**: search tools, citation tools, and citation builders MAY accept either form. They MUST resolve to canonical before persisting.

## Identifier mapping table

### ADR aliases

| Subject-namespace alias | Canonical ID | Status | Cross-program target |
|-------------------------|--------------|--------|----------------------|
| WSF-ADR-CULTURE-001 | ADR-WSF-33 | Baseline | ES-026 (Culture integration, Final) |
| WSF-ADR-SYSTEM-001 | ADR-WSF-34 | Baseline | ES-027 (System integration, Final) |
| WSF-ADR-SERVICE-001 | ADR-WSF-35 | Baseline | ES-031-SVC (Service integration, Accepted, compound ID) |
| WSF-ADR-PRODUCT-001 | ADR-WSF-36 | Baseline | ES-032-PRD (Product integration, Accepted, compound ID) |
| WSF-ADR-NETWORK-001 | ADR-WSF-37 | Deprecated (2026-09-28) | ES-031 + ES-032 (Network pair, ES-side canonical) |
| WSF-ADR-CLOSED-LOOP-001 | ADR-WSF-38 | Deprecated (2026-09-28) | ES-034 + ES-035 (Closed Loop stack, ES-side canonical) |

### CR aliases

| Subject-namespace alias | Canonical ID |
|-------------------------|--------------|
| WSF-CR-CULTURE-001 | CR-WSF-33 |
| WSF-CR-SYSTEM-001 | CR-WSF-34 |
| WSF-CR-SERVICE-001 | CR-WSF-35 |
| WSF-CR-PRODUCT-001 | CR-WSF-36 |
| WSF-CR-NETWORK-001 | CR-WSF-37 (Deprecated 2026-09-28) |
| WSF-CR-CLOSED-LOOP-001 | CR-WSF-38 (Deprecated 2026-09-28) |

### Foundational ADRs (no subject-namespace alias)

ADR-WSF-17..27 (Foundational architecture) and ADR-WSF-28..32 (Ecosystem cluster) use canonical sequential IDs only. Subject-namespace aliases were introduced starting with ADR-WSF-33 (ES-Integration tranche).

## Machine-readable mapping

See id-aliases.yaml (companion file) for the machine-readable reconciliation table.

## Deprecation note

ADR-WSF-37 + ADR-WSF-38 (Network + Closed Loop) and their companion CRs were Deprecated on 2026-09-28 per the user-authoritative model. Their subject-namespace aliases are retained for historical traceability. Resolution to canonical still works. Canonical status is Deprecated.

## Cross-program impact

- ES side: ES-026/027/029/030/031-SVC/032-PRD are the canonical integrations. Cross-program traceability preserved via subject-namespace aliases on the WSF side.
- ES-031/032/034/035 are ES-side canonical realizations. Their WSF aliases (WSF-ADR-NETWORK-001 + WSF-ADR-CLOSED-LOOP-001) are Deprecated. ES-side identifiers are primary.
- The compound ID convention (ES-031-SVC + ES-032-PRD) is documented in enterprise-semantics/authority-chain.md.

## Update history

- 2026-09-28. Initial reconciliation established per LOCKED-PICKS v9 §313-318 + user-authoritative model. Author: Emmanuel A. Otchere (cardinal user-authoritative model, 2026-09-28)
