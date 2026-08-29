# Change Control Lifecycle

> **The 8-stage lifecycle that governs every semantic change in WSF.**

Per CR-WSF-17 Rev.1 §13, every semantic artifact progresses through this lifecycle. The lifecycle is itself an ADR subject — refinements are made through the ADR process.

---

## The 8-Stage Lifecycle

```
Investigation
    ↓
Finding
    ↓
Synthesis
    ↓
ADR
    ↓
CR
    ↓
Implementation
    ↓
Validation
    ↓
Release
```

| Stage | Purpose | Output |
|---|---|---|
| **Investigation** | Research a question | Investigation document |
| **Finding** | Document observations | Findings ledger entry |
| **Synthesis** | Consolidate findings | Synthesis document |
| **ADR** | Establish architectural decision | ADR record |
| **CR** | Propose implementation | CR document |
| **Implementation** | Execute the change | Repository artifacts, code |
| **Validation** | Verify acceptance criteria | Validation report |
| **Release** | Make normative | Tagged release |

---

## Stage Details

### 1. Investigation

- Research questions, prior art, references
- Document in `wsf-governance/RESEARCH/`
- Tag as investigation (not decision)
- Output: Investigation document with findings

### 2. Finding

- Each observation recorded in findings ledger
- One finding per file (e.g., `F-123-finding-name.md`)
- Status: OPEN (until promoted)
- Output: Findings (F-NNN)

### 3. Synthesis

- Consolidate related findings
- Identify architectural decisions needed
- Output: Synthesis document (per investigation)

### 4. ADR

- Establish architectural position
- Use ADR template
- Reference findings and synthesis
- Output: ADR record in `wsf-governance/ADR/`

### 5. CR

- Propose implementation of one or more ADRs
- Use CR template
- Specify deliverables and acceptance criteria
- Output: CR record in `wsf-governance/CR/`

### 6. Implementation

- Execute CR work
- Create repositories, files, components
- Apply canonical examples (OTCHERE/Kwesi)
- Output: Working artifacts

### 7. Validation

- Verify against CR acceptance criteria
- Test against principles
- Output: Validation report

### 8. Release

- Tag release
- Update semantic status (Candidate → Normative)
- Announce
- Output: Tagged release with changelog

---

## Critical Distinctions

The lifecycle explicitly distinguishes:

```
Investigation Finding  ≠  Architectural Decision  ≠  Implementation
```

These three categories are **NOT** to be conflated:
- A finding is an observation
- A decision is an architectural position
- Implementation is the execution

Each category lives in different documentation:
- Findings: `01_findings/` (or `wsf-governance/RESEARCH/findings/`)
- Decisions: `wsf-governance/ADR/`
- Implementation: `wsf-governance/CR/` + the actual artifacts

---

## Implementation Gate

Per ADR-WSF-17:

> **No implementation shall be interpreted as automatically creating a normative semantic decision.**

A successful Implementation does NOT make the underlying decision Normative. Normativity is granted through:
- Successful Validation
- Explicit acceptance by governance authority
- Status transition per the Semantic Status Model

---

## Lifecycle Tracing

Each artifact in WSF should trace back through:

```
Artifact (in implementation)
   ↓ traces to
Repository Artifact
   ↓ traces to
CR (Implementation)
   ↓ traces to
ADR (Architectural Decision)
   ↓ traces to
Synthesis
   ↓ traces to
Findings (F-NNN)
   ↓ traces to
Investigation
```

This traceability is itself a governance asset.

---

## Re-entry

The lifecycle is NOT strictly one-way. An artifact may re-enter earlier stages:
- **Release → Investigation**: If a normative artifact needs revision, new investigation begins
- **Normative → Deprecated**: Through the Semantic Status Model
- **Implementation → CR**: If implementation issues are found, a new CR is created

Re-entry is governed by the ADR/CR process, not by informal decision.

---

## Example Lifecycle

```
Day 0:   Investigation: "What is the semantic distinction between Entity and Concept?"
Day 14:  Finding F-345: Entity ≠ Concept
Day 30:  Synthesis: Foundational Ontology Investigation
Day 60:  ADR-WSF-XX: Foundational Concept Ontology
Day 75:  CR-WSF-XX: Implement Entity/Concept distinction in wsf/
Day 90:  Implementation: concepts/entity.md, concepts/concept.md
Day 100: Validation: acceptance criteria met
Day 105: Release: tag v0.1.0, status: Normative
```

---

*This lifecycle is established per CR-WSF-17 Rev.1 §13. Refinements are made through the ADR process.*
