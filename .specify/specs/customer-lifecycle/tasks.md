# Tasks: customer-lifecycle

## Phase 1 - Foundation
- [x] T001 Lock canonical level model and boundaries in `common/customer-lifecycle/signal-dictionary.md` so Level 300 remains required baseline and Level 400 remains optional extension path.
- [x] T002 Codify at-risk rule examples (0/1/2/3+ negative signals, with 2+ = at-risk) in `common/customer-lifecycle/risk-rules.md` for shared downstream consistency.
- [x] T003 Confirm Level 300 output contract in `labs/customer-lifecycle/level-300/output-contract.md` includes VIP/Gold at-risk identification, plain-language explanation, recommended action, and portfolio summary (tier counts, at-risk counts, at-risk % by tier).
- [x] T004 Add explicit scope-cut rule language to `docs/customer-lifecycle/facilitator-guide.md` and `docs/customer-lifecycle/learner-guide.md`: non-essential in-class cuts must be moved to `labs/customer-lifecycle/level-400/extensions.md` (after-class), never deleted.

## Phase 2 - Feature Delivery
- [x] T005 Update `README.md` Getting Started flow to preserve current path model (`level-300` baseline, `level-400` extensions) and call out baseline sequence: Copilot Studio -> Foundry -> Agent Framework.
- [x] T006 Rewrite `labs/customer-lifecycle/level-300/copilot-studio.md` with explicit numbered navigate/click/type **build/configure** steps for Copilot Studio artifacts before prompt execution (not conversation-only).
- [x] T007 Update `labs/customer-lifecycle/level-300/foundry.md` with explicit numbered navigate/click/type baseline steps aligned to Level 300 required outputs and timebox.
- [x] T008 Rewrite `labs/customer-lifecycle/level-300/agent-framework.md` with explicit numbered navigate/click/type **build/configure** steps for Agent Framework alert workflow artifacts before proactive alert demo (not conversation-only).
- [x] T009 Update `docs/customer-lifecycle/learner-guide.md` to mirror Level 300 build/config expectations for Copilot Studio and Agent Framework, plus deferral-to-Level-400 scope-cut policy.
- [x] T010 Update `docs/customer-lifecycle/facilitator-guide.md` rubric/timing guidance to enforce build/config checkpoints (Copilot Studio <=30m, Foundry <=60m, Agent Framework <=10m) and Level 300-only completion grading.
- [x] T011 Curate `labs/customer-lifecycle/level-400/extensions.md` as the receiving location for deferred non-essential items, explicitly labeled after-class optional extensions (no impact on Level 300 pass/fail).

## Phase 3 - Validation and Cleanup
- [x] T012 Update `.specify/specs/customer-lifecycle/validation.md` with FR-006 checks that `labs/customer-lifecycle/level-300/copilot-studio.md` and `labs/customer-lifecycle/level-300/agent-framework.md` each include concrete creation/configuration steps before execution steps.
- [x] T013 Execute and record "not conversation-only" validation across `labs/customer-lifecycle/level-300/copilot-studio.md`, `labs/customer-lifecycle/level-300/agent-framework.md`, `docs/customer-lifecycle/learner-guide.md`, and `docs/customer-lifecycle/facilitator-guide.md`.
- [x] T014 Execute and record FR-012 scope-cut validation across `docs/customer-lifecycle/learner-guide.md`, `docs/customer-lifecycle/facilitator-guide.md`, and `labs/customer-lifecycle/level-400/extensions.md`, confirming deferred items are moved to Level 400 rather than removed.
- [x] T015 Execute level-model parity validation across `README.md`, `docs/customer-lifecycle/learner-guide.md`, `docs/customer-lifecycle/facilitator-guide.md`, `labs/customer-lifecycle/level-300/*.md`, and `labs/customer-lifecycle/level-400/extensions.md` to confirm `level-300` baseline + `level-400` extension consistency.
- [x] T016 Execute baseline output/risk-rule validation against `labs/customer-lifecycle/level-300/output-contract.md`, `common/customer-lifecycle/risk-rules.md`, and facilitator scoring guidance; record evidence and remediation items in `.specify/specs/customer-lifecycle/validation.md`.
- [x] T017 Perform final documentation reconciliation across all impacted files and close traceability links in `.specify/specs/customer-lifecycle/traceability.md` and `.specify/specs/customer-lifecycle/tasks.md`.

## Dependency Notes
- T002 depends on T001.
- T003 depends on T001 and T002.
- T004 depends on T001.
- T005 depends on T001 and T004.
- T006 depends on T001 and T003.
- T007 depends on T001 and T003.
- T008 depends on T001 and T003.
- T009 depends on T005, T006, and T008.
- T010 depends on T004, T005, T006, T007, and T008.
- T011 depends on T004 and T010.
- T012 depends on T006 and T008.
- T013 depends on T009, T010, and T012.
- T014 depends on T004 and T011.
- T015 depends on T005 through T011.
- T016 depends on T002, T003, T007, T008, and T010.
- T017 depends on T013, T014, T015, and T016.
