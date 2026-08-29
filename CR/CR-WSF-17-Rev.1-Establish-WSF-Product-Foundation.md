Amendment to preserve original CR’s intent while expanding it from repository establishment into the establishment of the complete WSF Product Foundation.

Below is the formal revised version.

CR-WSF-17 Rev. 1 ; Establish WSF Product Foundation

Status: Baseline
Revision: 1
Type: Foundational Program Implementation
Implements: ADR-WSF-17 ; Foundational Semantic Architecture
Target Organization: World-Semantic-Foundation
Supersedes: CR-WSF-17
Scope: World Semantic Foundation inception, semantic assets, executable platform, integration, visualization, and real-world realization

⸻

1. Change Request

Establish the initial implementation of the World Semantic Foundation (WSF) as a complete, governed, versioned, authoritative and usable semantic foundation.

WSF shall be implemented as more than a conceptual ontology or documentation repository.

The WSF Product Foundation shall provide six mutually reinforcing capabilities:

1. Semantic Foundation
2. Knowledge Assets
3. Semantic Engine
4. Integration
5. Visualization
6. Realization

supported by:

7. Governance

The implementation shall establish the GitHub organization structure, repositories, documentation, normative semantic assets, machine-readable specifications, deployable software foundation, integration mechanisms, visualization assets, examples, and governance mechanisms required to evolve WSF into a practical semantic platform.

The implementation shall proceed incrementally.

It shall not attempt to finalize the entire world semantic model or implement every possible semantic capability in the initial release.

⸻

2. Motivation

The WSF investigation established that a useful semantic foundation must bridge four normally separated concerns:

Meaning
     ↓
Representation
     ↓
Execution
     ↓
Application

A semantic foundation that exists only as documentation is difficult to operationalize.

A software platform without authoritative semantics risks encoding arbitrary or inconsistent meanings.

A machine-readable ontology without explanatory material limits human understanding and adoption.

A semantic model without practical realization does not demonstrate its utility.

WSF therefore adopts an integrated product approach.

The objective is to establish a semantic foundation that can be:

understood
referenced
implemented
queried
validated
integrated
visualized
simulated
instantiated
extended

and ultimately applied to real-world entities, systems, organizations, processes, events and digital twins.

⸻

3. Architectural Decision Implemented

This CR implements:

ADR-WSF-17 ; Foundational Semantic Architecture

WSF shall establish a deliberately constrained foundational semantic architecture rather than a flat terminology catalogue or an unrestricted universal taxonomy.

The initial architectural foundation recognizes the following semantic domains:

Existence
Occurrence
Condition
Disposition
Relation
Identity
Semantics
Proposition
Assertion
Qualification
Temporality
Spatiality
Epistemics

Initial foundational semantic candidates are:

Entity
Concept
Relationship
Event
State
Disposition
Proposition
Assertion
Identity
Context
Time
Space

Supporting constructs include:

Identifier
Reference
Namespace
Term
Definition
Validity
Evidence
Provenance
Authority

Derived concepts shall be introduced through explicit specialization and governance.

⸻

4. WSF Product Foundation

The implementation shall establish WSF as a seven-part product architecture.

                         WSF
                          │
        ┌─────────────────┼─────────────────┐
        ▼                 ▼                 ▼
   SEMANTIC          KNOWLEDGE         SEMANTIC
   FOUNDATION          ASSETS            ENGINE
        │                 │                 │
        └─────────────────┼─────────────────┘
                          │
                ┌─────────┴─────────┐
                ▼                   ▼
           INTEGRATION          VISUALIZATION
                │                   │
                └─────────┬─────────┘
                          ▼
                     REALIZATION
                          │
                          ▼
                     GOVERNANCE

These are not independent products.

They collectively form the WSF implementation.

⸻

5. Semantic Foundation

The Semantic Foundation is the authoritative semantic layer.

It shall contain:

* foundational concepts;
* definitions;
* semantic relationships;
* classifications;
* specializations;
* constraints;
* identity semantics;
* reference semantics;
* contextual semantics;
* temporal semantics;
* spatial semantics;
* assertion semantics;
* provenance semantics;
* conformance semantics.

The Semantic Foundation shall be the normative source from which machine-readable and executable representations are derived.

⸻

6. Knowledge Assets

WSF shall provide authoritative human-readable and referenceable knowledge assets.

These shall include:

Concept Definitions
Semantic Specifications
Research Records
Investigation Findings
Architectural Decisions
Change Requests
Design Rationales
Examples
Application Patterns
Implementation Guides
Conformance Guides
Visual Explanations

The documentation shall explain not only:

what WSF defines,

but also:

why it defines it this way.

The rationale and investigation history are therefore considered first-class program assets.

⸻

7. Executable Semantic Platform

WSF shall provide a deployable software implementation.

The initial platform shall establish the architecture for a WSF Semantic Engine.

Conceptually:

                  WSF SEMANTIC ENGINE
                           │
       ┌───────────────────┼───────────────────┐
       ▼                   ▼                   ▼
   Semantic Store     Semantic Services    API Layer
       │                   │                   │
       ├── Concepts        ├── Validation     ├── REST
       ├── Entities        ├── Resolution     ├── Graph
       ├── Relations       ├── Query          ├── Events
       ├── Assertions      ├── Reasoning      └── SDK
       ├── Context        └── Mapping
       └── Provenance

The initial implementation shall establish the extensible architecture rather than prematurely mandate a particular storage technology or reasoning engine.

⸻

8. Semantic Engine Capabilities

The platform shall be designed to support:

Create

Create semantic instances and assertions.

Identify

Assign and resolve semantic identities.

Reference

Resolve references across namespaces.

Describe

Represent entities, concepts, states and events.

Relate

Create and query semantic relationships.

Contextualize

Qualify semantics through context.

Validate

Validate semantic structures and assertions against WSF specifications.

Query

Retrieve semantic information through machine-accessible interfaces.

Reason

Support controlled semantic inference where explicitly supported by the semantic model.

Transform

Map between compatible semantic representations.

Import

Consume compatible external semantic/data representations.

Export

Produce interoperable representations.

Observe

Provide semantic state and event information for downstream applications.

⸻

9. Platform Neutrality

WSF shall remain technology-neutral at the semantic level.

The implementation may use technologies such as:

RDF
OWL
JSON-LD
Graph technologies
Relational technologies
REST
Event interfaces

where justified.

However:

Technology choices shall implement the semantic architecture; they shall not define the semantic architecture.

Technology selection shall therefore be handled through subsequent implementation ADRs.

⸻

10. Integration Foundation

WSF shall be designed for integration with both specialized and mainstream platforms.

The integration architecture shall support:

WSF
 │
 ├── OpenDEA
 ├── Enterprise Architecture Platforms
 ├── Knowledge Graph Platforms
 ├── Data Platforms
 ├── Modeling Tools
 ├── Digital Twin Platforms
 ├── Simulation Systems
 ├── AI/Agent Platforms
 └── Mainstream Enterprise Platforms

Integration shall occur through governed semantic interfaces rather than uncontrolled direct coupling.

⸻

11. OpenDEA Integration

OpenDEA shall consume and specialize WSF semantics.

The intended relationship is:

WSF
 │
 │ foundational semantics
 ▼
OpenDEA
 │
 │ enterprise architecture specialization
 ▼
Architecture Models

For example:

WSF Capability
      │
      ▼
OpenDEA Business Capability

OpenDEA remains an independently governed Enterprise Architecture system.

WSF shall not absorb OpenDEA’s enterprise architecture semantics.

⸻

12. Assessment-Models Boundary

The independent lifecycle of Assessment-Models shall be preserved.

Assessment-Models
       │
       │ governs maturity-model ecosystem
       ▼
Maturity Models
       │
       ▼
OpenDEA Maturity Assessment

The OpenDEA maturity assessment remains an OpenDEA-managed assessment instance.

Assessment-Models remains responsible for its maturity-model ecosystem and inter-model governance.

WSF shall not become the cardinal governance space for assessments.

⸻

13. Visualization Foundation

WSF shall establish a dedicated visual communication capability.

The objective is to make semantic structures understandable, referenceable and communicable.

Visual assets shall explain:

Why
What
How
Value

The visualization capability shall support:

Conceptual Diagrams

Representation of foundational semantic structures.

Semantic Maps

Relationships between concepts and semantic domains.

Architecture Diagrams

WSF and downstream specialization relationships.

Lifecycle Diagrams

Entity, event, state and transition behavior.

Causal Diagrams

Cause/effect and enabling relationships.

Comparative Diagrams

Contrasting conventional approaches with WSF-enabled approaches.

Application Diagrams

Digital twins, simulations, enterprise architecture and agentic applications.

⸻

14. Visual Asset Repository

A dedicated wsf-visuals repository shall provide:

Conceptual Visuals
Architecture Visuals
Semantic Maps
Reference Diagrams
Application Diagrams
Comparison Visuals
Illustration Sources
Rendering Specifications
Reusable Diagram Components

Where possible, diagrams should have machine-readable or reproducible source representations rather than only exported images.

The objective is to make visuals maintainable semantic assets.

⸻

15. Realization Foundation

WSF shall demonstrate semantic utility through executable and reference applications.

The initial realization program shall prioritize:

Entity Modeling
Digital Twin Modeling
Simulation
State/Event Modeling
Capability Modeling
Semantic Query
Semantic Validation

The purpose is to demonstrate that WSF semantics can describe not merely abstract concepts but actual modeled entities and their changing conditions.

⸻

16. Digital Twin Application

WSF shall support semantic representation of digital twins.

The foundational pattern is:

Entity Type
      │
      ▼
Entity Instance
      │
      ├── Identity
      ├── State
      ├── Events
      ├── Relationships
      ├── Capabilities
      ├── Context
      ├── Time
      └── Space

For example:

Entity Type:
Data Center
Entity Instance:
OTCHERE DC-01

The model may subsequently represent:

OTCHERE DC-01
    │
    ├── State
    ├── Equipment
    ├── Location
    ├── Capabilities
    ├── Events
    └── Relationships

This demonstrates how WSF can provide semantic foundations for digital representations of real-world entities.

⸻

17. Simulation Application

WSF shall support semantic state transition patterns:

Initial State
      │
      ▼
Event / Action
      │
      ▼
Transition
      │
      ▼
Resulting State
      │
      ▼
Next Event

The distinction between:

Capability

and:

Actual Event

shall remain explicit.

A model may therefore ask:

What can this entity do?

without asserting:

What did this entity actually do?

This distinction is fundamental for simulation, autonomous systems and digital twins.

⸻

18. Reference Example Enterprise

All canonical WSF examples shall use:

OTCHERE Inc

or:

OTCHERE

as the example enterprise.

The canonical example individual shall be:

Kwesi

The example enterprise name ACME shall not be used in:

* documentation;
* specifications;
* diagrams;
* source code examples;
* test data;
* tutorials;
* simulations;
* digital twin examples;
* future WSF-derived examples.

This convention should also be respected in downstream work where WSF examples are reused.

⸻

19. Repository Architecture

The WSF GitHub organization shall initially establish:

World-Semantic-Foundation/
│
├── wsf
├── wsf-spec
├── wsf-governance
├── wsf-examples
├── wsf-software
├── wsf-connectors
├── wsf-visuals
└── wsf-docs

wsf

Canonical semantic assets.

wsf-spec

Normative semantic and conformance specifications.

wsf-governance

ADR, CR, governance, lifecycle and authority.

wsf-examples

Reference semantic applications.

wsf-software

Deployable WSF Semantic Engine and related software.

wsf-connectors

Integration adapters and semantic mappings.

wsf-visuals

Reproducible visual semantic assets.

wsf-docs

Human-readable conceptual and implementation documentation.

Repository names may be refined through implementation ADRs before creation.

⸻

20. Root README

The root WSF documentation shall explain:

1. WSF purpose;
2. WSF mission;
3. WSF scope;
4. WSF non-scope;
5. foundational semantic architecture;
6. design principles;
7. investigation history;
8. architectural decisions;
9. repository architecture;
10. semantic assets;
11. software platform;
12. integration;
13. visualization;
14. digital twin application;
15. simulation;
16. OpenDEA relationship;
17. Assessment-Models boundary;
18. governance;
19. contribution;
20. versioning;
21. conformance;
22. roadmap.

The README shall explicitly document the distinction between:

Finding
Decision
Implementation

⸻

21. Investigation Record

WSF shall preserve the research lineage leading to its architecture.

The initial research record shall include:

Capability:Ability:Capacity
Semantic Representation
Intent:Constraint:Commitment
Ontological Classification
Proposition:Assertion
Identity:Reference
Existence:Occurrence
Time:Space:Causality:Validity
Foundational Semantic Synthesis
WSF Product Architecture

Research records shall remain distinguishable from normative decisions.

⸻

22. Governance

The governance system shall manage:

Concept Lifecycle
Semantic Authority
ADR Lifecycle
CR Lifecycle
Versioning
Release Management
Contribution
Review
Conformance
Deprecation
Retirement

The lifecycle shall be:

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

No implementation shall be interpreted as automatically creating a normative semantic decision.

⸻

23. Semantic Lifecycle

The implementation shall support semantic status states including:

Candidate
Investigating
Proposed
Normative
Deprecated
Retired

The exact semantics and transition rules shall be established by a subsequent governance ADR.

⸻

24. Versioning

WSF shall distinguish:

Semantic Identity
Version
Validity
Lifecycle Status

A version change does not automatically imply a new semantic identity.

A fundamental semantic change may require a new identity.

Detailed compatibility and versioning policy shall be established by subsequent ADRs.

⸻

25. Conformance

WSF shall establish a formal concept of conformance.

A WSF implementation may ultimately be assessed against:

Semantic Conformance
Identity Conformance
Reference Conformance
Relationship Conformance
Assertion Conformance
Provenance Conformance
Specialization Conformance
API Conformance
Serialization Conformance

Detailed conformance requirements shall be established through subsequent ADRs.

⸻

26. Deliverables

CR-WSF-17 Rev. 1 shall produce the initial WSF Product Foundation comprising:

Organization

* WSF GitHub organization structure.

Repositories

* canonical semantic repository;
* specification repository;
* governance repository;
* examples repository;
* software repository;
* connectors repository;
* visualization repository;
* documentation repository.

Semantic Assets

* foundational semantic architecture;
* foundational concept catalogue;
* relationship foundation;
* identity/reference foundation;
* assertion foundation;
* contextual foundation;
* temporal/spatial foundation.

Human Assets

* comprehensive README;
* investigation record;
* design rationale;
* ADRs;
* CRs;
* guides;
* examples;
* explanatory diagrams.

Software Assets

* Semantic Engine architecture;
* initial deployable software foundation;
* API foundation;
* validation foundation;
* semantic query foundation.

Integration Assets

* integration architecture;
* OpenDEA integration strategy;
* mainstream platform integration strategy;
* connector architecture.

Visual Assets

* semantic diagrams;
* architecture diagrams;
* comparison diagrams;
* application diagrams;
* reproducible visual sources.

Realization Assets

* entity modeling example;
* digital twin example;
* state/event example;
* capability example;
* simulation example.

⸻

27. Acceptance Criteria

CR-WSF-17 Rev. 1 shall be considered complete when:

Semantic Foundation

* [ ]	Foundational semantic architecture is implemented.
* [ ]	Foundational concepts are explicitly classified.
* [ ]	Derived concepts are distinguished.
* [ ]	Capability:Ability:Capacity is represented through Disposition.
* [ ]	Identity and Reference are distinct.
* [ ]	Proposition and Assertion are distinct.
* [ ]	Truth and Validity are distinct.
* [ ]	Event and State are distinct.
* [ ]	Relationships are first-class.
* [ ]	Context, Time and Space are represented.

Human Assets

* [ ]	Rich root README exists.
* [ ]	Investigation history is preserved.
* [ ]	Design rationale is documented.
* [ ]	ADR/CR mechanisms exist.
* [ ]	Canonical examples exist.
* [ ]	Visual explanations exist.

Software

* [ ]	WSF Semantic Engine repository exists.
* [ ]	Software architecture is documented.
* [ ]	Initial deployable implementation exists.
* [ ]	Semantic API foundation exists.
* [ ]	Validation capability exists.
* [ ]	Semantic query capability exists.
* [ ]	Identity/reference mechanisms are represented in the software architecture.

Integration

* [ ]	OpenDEA integration architecture is documented.
* [ ]	Mainstream platform integration strategy is documented.
* [ ]	Connector architecture exists.
* [ ]	Semantic mappings can be represented.

Visualization

* [ ]	WSF visual asset repository exists.
* [ ]	Foundational architecture visuals exist.
* [ ]	Conceptual semantic visuals exist.
* [ ]	Application visuals exist.
* [ ]	Visual source artifacts are reproducible where practical.

Realization

* [ ]	Entity example exists.
* [ ]	Digital twin example exists.
* [ ]	Event/state example exists.
* [ ]	Capability example exists.
* [ ]	Simulation pattern exists.

Boundaries

* [ ]	OpenDEA remains independently governed.
* [ ]	Assessment-Models remains independently governed.
* [ ]	OpenDEA Maturity Assessment remains an OpenDEA-managed instance.
* [ ]	WSF does not become the assessment governance authority.

Example Convention

* [ ]	OTCHERE Inc is used as the canonical example enterprise.
* [ ]	Kwesi is used as the canonical example individual.
* [ ]	No new ACME references exist.

⸻

28. Explicit Non-Goals

This CR does not:

* attempt to model every possible world concept;
* establish a complete universal ontology;
* finalize every WSF concept;
* establish the complete ESS;
* establish the complete EO;
* modify OpenDEA governance;
* modify Assessment-Models governance;
* create a centralized assessment authority in WSF;
* mandate one ontology language;
* mandate one database technology;
* mandate one reasoning engine;
* mandate one visualization technology;
* finalize all API specifications;
* finalize all digital twin standards;
* finalize all simulation semantics.

Those matters remain subject to subsequent architectural decisions.

⸻

29. Success Condition

The success condition is not:

“WSF has repositories.”

The success condition is:

WSF exists as an authoritative, understandable, referenceable, machine-readable, executable and integrable semantic foundation that can be applied to real-world modeling and demonstrated through practical applications.

The WSF Product Foundation must allow a user to move through:

UNDERSTAND
     ↓
REFERENCE
     ↓
MODEL
     ↓
VALIDATE
     ↓
EXECUTE
     ↓
INTEGRATE
     ↓
VISUALIZE
     ↓
SIMULATE
     ↓
REALIZE

without leaving the semantic foundation behind.

⸻

30. Strategic Outcome

The implementation establishes WSF as a bridge between:

Ontology
      │
      ▼
Information Semantics
      │
      ▼
Enterprise Semantics
      │
      ▼
Executable Models
      │
      ▼
Digital Representations
      │
      ▼
Digital Twins / Simulation
      │
      ▼
Real-World Systems

This is the principal strategic outcome of CR-WSF-17 Rev. 1.

WSF therefore becomes not simply a repository of definitions, but a semantic foundation capable of supporting actual computational and organizational realization.

⸻

31. Subsequent Implementation Sequence

Following acceptance of this CR, implementation shall proceed through focused ADRs and CRs.

The immediate sequence should address:

ADR-WSF-18
Concept Identity
ADR-WSF-19
Semantic Relationship Model
ADR-WSF-20
Concept Definition Model
ADR-WSF-21
Namespace And Reference Model
ADR-WSF-22
Assertion And Provenance Model
ADR-WSF-23
Semantic Representation Architecture
ADR-WSF-24
WSF Software Architecture
ADR-WSF-25
WSF Integration Architecture
ADR-WSF-26
WSF Visualization Architecture
ADR-WSF-27
WSF Digital Twin And Simulation Architecture

The existing ADR register shall be reconciled before committing these identifiers to prevent numbering collisions.

Each ADR shall result in one or more traceable implementation CRs.

⸻

32. Traceability

The WSF implementation shall maintain explicit traceability:

Research
   │
   ▼
Finding
   │
   ▼
Synthesis
   │
   ▼
ADR
   │
   ▼
CR
   │
   ▼
Repository Artifact
   │
   ▼
Executable / Semantic Asset
   │
   ▼
Validation
   │
   ▼
Release

This traceability is itself a WSF governance asset.

It ensures that future users can understand not merely what exists, but why it exists, who decided it, what evidence informed it, how it was implemented, and how it may evolve.

⸻

33. Final Decision Boundary

CR-WSF-17 Rev. 1 establishes the implementation foundation, not the final WSF ontology.

It authorizes construction of the environment in which the authoritative semantic foundation can be developed safely.

The distinction is deliberate:

CR-WSF-17 Rev. 1
        │
        ▼
Build the WSF Foundation
        │
        ▼
Subsequent ADRs
        │
        ▼
Define the detailed semantics
        │
        ▼
Subsequent CRs
        │
        ▼
Implement the semantics

This preserves the program’s central discipline:

Investigate deeply, decide explicitly, implement traceably, demonstrate practically, and evolve under governance.

This revision is now sufficiently broad to represent the actual WSF program outcome rather than just its repository bootstrap. The next step should be the implementation decomposition of CR-WSF-17 Rev. 1:turning these deliverables into concrete GitHub repositories, directory trees, initial files, software components, visual asset conventions, and an ordered implementation backlog.