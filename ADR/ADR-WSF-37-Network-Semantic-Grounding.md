# ADR-WSF-37 ; Network Semantic Grounding ; Tier 3 Baseline

**Status:** Baseline
**Date:** 2026-09-27
**Deciders:** eaojnr
**Phase:** Tier 3 ; Foundational (with `Specialization` uses)
**Authority:** WSF

## 1. Context

The Recon-ES-007 (Network Foundational Dependency Question, filed 2026-09-27) established the case that Network is a distinct foundational boundary from System (bounded-identity) and Ecosystem (context-sharing-emergent). Network has connection-identity: its being is defined by the topology of links and nodes, not by a single bounded whole.

This filing is governed by the WSF Semantic Status Model and Change Control Lifecycle.

## 2. Canonical Definition

A Network is a structural topology of interconnected entities, nodes, and links whose identity is defined by the connection structure. Networks are characterized by:

- nodes (endpoints participating in connections)
- links (the connections between nodes)
- topology (the structural pattern of nodes and links)
- identity by structure (changing the structure changes the network)

## 3. Boundary

Network is NOT reducible to:

- System (which has a bounded identity and single-purpose behavior)
- Ecosystem (which has a shared context and produces emergent outcomes)
- Relationship (which is a single link between two entities, not a topology)

Network IS distinct from System by:

- System: bounded-identity ; Network: connection-identity
- System: has a single boundary ; Network: has nodes and links as identity

Network IS distinct from Ecosystem by:

- Ecosystem: shared-context + emergent outcome ; Network: pure connection topology
- Ecosystem: members can have different roles ; Network: nodes are interchangeable positions in topology

## 4. Specialization Discipline

Any specialization of Network MUST reference wsf:Network as the parent. Per the Foundational Dependency Gate (D-004), no specialization can redefine the parent.

## 5. AI Boundary

Network does not require AI. An AI network is a Network with AI nodes/links, not a different concept.

## 6. Resolution Path

The Agentic Network and Autonomous Network candidates (CR-ES-022 section 4) gate on this ADR landing at Baseline.

## Baseline Promotion Metadata

- promotion_date: 2026-09-27
- promotion_trigger: wsf-spec PR #2 MERGED (; enables ES-034 integration pair)
- prior_status: Proposed
- final_status: Baseline
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
