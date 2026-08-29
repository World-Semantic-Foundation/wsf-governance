# Change Request (CR) Template

> **Use this template when proposing a change that implements one or more ADRs in the WSF product.**

Per CR-WSF-17 Rev.1 §12, all CRs live in `wsf-governance/CR/` and follow the 8-stage change control lifecycle: `Investigation → Finding → Synthesis → ADR → CR → Implementation → Validation → Release`.

---

## Frontmatter

```yaml
---
cr_id: CR-WSF-XX              # Sequential number
title: <concise change title>
revision: <number>            # Rev. 1, Rev. 2, etc.
status: Proposed | Accepted | Implemented | Withdrawn
type: Foundational | Implementation | Maintenance | Conformance
implements:
  - <list of ADRs being implemented>
target_organization: World-Semantic-Foundation
scope: <brief scope description>
date: YYYY-MM-DD
author: <name or handle>
supersedes: <prior CR if any>
related:
  - <related ADRs, CRs, findings>
tags: <relevant tags>
---
```

## Required Sections

### 1. Change Request

What is being changed? State the change clearly:
- New repositories
- New files / directories
- New software components
- New documentation
- New governance scaffolding

### 2. Motivation

Why is this change needed? What problem does it solve? What opportunity does it create?

### 3. Architectural Decision Implemented

Which ADR(s) does this CR implement? Reference them explicitly.

### 4. Scope

What is in scope? What is explicitly out of scope? What are the boundaries?

### 5. Deliverables

List every concrete deliverable:
- Repositories
- Files
- Components
- Documentation
- Examples
- Tests
- Visuals

### 6. Acceptance Criteria

What must be true for this CR to be considered complete?
- Functional criteria
- Documentation criteria
- Conformance criteria
- Boundary criteria (what must NOT be done)

### 7. Implementation Approach

How will this CR be implemented?
- Order of work
- Dependencies
- Rollout strategy
- Testing strategy

### 8. Explicit Non-Goals

What does this CR NOT do? Be explicit:
- Things deferred to subsequent CRs
- Things that are explicitly out of WSF scope
- Things that belong to other organizations

### 9. Success Condition

How will we know this CR succeeded? What is the success criterion?

### 10. Cross-References

- ADRs being implemented
- Related CRs
- Findings
- Investigation sections

---

## Process

1. **Identify**: What ADR(s) need implementation?
2. **Draft**: Use this template
3. **Submit**: Place in `wsf-governance/CR/`
4. **Review**: Solicit review per governance process
5. **Accept**: Update to `status: Accepted`
6. **Implement**: Execute the work
7. **Validate**: Test against acceptance criteria
8. **Close**: Mark complete and link to releases

---

## Authoring Guidelines

- **Reference the ADR(s)**: Every CR must implement at least one ADR
- **Be specific about deliverables**: List concrete files, components, repos
- **Explicit non-goals**: Critical for scope control
- **Use canonical examples**: OTCHERE Inc / Kwesi
- **Apply principles**: All 12 Foundational Principles apply
- **Preserve boundaries**: OpenDEA, Assessment-Models, WSF boundaries

---

## Example Stub

```yaml
---
cr_id: CR-WSF-XX
title: <Implementation Title>
revision: 1
status: Proposed
type: Implementation
implements:
  - ADR-WSF-XX
target_organization: World-Semantic-Foundation
scope: <scope>
date: YYYY-MM-DD
author: <handle>
supersedes: ~
related:
  - <related items>
tags: []
---

# CR-WSF-XX — <Title>

## 1. Change Request

<Describe what is being created/changed>

## 2. Motivation

<Why this change>

## 3. Architectural Decision Implemented

<Reference ADRs>

## 4. Scope

### In Scope
- ...

### Out of Scope
- ...

## 5. Deliverables

- [ ] Deliverable 1
- [ ] Deliverable 2
- [ ] ...

## 6. Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] ...

## 7. Implementation Approach

<Approach>

## 8. Explicit Non-Goals

- Not X
- Not Y
- Not Z

## 9. Success Condition

<How we know it succeeded>

## 10. Cross-References

- ADR-WSF-XX
- Related findings
- Related investigation sections
```

---

*This template is established per CR-WSF-17 Rev.1 §12 governance scaffolding. CRs are the implementation vehicles for ADRs.*
