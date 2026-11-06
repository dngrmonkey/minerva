# MINERVA Handoff Record

**Date:** 2026-11-05  
**Prepared By:** Daedalus  
**Project:** Minerva  
**Current Phase:** Shared Architecture Approved → Core Platform & Capability Architecture  
**Active Artifact:** 03 — Minerva Core Platform & Capability Architecture (next architecture artifact)

## Frozen / Approved Dependencies

- 01 — Minerva Product Vision
- 02 — Minerva Shared Architecture
- Canonical Project State Contract
- Specialist Interface Contract
- Orchestration Contract
- Shared UX Behavior Contract
- State-to-UX Mapping Contract
- Unified group-chat UX with controlled specialist participation
- Progressive left frame with Project Guide, Specialist Activity, and Context & Inputs
- Standalone application boundary: Minerva is intended to run in its own dedicated application window and ultimately as a standalone app independent of host AI chat products

## Completed Work and Decisions

- Reconfirmed that the existing visual UX direction is valid but insufficient by itself to begin prototype implementation.
- Decided the first prototype must be subject-agnostic; Tutor.com is a validation/regression case, not the architectural basis.
- Identified a material missing layer between Shared Architecture and prototype implementation: the Minerva Core Platform & Capability Architecture.
- Established that Minerva must gather and maintain enough shared project truth before specialist selection to determine required capabilities rather than route only by requested artifact type.
- Established that specialist selection must become capability-based rather than hard-coded to broad labels such as video, presentation, or self-paced learning.
- Established the need for a standard Specialist Framework that future specialists must implement.
- Established the need for a Capability Manifest/Registry so Minerva can understand current specialist abilities.
- Established that a specialist may gain new capability when a new engine/workflow is added beneath it, without requiring Minerva core routing logic to be rewritten.
- Clarified the specialist/engine hierarchy: Minerva reasons primarily at the specialist-capability level; specialists select their internal production engine/workflow.
- Confirmed planned ecosystem extensibility beyond CALLIOPE and GALATEA, including PRAXIS next and possible future specialists such as a handout/document specialist (working name MUSE).
- Confirmed that multi-specialist group interaction behavior still requires formalization beyond the existing visual concept.

## Unresolved / Not Yet Frozen

- Exact initial Minerva opening conversation.
- Exact minimum/required pre-routing shared project truth fields and readiness threshold.
- Specialist Framework schema.
- Capability Manifest/Registry schema.
- Capability matching/routing rules.
- Engine capability inheritance model.
- Specialist registration/discovery behavior.
- Cross-specialist dependency and conflict behavior.
- Direct user address of a specialist inside the unified conversation.
- Generic prototype scenario/content.
- Implementation architecture and technology stack.

## Validation / Approval / Freeze Status

- Product Vision: Defined
- Shared Architecture: Approved baseline
- Standalone application boundary: Approved architectural constraint
- Core Platform & Capability Architecture: Not yet defined
- Prototype validation: Deferred
- Implementation architecture: Not started

## Changed Files

- `architecture/02-shared-architecture.md` — updated current status, subject-agnostic prototype constraint, standalone application boundary, and next action
- `README.md` — updated phase, current handoff, and next action
- `handoffs/2026-11-05-core-platform-capability-direction-handoff.md` — created

## Exact Next Action

Define **03 — Minerva Core Platform & Capability Architecture** with these required sections:

1. Project Bootstrap / initial Minerva conversation model
2. Pre-routing Shared Project Truth and readiness threshold
3. Specialist Framework
4. Capability Manifest and Capability Registry
5. Specialist vs production-engine hierarchy
6. Engine-to-specialist capability inheritance/update behavior
7. Capability-based specialist selection and routing
8. Multi-specialist group-conversation participation rules
9. Future-specialist registration/extensibility rules
10. Standalone application boundary implications

Do not begin prototype implementation until this architecture is defined and approved. Tutor.com should be retained as a later validation case, not used to define the platform model.
