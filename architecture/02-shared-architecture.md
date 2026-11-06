# 02 — Minerva Shared Architecture

## Status

**Approved architectural baseline — 2026-11-04**

This artifact defines the shared Minerva architecture that sits between the Product Vision and implementation/prototyping. It consolidates the approved project-state, specialist-interface, orchestration, UX-behavior, and state-to-UX contracts.

The governing architectural principle is:

> **Minerva owns canonical shared project state and project-level orchestration. Specialists own domain-specific state and production behavior. Production engines own no durable project truth. Conversation is the human interface, not the authoritative database.**

---

## 1. System Roles and Authority

### Minerva owns

- canonical shared project state;
- project identity and project-level status;
- initial discovery and minimum reliable context;
- specialist recommendation and activation;
- orchestration and next-action determination;
- cross-specialist continuity;
- shared UX shell and status language;
- shared requirements and quality expectations;
- project-level issue, decision, and dependency tracking;
- project completion readiness.

### Specialists own

Specialists such as CALLIOPE, GALATEA, and PRAXIS own their domain-specific state, workflow, artifacts, and production decisions within the assignment Minerva gives them.

### Production engines own

Production engines execute specialist work. They do not become authorities for shared project state.

### Client owns

The client retains authority over consequential judgment, required deliverables, major project changes, and final acceptance.

---

# 2. Canonical Project State Contract

Minerva maintains one authoritative project record. Conversation, UI components, specialists, and engines do not maintain competing copies of shared truth.

## Project identity

Minimum project-level identity includes:

- project ID;
- project name;
- created/updated timestamps;
- project status;
- active conversational/orchestration lead;
- participating specialists.

## Shared project truth

Shared state is grouped conceptually into:

### Intent

- need;
- subject/content;
- audience;
- objective;
- intended outcome.

### Requirements

- project requirements;
- accessibility requirements;
- branding requirements;
- policy requirements;
- delivery requirements;
- platform requirements.

### Sources and evidence

Source records preserve traceability, authority, availability, and validation status.

### Assets

Assets remain distinct from sources. Asset records preserve type, purpose, location/reference, authenticity/currentness, required-for relationship, and availability status.

### Deliverables

A project may contain multiple deliverables. Deliverables record type, responsible specialist, purpose, audience, status, artifact reference, and version.

### Orchestration state

Minerva tracks:

- active lead;
- participating specialists;
- current project stage;
- next action;
- pending decisions;
- open issues;
- warnings;
- blockers.

### Specialist state

Each specialist has its own namespace/state and does not duplicate shared project truth.

## State-change rule

Specialists may directly change their own domain state. Changes to shared project truth are proposed to Minerva and resolved according to ownership and judgment requirements.

## Conversation rule

Conversation generates state changes but is not authoritative state.

A project must be resumable from canonical state without rereading the entire conversation.

## History

Meaningful state changes should preserve actor, field, previous value, new value, reason, and timestamp so that state remains auditable and recoverable.

---

# 3. Specialist Interface Contract

Every specialist must support four responsibilities:

1. **Receive**
2. **Operate**
3. **Report**
4. **Return**

## Specialist manifest

A specialist should expose durable metadata including:

- specialist ID;
- display name;
- domain;
- capabilities;
- supported deliverables;
- version.

## Context intake

Minerva provides specialists only the project context relevant to their assignment, including applicable intent, audience, objective, requirements, sources, assets, requested deliverables, decisions, and reusable prior outputs.

The user should not need to repeat information already held in canonical project state.

## Read authority

A specialist may read:

- relevant shared project truth;
- applicable requirements;
- applicable sources and assets;
- relevant project decisions;
- explicitly exposed outputs from other specialists;
- its own specialist state.

A specialist does not automatically receive another specialist's complete internal state.

## Write authority

A specialist may write its own:

- workflow state;
- domain artifacts;
- recommendations;
- output metadata;
- status.

Shared project changes are proposed back to Minerva.

## Common lifecycle

The shared lifecycle should distinguish at least:

- available;
- activated;
- working;
- waiting;
- ready for review;
- complete;
- paused;
- failed.

This lifecycle is separate from a specialist's own internal production stages.

## Progress reporting

Every specialist should expose a small common progress envelope:

- current stage;
- next action;
- progress state;
- open requirements;
- warnings;
- blockers;
- review state;
- human-readable status.

## Questions and decisions

Questions should be classifiable as clarification, decision, approval, missing information, missing asset, or preference.

Consequential decisions should produce structured decision records rather than live only in chat history.

## Artifacts

Meaningful specialist outputs should be registered as artifacts with identity, type, owner, title, version, status, location/reference, and source dependencies.

Artifact status is separate from specialist lifecycle.

## Cross-specialist reuse

Specialists expose reusable outputs through stable interfaces. Another specialist consumes approved exposed outputs rather than depending on hidden conversation history or another specialist's full internal state.

## Completion

A specialist completion response should report:

- status;
- completed work;
- produced artifacts;
- approved outputs;
- remaining issues;
- unresolved decisions;
- recommended next actions;
- recommended specialists when applicable.

---

# 4. Orchestration Contract

Minerva directs project-level flow across discovery, specialists, decisions, artifacts, dependencies, and completion.

## Entry modes

### Minerva entry

The user begins with Minerva and Minerva establishes enough shared truth to make the next reliable decision.

### Direct specialist entry

The user may explicitly request a specialist. Minerva still establishes the project shell and canonical project state.

## Minimum Reliable Context

Discovery stops when Minerva has enough reliable context to make the next appropriate project decision. It should not ask questions merely because an intake field is empty.

Project knowledge should be distinguishable as:

- known;
- inferred;
- unknown;
- required now;
- required later.

## Decision cycle

Minerva repeatedly:

**Observe State → Determine Next Need → Choose Actor → Act / Ask / Delegate → Receive Result → Update State → Re-evaluate**

## Next action

Minerva maintains one primary project-level next action.

Secondary tasks and pending items may exist, but the system should always know what most directly moves the project forward.

## Specialist recommendation and activation

Recommendation is separate from activation.

For V1, adding a specialist requires explicit client approval unless the client already requested that specialist or the transition is purely operational and already authorized.

Activation includes context packaging, specialist acknowledgement, state update, and visible participation.

## Active lead vs participating specialists

Only one participant should normally lead the conversation at a time.

Multiple specialists may participate in the project simultaneously.

This distinguishes:

- orchestration/conversation lead;
- visible participants;
- specialists actively working.

## Judgment boundary

The governing rule is:

> **Automate operational decisions; escalate judgment decisions.**

## Blockers and parallel work

A dependency may block the current stage, a later stage, or only one specialist.

If one workstream is waiting and another can continue, Minerva may recommend moving the active lead rather than idling the entire project.

## Re-entry

A specialist can be reactivated and should receive its prior state plus relevant shared-state changes and reusable outputs created since it last worked.

## Revision routing

Revisions should be routed to the smallest appropriate owner and layer.

Changes to canonical shared truth trigger impact evaluation rather than automatic invalidation of all downstream work.

## Completion

Minerva marks a project ready for completion only when required deliverables, reviews, quality gates, decisions, blockers, and specialist work are reconciled.

Final acceptance remains a client decision.

---

# 5. Shared UX Behavior Contract

## Governing UX model

Minerva is a single coordinated workspace, not a set of disconnected specialist applications.

The approved UX direction is:

> **A unified group-chat style conversation with controlled specialist participation and a progressively opening left-side project frame.**

## Primary screen model

The V1 shell uses two primary frames:

### Left Frame — Project Guide

A structured, progressive, collapsible project-state frame.

### Main Frame — Conversation + Active Work

The shared conversation and contextual work surface.

A permanent third frame is not part of the V1 baseline.

## Progressive left frame

The left frame should begin collapsed, minimal, or lightly populated and become more useful as reliable project context emerges.

It contains three primary zones:

### Project Guide

Shows:

- current project stage;
- completed stages with checkmarks;
- active stage;
- pending stages;
- blockers or review state when meaningful;
- next meaningful step.

### Specialist Activity

Shows:

- participating specialist;
- current focus;
- human-readable status;
- meaningful waiting/blocker/review state.

### Context & Inputs

Shows confirmed and currently relevant:

- sources;
- uploaded assets;
- audience;
- objective/goal;
- intended deliverables;
- important accepted decisions.

The panel is not a raw data dump.

## Unified conversation

The main stream may contain:

- user messages;
- Minerva coordination messages;
- specialist contribution messages;
- invocation events;
- decision events;
- artifact events;
- blocker/warning events when user-visible action is warranted.

## Specialist appearance rule

A specialist appears directly in the conversation stream only when it:

1. returns a meaningful contribution;
2. asks a necessary question;
3. requests approval or a decision;
4. reports a blocker;
5. delivers an artifact or recommendation.

Routine work remains visible through Specialist Activity or is summarized by Minerva.

## Minerva synthesis

Minerva acts as the conductor and synthesizer. After multiple specialist contributions or meaningful stage changes, Minerva should recompose the results into a clear project-level understanding and next action.

## Visual identity

Specialists may have distinct icons, accent colors, message treatments, and status indicators while remaining inside the same Minerva shell.

The experience should feel like:

> **Different expert, same workspace.**

Underlying AI/model/provider identity remains hidden.

---

# 6. State-to-UX Mapping Contract

The UI renders canonical or specialist-reported meaning through a UX interpretation layer.

**State → UX Interpretation → Visible Interface**

## Project Guide

Project-level state maps to:

- not started → pending;
- active → highlighted;
- complete → checkmark;
- blocked → blocked treatment;
- ready for review → review treatment;
- intentionally unnecessary → skipped/not required.

A stage receives a checkmark only when its completion rule is satisfied, not merely because conversation moved on.

## Specialist Activity

Specialists become visible when invoked, actively working, waiting, producing relevant work, or otherwise participating.

Raw internal stage names should map to human-readable status labels.

## Context & Inputs

Confirmed reliable context appears here.

Speculative, rejected, superseded, or purely internal data does not appear as current context.

If a confirmed value changes, the live panel shows only the current value; history remains in state history.

## Decisions

Active user decisions appear prominently in conversation.

Settled decisions may remain in Context & Inputs only when they materially affect future work.

## Invocation

When Minerva activates one or more specialists, the UI may show one grouped invocation event rather than multiple redundant starting messages.

Invocation animation/status does not remain active indefinitely; ongoing work moves to Specialist Activity.

## Artifacts

Artifacts become visible when they require review, represent meaningful completed work, are delivered, or are reused across specialists.

Routine machine/intermediate files remain hidden.

## Blockers and warnings

A blocker is surfaced in both project/specialist state and conversation only when user action or orientation requires it.

Warnings and dependencies needed later should remain quieter and should not interrupt unrelated current work.

## Work Surface

A structured Work Surface appears when an artifact is better reviewed or manipulated outside ordinary chat, such as a storyboard, slide structure, module map, video preview, or artifact review.

Conversation remains accessible and the user stays inside the Minerva shell.

## Resume

Reopening a project should reconstruct orientation from state:

- current stage;
- active lead;
- participating specialists;
- important context;
- outstanding decision/blocker;
- next action.

The system should not require replaying conversation history to resume correctly.

---

# 7. V1 Prototype Baseline

The first interaction prototype should validate this sequence:

1. Minerva opens a blank/minimal workspace.
2. User provides an instructional need and sources.
3. Minerva conducts targeted discovery.
4. Reliable context begins populating Context & Inputs.
5. Project Guide opens progressively.
6. Minerva recommends/invokes appropriate specialists.
7. Specialist Activity shows quiet ongoing work.
8. Specialists appear in the conversation only for meaningful contributions or needs.
9. Minerva synthesizes results and establishes the next project step.
10. A meaningful artifact becomes available.
11. The Work Surface opens for artifact review.
12. Review state and Project Guide update from the same underlying project state.

The prototype must remain subject-agnostic. The Tutor.com counselor-training concept may be used only as a validation/regression case after the generic interaction model is defined.

---

# 8. Architectural Boundaries Not Yet Frozen

The following remain implementation/design decisions rather than approved architecture:

- exact layout dimensions;
- exact colors and gradients;
- typography;
- animation timing;
- precise navigation placement;
- exact tool-switcher design;
- exact visual component library;
- exact stage names for every specialist;
- storage technology;
- database technology;
- frontend framework;
- backend framework;
- provider/model selection;
- production-engine implementation.

### Standalone application boundary

Minerva is intended to run in its own dedicated application window and ultimately as a standalone application. The UX, project state, orchestration model, and specialist interfaces must remain independent of ChatGPT, Claude, or any other host AI chat product. AI providers and production engines are implementation services behind the Minerva application boundary.

The approved architecture defines behavior and authority, not final visual styling or technology selection.

---

# 9. Current Architectural Status

**Product Vision:** Defined  
**Shared Architecture:** Approved baseline  
**Implementation architecture:** Not yet defined  
**Core Platform & Capability Architecture:** Required next  
**Prototype:** Deferred until Core Platform & Capability Architecture is defined

A material architectural gap was identified before prototype work: Minerva still needs a subject-agnostic bootstrap model, an explicit pre-routing shared-truth model, a durable specialist framework, a capability registry, engine-to-specialist capability inheritance, extensibility rules for future specialists, and formal multi-specialist participation behavior.

The Tutor.com project remains a validation case rather than the prototype's architectural basis.

**Exact next action:**

> Define **03 — Minerva Core Platform & Capability Architecture** covering Project Bootstrap, pre-routing Shared Project Truth, Specialist Framework, Capability Manifest/Registry, specialist-vs-engine hierarchy, engine capability inheritance, capability-based routing, multi-specialist conversation rules, standalone application boundary implications, and extensibility rules for future specialists.
