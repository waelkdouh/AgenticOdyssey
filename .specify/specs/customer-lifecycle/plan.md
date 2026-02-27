# Implementation Plan: VIP Customer Lifecycle Workshop Scenario

## Technical Scope
- Target areas (impacted paths):
  - `README.md` — keep as workshop Getting Started entry point with TOC and top-level phase flow.
  - `labs/customer-lifecycle/level-300/` — required baseline learner flows and deliverables:
    - `copilot-studio.md` (explicit build/configure + prompt execution; click-by-click navigate/click/type),
    - `foundry.md`,
    - `agent-framework.md` (explicit build/configure alert workflow + proactive alert demo),
    - `output-contract.md`.
  - `labs/customer-lifecycle/level-400/extensions.md` — optional after-class complexity extensions only.
  - `docs/customer-lifecycle/learner-guide.md` — learner-facing baseline guidance and level boundaries.
  - `docs/customer-lifecycle/facilitator-guide.md` — instructor timing, rubric, and scope-control guidance.
  - `common/customer-lifecycle/` — shared logic and terminology:
    - `signal-dictionary.md`,
    - `risk-rules.md` (2+ negative signals),
    - `action-mapping.md`.
  - `.specify/specs/customer-lifecycle/` — keep spec/plan/tasks/traceability/validation aligned.
- Integration points:
  - `data/Zava Sales Data - FY2024-2026.xlsx` and `narrative.md` as canonical scenario inputs.
  - `.specify/memory/constitution.md` principles: lab-first clarity, minimal disruption, verification required, documentation parity.

## Design Decisions
- Preserve the current level model and pass/fail boundary:
  - **Level 300** remains the required workshop baseline.
  - **Level 400** remains optional complexity only and does not affect Level 300 completion.
- Implement FR-006 as **build/configure work**, not conversation-only execution:
  - Copilot Studio baseline requires learners to build/configure the conversational experience before running insight prompts.
  - Agent Framework baseline requires learners to build/configure alert workflow behavior before running proactive alert demonstrations.
- Enforce FR-012 scope policy explicitly:
  - If in-class time is constrained, move non-essential enhancements to `labs/customer-lifecycle/level-400/extensions.md` as after-class work.
  - Do not delete deferred content; preserve it as documented Level 400 extensions.
  - Do not cut required Level 300 build/configuration steps from in-class flow.
- Keep output and logic requirements unchanged for baseline consistency:
  - Level 300 must still deliver at-risk VIP/Gold identification, plain-language explanation, recommended action, and portfolio summary (tier counts, at-risk counts, at-risk % by tier).
  - At-risk rule remains 2+ negative lifecycle signals.

## Risks and Mitigations
- Risk: FR-006 is interpreted as “run prompts only” without required setup.
  - Mitigation: mark explicit build/configure checkpoints in `copilot-studio.md` and `agent-framework.md`, and mirror those checkpoints in learner/facilitator docs.
- Risk: time pressure removes baseline steps instead of deferring enhancements.
  - Mitigation: codify FR-012 scope-cut rule in facilitator guidance and require explicit “moved to Level 400” notation for every deferred item.
- Risk: Level 300 vs Level 400 boundary drifts across files.
  - Mitigation: maintain one consistent boundary statement in README, learner guide, facilitator guide, and Level 400 extensions page.
- Risk: lab updates and docs diverge.
  - Mitigation: run documentation parity validation as a release gate before signoff.

## Validation Plan
- [ ] **FR-006 lab build/config validation (Copilot Studio)**: Verify `labs/customer-lifecycle/level-300/copilot-studio.md` includes explicit baseline steps to build/configure the Copilot Studio experience (navigate/click/type), then run insight prompts.
- [ ] **FR-006 lab build/config validation (Agent Framework)**: Verify `labs/customer-lifecycle/level-300/agent-framework.md` includes explicit baseline steps to build/configure the Agent Framework alert workflow, then run proactive alert demonstrations.
- [ ] **FR-006 documentation parity validation**: Verify `README.md`, `docs/customer-lifecycle/learner-guide.md`, and `docs/customer-lifecycle/facilitator-guide.md` all explicitly state that Copilot Studio and Agent Framework require build/configuration in Level 300 (not conversation-only use).
- [ ] **FR-012 scope-cut policy validation**: Verify facilitator and learner docs state that non-essential cuts move to Level 400 after-class extensions and are not deleted; confirm `labs/customer-lifecycle/level-400/extensions.md` is the receiving path.
- [ ] **Level model validation**: Verify Level 300 baseline + Level 400 optional complexity language is present and consistent across impacted paths, with Level 300 as the only completion baseline.
- [ ] **Baseline output validation**: Run Level 300 flow and confirm required outputs: at-risk VIP/Gold identification, plain-language explanation, recommended action, and portfolio summary (tier counts, at-risk counts, at-risk % by tier).
- [ ] **Risk-rule validation**: Validate 0/1/2/3+ negative signal examples and confirm only customers with 2+ negative signals are labeled at-risk.
- [ ] **Timebox rehearsal**: Confirm baseline can be delivered within workshop constraints (Copilot Studio ≤30 min, Foundry ≤60 min, Agent Framework ≤10 min).

## Rollout Notes
- Implement in two passes to reduce disruption:
  - Pass 1: lock Level 300 baseline build/config requirements and update README + learner/facilitator docs.
  - Pass 2: refine and expand Level 400 after-class extensions without changing Level 300 pass/fail.
- Keep changes additive and backward-compatible with current repository paths and existing lab assets.
- Require explicit communication to instructors: scope cuts are deferrals to Level 400, not deletions from the learning pathway.
