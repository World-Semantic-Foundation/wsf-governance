# ADR-WSF-29: Domain-Extension Numbering and Categorisation Convention

> **Status:** Proposed
> **Decision Type:** Governance convention
> **Scope:** All future ADRs and CRs in the World Semantic Foundation
> **Supersedes:** None
> **Depends On:** ADR-WSF-17 (Foundational Semantic Architecture)
> **Related:** ADR-WSF-28 (Ecosystem as Tier 3 Worked Example)
> **Paired submission:** This ADR is filed in the same PR as ADR-WSF-28.

---

## 1. Context

The World Semantic Foundation has filed twenty-seven ADRs (ADR-WSF-01 through ADR-WSF-27) without an explicit numbering and categorisation convention. The conventions that have emerged are discovered by reading the existing files rather than by consulting a governing ADR. As the foundation grows, particularly as it begins to admit domain extensions (the first of which is the Ecosystem domain established by ADR-WSF-28), the absence of an explicit convention will produce three problems.

1. **Discoverability.** Reviewers and consumers cannot tell from an ADR number alone whether the ADR is foundational (semantic primitive), implementational (engine, integration, visualisation, digital twin), or domain-extending (a specific domain such as ecosystem). The number carries no category information.
2. **Allocation disputes.** As multiple working groups form around different domains (Ecosystem, Service Management, Identity, Knowledge Management, and others), questions will arise about which number range each group may use. Without a convention, allocation becomes ad hoc.
3. **CR-to-ADR binding.** The existing CR (`CR-WSF-17-Rev.1-Establish-WSF-Product-Foundation.md`) demonstrates a `CR-WSF-NN.RevM` pattern, but the pattern is not codified. Each future CR must re-derive the convention.

This ADR establishes the convention explicitly. It is filed as a paired submission with ADR-WSF-28 so that the convention is in force at the moment of its first domain-extension use.

## 2. Decision

### 2.1 ADR numbering

ADR numbers SHALL be assigned sequentially from `ADR-WSF-01` upward, with no gaps. The number has no categorical meaning in itself; categorisation is communicated through the `Decision Type` field in the frontmatter (per §2.4).

### 2.2 ADR number ranges

The following ranges are reserved for the indicated categories. The ranges are soft: an ADR whose primary concern crosses categories MAY be filed in either range, at the author's discretion, with the choice recorded in the frontmatter.

| Range | Reserved category | Definition |
|---|---|---|
| ADR-WSF-01 to ADR-WSF-17 | Foundational semantics | Decisions establishing the semantic primitives, tier discipline, and architectural lineage. Includes ADR-WSF-17 (the foundational architecture itself). |
| ADR-WSF-18 to ADR-WSF-27 | Implementation architecture | Decisions implementing the foundational architecture in software, integration, visualisation, and simulation. Includes ADR-WSF-24 (Software), ADR-WSF-25 (Integration), ADR-WSF-26 (Visualisation), ADR-WSF-27 (Digital Twin / Simulation). |
| ADR-WSF-28 onward | Domain extensions | Decisions extending the foundational architecture to specific domains. The first is ADR-WSF-28 (Ecosystem). Subsequent domain extensions (Service Management, Identity, Knowledge Management, etc.) follow in sequential order. |

The ranges are recorded here for documentation. They are not enforced: an ADR whose number is in the implementation-architecture range but whose primary concern is a domain extension SHALL be filed in the domain-extension range, with a one-line note in the frontmatter recording the rationale. The ranges exist to make the index scannable, not to constrain the work.

### 2.3 CR numbering and sub-numbering

CRs SHALL be named `CR-WSF-NN.RevM`, where:

- `NN` is the number of the ADR that authorises the CR.
- `RevM` is the revision number, starting at `Rev.1` for the first CR implementing an ADR, and incrementing for subsequent revisions of the same CR.

If a CR depends on more than one ADR, `NN` SHALL be the lower of the ADR numbers, and the additional ADRs SHALL be recorded in the CR's `Depends On` field.

If a CR does not depend on a specific ADR (an implementation work item that arises from maintenance, not from an architectural decision), the CR SHALL use the number `CR-WSF-00.RevM`, where `00` signals an orphan CR that requires ADR-WSF-NN parent assignment before reaching Baseline.

### 2.4 Frontmatter fields

Every ADR and CR SHALL carry the following frontmatter fields, in addition to the existing fields established by ADR-WSF-20 and ADR-WSF-17. The fields are normative for ADRs and CRs filed after the acceptance of this ADR; pre-existing ADRs MAY be retro-fitted at the next revision cycle.

```yaml
---
status: Candidate | Investigating | Proposed | Baseline | Final | Deprecated | Retired
decision_type: Foundational | Implementation | Domain Extension | Governance | Convention
scope: <free text: what the decision applies to>
supersedes: <ADR-NN or none>
depends_on: [<list of ADR-NN>]
related: [<list of ADR-NN>]
paired_submission: <ADR-NN or none>  # present only when filed with a paired ADR
category: foundational | implementation | domain-extension | governance | convention
---
```

The `category` field is the canonical machine-readable form of the categorisation. The `decision_type` field is the human-readable form. Both SHALL agree.

### 2.5 Index and ADR README maintenance

The ADR README SHALL maintain three sections, in order: Foundational, Implementation, Domain Extension, Governance, Convention. Each section lists the ADRs in that category in numerical order. Pre-existing ADRs SHALL be retro-fitted into the sections at the next README revision.

## 3. Why this ADR is necessary

The convention is required to make the foundation scannable, to prevent allocation disputes, and to formalise the CR-to-ADR binding that has emerged in practice. Without it, every future ADR requires reviewers to derive the convention afresh, and every new domain-extension working group must negotiate its number range from first principles.

The convention is also required to demonstrate that the foundation scales. Twenty-seven ADRs are tractable; two hundred are not, unless the index is structured. The categories established by this ADR are the structure.

## 4. Consequences

### 4.1 Positive

- Reviewers can locate an ADR by category without scanning the full index.
- New domain-extension working groups receive a number range automatically (the next free slot in the domain-extension range).
- CR sub-numbering is codified, removing the need to derive the convention from the single existing example.
- Frontmatter fields provide machine-readable ADR metadata, enabling tooling (search, filtering, validation) that the existing free-form frontmatter does not.
- The ADR README structure supports scannability at scale.

### 4.2 Cost

- The ADR README requires a one-time restructuring from the current two-section layout (Foundational + Implementation) to the five-section layout established by §2.5.
- Pre-existing ADRs MAY require a one-line frontmatter addition (`category:` field) at next revision. This is not retroactive; existing ADRs are valid as filed.
- The convention constrains naming choices. Future ADRs that cross categories must declare a primary category.
- New tooling (if developed) MUST consume the frontmatter fields, which means frontmatter MUST be machine-parseable. This is a soft constraint that requires discipline, not enforcement.

These costs are accepted consequences of bringing the convention into explicit form.

### 4.3 Implementation gate

This ADR does NOT authorise any CR. The convention takes effect on acceptance. No implementation work is required beyond the one-time README restructuring, which is performed as part of this ADR's PR (the PR that includes this ADR also includes the README update).

## 5. Alternatives rejected

### A. Do nothing; let conventions emerge.

Rejected because the convention is needed now, before the foundation grows beyond twenty-seven ADRs. Waiting until fifty ADRs forces a more disruptive retrofit.

### B. Reserve disjoint number ranges per working group (Ecosystem gets 28 to 49, Service Management gets 50 to 79, etc.).

Rejected because it requires a Working Group Charter for every domain extension, which is governance overhead the foundation is not yet positioned to support. The single domain-extension range is simpler and equally scannable through the frontmatter `category:` field.

### C. Drop the convention into the existing CR (`CR-WSF-17-Rev.1`) as a revision.

Rejected because the convention is a governance decision in its own right, not a revision of an implementation CR. Filing it as a CR revision would obscure its nature.

### D. Make the convention a Tier-1 finding rather than an ADR.

Rejected because the convention is not a Tier 1 semantic primitive; it is a governance decision about how ADRs and CRs are named and structured. ADR is the correct category.

## 6. Decision summary

The decision can be reduced to one sentence.

> ADR numbers are assigned sequentially with no categorical meaning; the category is communicated through the frontmatter `category:` and `decision_type:` fields; CRs follow the `CR-WSF-NN.RevM` pattern anchored to the authorising ADR; the ADR README is restructured into five sections (Foundational, Implementation, Domain Extension, Governance, Convention).

This ADR is filed in the same PR as ADR-WSF-28. Both reach Baseline independently. The convention is in force from the moment of acceptance.

## 7. Required follow-on actions

The following actions are required at the next revision cycle. They are not part of this ADR's acceptance gate but are tracked as separate work items.

1. Restructure `wsf-governance/ADR/README.md` into five sections per §2.5.
2. Retro-fit the `category:` frontmatter field on pre-existing ADRs (ADR-WSF-01 through ADR-WSF-27).
3. Update the `templates/ADR-TEMPLATE.md` to include the new frontmatter fields.
4. Update the `templates/CR-TEMPLATE.md` to include the new frontmatter fields and the `CR-WSF-NN.RevM` naming instruction.

## 8. References

- ADR-WSF-17 (Foundational Semantic Architecture): establishes the tier discipline that this ADR's category field draws on.
- ADR-WSF-20 (Concept Definition Model): establishes the frontmatter schema that this ADR extends.
- ADR-WSF-28 (paired submission): the first domain-extension ADR, demonstrating the convention in its first use.
- The existing `CR-WSF-17-Rev.1-Establish-WSF-Product-Foundation.md`: the precedent for the `CR-WSF-NN.RevM` pattern.

---

*This ADR establishes the Domain-Extension Numbering and Categorisation Convention. The convention is in force from the moment of acceptance.*
