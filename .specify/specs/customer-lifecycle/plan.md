# Implementation Plan: VIP Customer Lifecycle Workshop Scenario

## Technical Scope
- Target areas (impacted paths):
  - `README.md` (Getting Started TOC + phase flow clarity).
  - `labs/customer-lifecycle/level-300/`:
    - `copilot-studio.md` (explicit build/configure baseline steps),
    - `foundry.md` (four-agent workflow, recency-threshold alert rule, New Foundry navigation assumptions),
    - `agent-framework.md` (explicit build/configure proactive alert flow),
    - `output-contract.md` (Level 300 required outputs).
  - `labs/customer-lifecycle/level-400/extensions.md` (optional complexity only).
  - `common/customer-lifecycle/`:
    - `risk-rules.md` (2+ negative signals gate + documented VIP recency threshold),
    - `signal-dictionary.md`,
    - `action-mapping.md`.
  - `docs/customer-lifecycle/` (learner/facilitator parity for level boundaries, scope cuts, and navigation assumptions).
  - `.specify/specs/customer-lifecycle/` (spec/plan/tasks consistency).
- Integration points:
  - Canonical internal inputs: `data/Zava Sales Data - FY2024-2026.xlsx`, `narrative.md`.
  - Explicit FR-014 exception input: synthetic news dataset (`synthetic_regional_news_24m`) for Agent 4 only.
  - Constitution alignment: lab-first clarity, minimal disruption, verification required, documentation parity.

## Design Decisions
- Keep **Level 300** as the only completion baseline; keep **Level 400** strictly optional extensions.
- Treat Copilot Studio and Agent Framework as required **build/configure** experiences (not prompt-only demos).
- Preserve Foundry as a **four-agent workflow**:
  1. RFM computation,
  2. tier + simple health indicators,
  3. VIP alert rule using **documented recency threshold**,
  4. news-based short-term action evaluation.
- Formalize the VIP alert condition as: `tier='VIP' AND recency > <documented_threshold>` and keep at-risk classification gated by `2+` negative signals.
- Keep synthetic news guidance learner-visible and bounded to the **most recent 24 months**, with regional events and fictional company references (e.g., Contoso).
- Carry forward New Foundry portal assumptions already implemented in `labs/customer-lifecycle/level-300/foundry.md` (New Foundry toggle on; project API keys disabled).

## Risks and Mitigations
- Risk: “high recency” remains ambiguous and causes inconsistent Agent 3 outputs.
  - Mitigation: define one numeric recency threshold in `common/customer-lifecycle/risk-rules.md` and reference it from `foundry.md`.
- Risk: Agent 4 synthetic-news input drifts outside FR-014 constraints.
  - Mitigation: enforce schema + 24-month window checks in Foundry lab validation steps.
- Risk: learners skip required setup and run only prebuilt artifacts.
  - Mitigation: require explicit navigate/click/type build-config checkpoints in Copilot Studio and Agent Framework docs.
- Risk: tenant-specific portal/auth assumptions are missed.
  - Mitigation: keep front-loaded verification steps in `foundry.md` and mirror them in facilitator guidance.

## Validation Plan
- [ ] Verify `labs/customer-lifecycle/level-300/foundry.md` still contains New Foundry navigation + auth assumptions (toggle enabled, no Project API keys).
- [ ] Verify Foundry instructions explicitly describe all four agents and expected handoff outputs.
- [ ] Verify `common/customer-lifecycle/risk-rules.md` documents a concrete VIP recency threshold and `foundry.md` references the same threshold text.
- [ ] Run sample records for 0/1/2/3+ negative-signal cases and confirm only `2+` is `at_risk`.
- [ ] Validate Agent 4 input is synthetic, learner-visible, includes regional events + fictional company references, and is constrained to last 24 months.
- [ ] Rehearse Level 300 baseline outputs end-to-end: at-risk VIP/Gold list, plain-language explanation, recommended action, and portfolio summary.
- [ ] Confirm Level 400 items remain optional-only and scope cuts are moved to `labs/customer-lifecycle/level-400/extensions.md`, not removed.

## Rollout Notes
- Apply changes additively to existing lab/docs structure; avoid disruptive restructuring.
- Update shared rule/docs first (`common/` + `labs/.../foundry.md`), then align README and facilitator/learner docs for parity.
- Communicate one rule to instructors: Level 300 is required baseline; defer extras to Level 400.
