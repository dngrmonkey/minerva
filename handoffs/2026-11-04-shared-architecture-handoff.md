# MINERVA Handoff Record

**Date:** 2026-11-04  
**Prepared By:** Daedalus  
**Project:** Minerva  
**Current Phase:** Shared Architecture Approved → Interaction Prototype  
**Active Artifact:** 02 — Minerva Shared Architecture

## Frozen / Approved Dependencies

- 01 — Minerva Product Vision
- Canonical Project State Contract
- Specialist Interface Contract
- Orchestration Contract
- Shared UX Behavior Contract
- State-to-UX Mapping Contract

## Completed Work and Decisions

- Defined Minerva as the canonical owner of shared project state and project-level orchestration.
- Established that conversation is the human interface, not the authoritative project database.
- Established specialist-local state and specialist ownership of domain-specific production behavior.
- Established that production engines own no durable project truth.
- Defined the common specialist receive/operate/report/return interface.
- Defined Minerva's orchestration cycle, minimum reliable context, next-action authority, specialist activation, re-entry, revision routing, and completion behavior.
- Approved a unified group-chat style UX in which Minerva remains orchestration authority and specialists appear as controlled visible participants.
- Approved a progressively opening left frame with three primary zones: Project Guide, Specialist Activity, and Context & Inputs.
- Approved the specialist appearance rule: specialists speak directly in the stream only for meaningful contribution, necessary question, approval/decision request, blocker, or artifact/recommendation.
- Approved state-to-UX mapping rules for stage completion, specialist status, context, decisions, invocation, artifacts, blockers/warnings, Work Surface activation, and resume behavior.
- Decided not to add another abstract architecture contract before prototype validation.

## Unresolved / Not Yet Frozen

- exact visual dimensions;
- exact palette/gradient treatment;
- typography and animation timing;
- precise navigation/tool-switcher placement;
- exact specialist stage labels;
- implementation architecture;
- data/storage technology;
- frontend/backend stack;
- model/provider selection;
- production-engine implementation.

## Validation / Approval / Freeze Status

- Product Vision: Defined
- Shared Architecture: Approved baseline
- UX behavioral direction: Approved baseline
- State-to-UX mapping: Approved baseline
- Prototype validation: Not started
- Implementation architecture: Not started

## Changed Files

- `architecture/02-shared-architecture.md` — created
- `architecture/01-product-vision.md` — status pointer updated
- `README.md` — architecture index and current state updated
- `handoffs/2026-11-04-shared-architecture-handoff.md` — created

## Exact Next Action

Build the first low-fidelity Tutor.com Minerva interaction prototype covering:

**Entry → targeted discovery → progressive left-frame opening → context capture → specialist invocation → quiet specialist status → meaningful specialist contributions → Minerva synthesis → artifact/review transition.**

Do not expand the abstract architecture further unless prototype behavior exposes a material gap.
