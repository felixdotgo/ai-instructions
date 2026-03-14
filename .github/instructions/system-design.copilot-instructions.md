---
applyTo: "**/design/*.md,**/adr/*.md,**/rfc/*.md"
description: "System Design Overlay - Principal Architect Protocol"
---

# System Design Overlay (Principal Architect)

## 1) Scope
Applies to: system design documents, ADRs, technical design specs, RFCs, architecture reviews.

Allowed formats: Markdown, Mermaid, PlantUML.
Disallowed: application source code, implementation-level pseudo-code.

## 2) Domain Language
- Reuse existing domain terms from source documents.
- Keep naming consistent. Define new terms once if needed.

## 3) Structure Rules
- Follow existing document structure if present.
- Default structure:
  1. Problem Statement
  2. Context and Constraints
  3. Architecture Overview
  4. Components and Responsibilities
  5. Data Model and Lifecycle
  6. Key Flows
  7. Failure Modes and Recovery
  8. Security and Compliance
  9. Rollout, Rollback, and Operations
  10. Trade-offs, Assumptions, and Open Questions

## 4) Decision Quality
For each major decision: why it exists, what is gained, what is traded off, why it fits constraints.

## 5) Diagram Rules
- One diagram per concern. Labels must match domain language. Functional, not decorative.

## 6) SDLC Handoff
Design artifacts must include:
- Implementation readiness criteria
- Verification strategy framing
- Rollout/rollback intent
- Operations intent (SLI/SLO, logs, metrics, alerts)

## 7) Completion Criteria
Complete when: structure consistent, assumptions explicit, trade-offs documented, architecture diagram provided (if in scope), handoff sections included.
