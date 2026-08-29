# Architectural Decision Record (ADR) Template

> **Use this template when proposing an architectural decision that affects WSF or its integration with downstream systems.**

Per CR-WSF-17 Rev.1 §12, all ADRs live in `wsf-governance/ADR/` and follow the 8-stage change control lifecycle: `Investigation → Finding → Synthesis → ADR → CR → Implementation → Validation → Release`.

---

## Frontmatter

```yaml
---
adr_id: ADR-WSF-XX              # Sequential number; reconcile with existing ADR register
title: <concise decision title>
status: Proposed | Accepted | Deprecated | Superseded
date: YYYY-MM-DD
author: <name or handle>
deciders: <list of decision-makers if known>
supersedes: <ADR-WSF-YY if applicable>
superseded_by: <ADR-WSF-ZZ if applicable>
related:
  - <list of related ADRs/CRs/findings>
tags: <list of relevant tags>
---
```

## Required Sections

### Context

What is the issue or opportunity we're seeing? Why does this decision need to be made now? What investigations or research inform this decision?

### Decision

What is the architectural decision being made? State it clearly and unambiguously. Include:
- The decision statement
- Any definitions being established
- Any distinctions being formalized
- Any principles being applied

### Consequences

What becomes possible or impossible because of this decision?
- Positive consequences
- Negative consequences
- Risks and mitigations

### Alternatives Considered

What other options were considered, and why were they rejected?

### Cross-References

- Related ADRs
- Related CRs
- Related findings
- Related investigation sections
- Related example entities (OTCHERE/Kwesi)

### Lifecycle Status

Current status of this ADR. Per the 6-stage semantic status model:
- **Candidate** — Under initial consideration
- **Investigating** — Under formal investigation
- **Proposed** — Formally proposed, awaiting decision
- **Normative** — Accepted and authoritative
- **Deprecated** — No longer recommended
- **Retired** — Formally withdrawn

---

## Process

1. **Investigate**: Research the question, document findings
2. **Synthesize**: Consolidate findings into a coherent position
3. **Propose**: Create the ADR using this template with `status: Proposed`
4. **Review**: Solicit review from stakeholders (per governance process)
5. **Accept**: Update to `status: Accepted` once approved
6. **Implement**: Create CR(s) to operationalize
7. **Deprecate/Retire**: Update status as needed

---

## Authoring Guidelines

- **Be specific**: Avoid ambiguous language
- **Reference evidence**: Link to findings, investigations, examples
- **State principles**: Apply the 12 Foundational Principles
- **Use canonical examples**: OTCHERE Inc / Kwesi — never ACME
- **Distinguish concerns**: Do NOT conflate investigation findings with architectural decisions with implementation artifacts
- **Preserve identity**: Reference Semantic Identity, not just names

---

## Example Stub

```yaml
---
adr_id: ADR-WSF-18
title: WSF Concept Identity Model
status: Proposed
date: 2026-08-29
author: WSF Program
deciders: <pending>
supersedes: ~
superseded_by: ~
related:
  - ADR-WSF-10 Semantic Identity & Naming
  - ADR-WSF-17 Foundational Semantic Architecture
  - CR-WSF-17 Rev.1
tags: [identity, namespace, foundational]
---

# ADR-WSF-18 — WSF Concept Identity Model

## Context

WSF needs a stable, persistent identity model for concepts that survives:
- Repository migration
- Representation changes (RDF/OWL/JSON-LD)
- Version evolution
- Specialization

The investigation record (Investigation 6 — Identity–Reference) established that Identity ≠ Identifier ≠ Name ≠ Reference ≠ Representation.

## Decision

[To be drafted when this ADR is proposed]

## Consequences

[To be drafted]

## Alternatives Considered

[To be drafted]

## Cross-References

- ADR-WSF-10: Semantic Identity & Naming
- Investigation 6 — Identity–Reference

## Lifecycle Status

Status: Candidate → Proposed → Normative
```

---

*This template is established per CR-WSF-17 Rev.1 §12 governance scaffolding. ADRs are immutable historical records once Accepted; changes occur through subsequent ADRs.*
