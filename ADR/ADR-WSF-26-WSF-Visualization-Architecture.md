# ADR-WSF-26 : WSF Visualization Architecture

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-23 ; Semantic Representation Architecture
Related: ADR-WSF-02, ADR-WSF-12, ADR-WSF-19, ADR-WSF-23, ADR-WSF-24, ADR-WSF-25
Decision Type: Foundational Visualization Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **WSF Visualization Architecture** that governs how foundational semantic constructs (concepts, relationships, assertions, identities) are rendered as visual artefacts for human understanding, analysis, and communication.

The governing principle is:

> **Visualization makes meaning perceivable ; it does not add new meaning.**

The WSF Visualization Architecture therefore:

- Defines canonical visualization types for semantic content ;
- Establishes visual encoding principles for semantic primitives ;
- Specifies rendering targets (web, print, embedded, interactive) ;
- Supports both static and interactive visualizations ;
- Maintains semantic accuracy across visual representations ;
- Provides accessibility compliance.

---

## 2. Why This Decision Is Necessary

The architecture addresses four irreducible requirements:

1. **Human comprehension** : semantic content must be perceivable by humans for review, analysis, and decision-making.
2. **Communication** : visualizations enable sharing semantic understanding across audiences.
3. **Navigation** : large semantic graphs require visual navigation aids.
4. **Accessibility** : visualizations must be perceivable by people with diverse abilities.

Without a governed visualization architecture:

- Visualization quality varies wildly across consumers ;
- Semantic information is lost or distorted in rendering ;
- Accessibility is inconsistent or absent ;
- Visualization tooling cannot interoperate.

---

## 3. Decision Drivers

The WSF Visualization Architecture addresses:

- Semantic accuracy in visual encoding ;
- Interactive exploration of large graphs ;
- Static and dynamic rendering ;
- Multiple output formats (SVG, PNG, PDF, HTML) ;
- Responsive design for various screen sizes ;
- Accessibility (WCAG 2.1 AA compliance) ;
- Performance for large semantic graphs ;
- Customisable visual encodings ;
- Export and embedding ;
- Integration with documentation portals.

---

## 4. Visualization Categories

The architecture defines seven visualization categories:

### 1. Concept Diagrams

Render concept definitions as visual cards or nodes:

- Concept name and identity ;
- Definition text ;
- Key attributes ;
- Parent/child relationships ;
- Cross-references.

### 2. Relationship Graphs

Render relationship networks:

- Nodes represent concepts ;
- Edges represent relationship types ;
- Edge labels show relationship names ;
- Layout algorithms (force-directed, hierarchical, circular) ;
- Filtering and focus modes.

### 3. Hierarchy Trees

Render inheritance and specialisation structures:

- Parent-child relationships ;
- Multiple inheritance support ;
- Collapsible and expandable ;
- Indication of inheritance depth.

### 4. Assertion Maps

Render assertion sets with provenance:

- Subjects and objects as nodes ;
- Relationships as edges ;
- Evidence as attached annotations ;
- Lifecycle state indication ;
- Temporal ordering.

### 5. Lifecycle Timelines

Render semantic evolution over time:

- Concept introduction dates ;
- Version markers ;
- Deprecation events ;
- Retirement events.

### 6. Provenance Chains

Render audit trails:

- Attribution metadata ;
- Action sequences ;
- Source references ;
- Time-stamped events.

### 7. Domain Maps

Render specialised domains:

- Subgraphs for enterprise, technical, operational views ;
- Layered rendering (foundation → specialisation) ;
- Cross-domain bridges.

---

## 5. Visual Encoding Principles

The architecture establishes encoding rules:

### Encoding Rule 1 : Concept Visual Identity

Each concept has a canonical visual representation:

- **Shape** : distinguishes concept type (entity, capability, event, etc.) ;
- **Colour** : distinguishes semantic domain ;
- **Size** : encodes usage frequency or importance ;
- **Border** : indicates lifecycle state (draft, baseline, deprecated).

### Encoding Rule 2 : Relationship Visual Encoding

Each relationship has a canonical visual representation:

- **Line style** : distinguishes relationship type (inheritance, composition, assertion) ;
- **Direction** : arrow indicates source-to-target direction ;
- **Colour** : distinguishes relationship category ;
- **Width** : encodes assertion strength or cardinality.

### Encoding Rule 3 : Semantic Fidelity

Visual encodings SHALL preserve semantic distinctions:

- Distinct concepts SHALL have visually distinguishable representations ;
- Distinct relationship types SHALL have visually distinguishable encodings ;
- Semantic hierarchies SHALL be visually evident through spatial layout.

### Encoding Rule 4 : No Information Loss

Visualisations SHALL NOT introduce semantic distortions:

- All concepts in the source SHALL be representable ;
- All relationships SHALL be representable ;
- No semantic content SHALL be silently dropped.

---

## 6. Rendering Targets

The architecture supports multiple rendering targets:

### Web (Interactive)

- HTML5 + SVG ;
- D3.js or vis.js for interaction ;
- Real-time updates via WebSocket ;
- Pan, zoom, focus, filter ;
- Tooltip details on hover.

### Web (Static)

- Pre-rendered SVG or PNG ;
- Suitable for documentation ;
- CDN-friendly ;
- Print-compatible.

### Print

- High-resolution PDF ;
- Multi-page layouts ;
- Vector graphics for clarity ;
- A4, Letter, A3 formats.

### Embedded

- Inline SVG for Markdown documentation ;
- Mermaid syntax for GitHub rendering ;
- Compact for inline use.

### Mobile

- Responsive layouts ;
- Touch-optimised interactions ;
- Reduced complexity for small screens ;
- Offline-capable.

---

## 7. Rendering Pipeline

The architecture defines a three-stage rendering pipeline:

### Stage 1 : Semantic Extraction

Extract semantic content from WSF:

- Query WSF for concepts, relationships, assertions ;
- Apply scope filters (subgraph selection) ;
- Apply temporal filters (point-in-time view) ;
- Resolve cross-references.

### Stage 2 : Layout Computation

Compute visual layout:

- Apply layout algorithm (force-directed, hierarchical, etc.) ;
- Compute node positions ;
- Compute edge routes ;
- Apply visual encodings ;
- Handle overflow and collision.

### Stage 3 : Rendering

Produce final output:

- Generate SVG / PNG / PDF ;
- Apply styling per theme ;
- Embed interactivity (for interactive targets) ;
- Validate against accessibility checks.

---

## 8. Layout Algorithms

The architecture supports:

### Force-Directed Layout

For relationship graphs:

- Spring forces between connected nodes ;
- Repulsion forces between all nodes ;
- Centering force ;
- Suitable for general-purpose exploration.

### Hierarchical Layout

For inheritance trees:

- Top-down or left-right orientation ;
- Sugiyama-style layered approach ;
- Suitable for ontology hierarchies.

### Circular Layout

For cyclic structures:

- Nodes on circle perimeter ;
- Edges as chords or arcs ;
- Suitable for federation views.

### Grid Layout

For concept grids:

- Concepts in rows/columns ;
- Grouped by domain or type ;
- Suitable for catalog views.

### Radial Layout

For star-shaped structures:

- Central concept ;
- Radial positioning of related concepts ;
- Suitable for focused exploration.

---

## 9. Themes and Styling

The architecture supports themed rendering:

### Default Theme

- Light background, dark foreground ;
- Semantic colour palette per concept type ;
- Standard typography (sans-serif body, monospace for identifiers).

### Dark Theme

- Dark background, light foreground ;
- Adjusted colour palette for contrast ;
- Suitable for low-light environments.

### Print Theme

- High-contrast for print ;
- Optimised for paper rendering ;
- Vector graphics only.

### High-Contrast Theme

- WCAG AAA compliance ;
- Suitable for accessibility ;
- Minimal visual noise.

### Custom Themes

- Organisation-specific branding ;
- Domain-specific colour coding ;
- Configurable typography.

---

## 10. Accessibility

The architecture enforces WCAG 2.1 AA compliance:

### Perceivable

- Colour is not the sole information carrier (shape, position supplement) ;
- Contrast ratio ≥ 4.5:1 for text ;
- Text alternatives for non-text content ;
- Resizable up to 200% without loss.

### Operable

- Keyboard navigation for interactive elements ;
- Sufficient time for time-based interactions ;
- No seizure-inducing flashing ;
- Clear focus indicators.

### Understandable

- Consistent navigation ;
- Predictable behaviour ;
- Input assistance for forms.

### Robust

- Compatible with assistive technologies ;
- Valid markup ;
- Status messages for dynamic content.

---

## 11. Interactive Features

Interactive visualisations support:

### Navigation

- Pan and zoom ;
- Focus mode (highlight neighbourhood) ;
- Breadcrumb navigation ;
- Mini-map for orientation.

### Filtering

- By concept type ;
- By relationship type ;
- By lifecycle state ;
- By domain or namespace.

### Search

- Full-text search across concepts ;
- Identifier-based search ;
- Faceted search by attributes.

### Detail View

- Click-to-inspect concept details ;
- Tooltips on hover ;
- Side panels for context ;
- Drill-down navigation.

### Comparison

- Side-by-side comparison ;
- Diff visualisation between versions ;
- Highlight differences.

### Export

- SVG, PNG, PDF export ;
- Embed code (iframe, image) ;
- URL with view state preserved.

---

## 12. Performance

Visualization performance characteristics:

- **Rendering latency** : <500ms for graphs up to 1K nodes ;
- **Interaction latency** : <100ms for pan, zoom, focus ;
- **Initial load** : <2s for standard visualisations ;
- **Memory footprint** : <100MB for 10K-node graphs.

Performance degrades gracefully for larger graphs:

- Progressive loading ;
- Level-of-detail rendering ;
- Sampling for very large graphs.

---

## 13. Integration with Documentation

Visualizations integrate with documentation:

### Inline Embedding

- Markdown image syntax ;
- Mermaid syntax for GitHub-rendered diagrams ;
- SVG embed with fallback PNG.

### Documentation Portal

- Auto-generated concept diagrams ;
- Interactive graphs in portal pages ;
- Diagram versioning with documentation.

### Linkage

- Diagrams link to concept pages ;
- Concept pages link to diagrams ;
- Bidirectional navigation.

---

## 14. Tool Ecosystem

The architecture supports:

### WSF Renderer

Canonical renderer implementing the rendering pipeline.

### WSF Layout Engine

Pluggable layout algorithm implementations.

### WSF Theme Pack

Pre-built themes for common use cases.

### WSF Accessibility Toolkit

Tools for accessibility validation and remediation.

### WSF Embed Library

JavaScript library for embedding interactive visualisations.

---

## 15. Implementation Implications

The architecture requires:

- **Canonical renderer** : open-source reference implementation ;
- **Layout library** : multiple layout algorithms ;
- **Theme repository** : curated theme collection ;
- **Accessibility validator** : automated WCAG checking ;
- **Documentation integration** : Markdown/Mermaid export ;
- **Performance benchmarks** : continuous benchmarking ;
- **Test suite** : visual regression testing.

---

## 16. Consequences

### Positive

- Consistent visual quality across consumers ;
- Semantic accuracy preserved in rendering ;
- Accessibility compliance ;
- Performance at scale ;
- Tool ecosystem support.

### Negative

- Multiple visualisation categories increase complexity ;
- Layout algorithm selection requires expertise ;
- Accessibility tooling requires ongoing maintenance ;
- Performance tuning needed for large graphs.

---

## 17. Rejected Alternatives

### A : Free-Form Visualisation

Allow consumers to define any visualisation. Rejected because:

- Causes semantic inconsistencies ;
- Limits accessibility guarantees ;
- Reduces tool ecosystem value.

### B : Static Images Only

Restrict to static image output. Rejected because:

- Limits interactive exploration ;
- Excludes real-time use cases ;
- Reduces documentation value.

### C : SVG Only

Restrict to SVG output. Rejected because:

- Limits print use cases ;
- Reduces compatibility ;
- Excludes raster rendering needs.

### D : No Accessibility Requirements

Skip accessibility compliance. Rejected because:

- Excludes users with disabilities ;
- Limits adoption in regulated sectors ;
- Reduces universal usability.

### E : Implicit Performance Targets

Leave performance as implementation-defined. Rejected because:

- Causes inconsistent user experience ;
- Limits large-graph usability ;
- Reduces predictability.

---

## 18. Explicit Non-Decisions

This ADR does NOT decide:

- Specific visualisation library defaults ;
- Particular layout algorithm preferences ;
- Cloud-hosted vs self-hosted rendering ;
- Specific theme vendor partnerships ;
- 3D rendering extensions ;
- Animation framework choices.

These decisions belong to deployment-specific CRs and operational policies.

---

## 19. Decision Summary

The World Semantic Foundation establishes a WSF Visualization Architecture that:

- Defines seven canonical visualisation categories ;
- Establishes visual encoding principles preserving semantic accuracy ;
- Supports web, print, embedded, and mobile rendering ;
- Defines a three-stage rendering pipeline ;
- Provides multiple layout algorithms for different graph structures ;
- Supports themed rendering for varied contexts ;
- Enforces WCAG 2.1 AA accessibility compliance ;
- Enables interactive exploration at scale.

---

## 20. Required Follow-On ADRs

The implementation of this ADR requires:

- ADR-WSF-27 : WSF Digital Twin and Simulation Architecture (defines simulation-specific visualisation patterns)

---

*Status: Baseline. Parent: ADR-WSF-23.*