# Level 300 Lab: Agent Framework (10 Minutes)

## Goal
Build/configure a Level 300 Agent Framework alert workflow and run proactive, explain-only alerts for at-risk VIP/Gold customers using outputs from Foundry.

## Inputs
- Level 300 scoring outputs from Foundry lab
- `common/customer-lifecycle/risk-rules.md`
- `common/customer-lifecycle/action-mapping.md`

## Step-by-Step (Navigate / Click / Type)
1. Open Agent Framework workspace.
   - **Navigate:** Open the environment where workshop workflows are created.
   - **Click:** Create new workflow (or open editable workshop draft).
   - **Type:** Name `vip-gold-risk-alerts-l300`.
   - **Verify:** Workflow canvas is visible and editable.

2. Configure workflow input schema.
   - **Click:** Add input dataset / connector.
   - **Type:** Bind the Foundry customer-level output for Level 300.
   - **Click:** Map fields `customer_id`, `tier`, `triggered_signals`, `negative_signal_count`, `risk_status`.
   - **Click:** Save input mapping.
   - **Verify:** Schema preview shows mapped fields.

3. Build trigger gating logic (required baseline config).
   - **Click:** Add trigger/filter node.
   - **Type:** Configure rule `tier in (VIP, Gold) AND negative_signal_count >= 2 AND risk_status = at_risk`.
   - **Click:** Save trigger settings.
   - **Verify:** One-signal (`watch`) and zero-signal (`healthy`) rows are excluded.

4. Build alert payload template.
   - **Click:** Add message/template node.
   - **Type:** Include sections for:
     1. customer ID and tier,
     2. triggered negative signals,
     3. plain-language risk explanation,
     4. recommended human action bundle.
   - **Click:** Set delivery mode to explain-only (no autonomous outreach).
   - **Click:** Save template.
   - **Verify:** Template contains all required sections and explain-only mode.

5. Configure run path and publish draft.
   - **Click:** Connect input -> trigger -> alert template nodes.
   - **Click:** Validate workflow.
   - **Click:** Save/Publish draft.
   - **Verify:** Validation passes with no blocking errors.

6. Execute proactive alert test run.
   - **Click:** Run test / simulate workflow.
   - **Type:** Use current Level 300 dataset snapshot.
   - **Click:** Execute.
   - **Verify:** Alerts are generated only for at-risk VIP/Gold customers.

7. Validate Level 300 contract alignment.
   - **Click:** Review run outputs.
   - **Verify:** No autonomous action is performed (explain-only alerts).
   - **Verify:** No 0/1-signal customer is alerted as at-risk.
   - **Verify:** Output aligns to `labs/customer-lifecycle/level-300/output-contract.md`.

8. Save evidence for facilitator.
   - **Click:** Export/copy workflow configuration summary and run output.
   - **Type:** Record final check: `L300 complete; L400 not required for pass/fail.`

## Timebox Guidance
1. **0-3 min:** Build workflow shell and input mapping.
2. **3-7 min:** Configure trigger and alert template.
3. **7-10 min:** Execute test run, validate gating, save evidence.

## Baseline Constraints
- Level 300 requires workflow build/configuration before demo execution (not conversation-only use of prebuilt flow).
- Alerts are explain-only (no autonomous customer contact).
- One-signal customers stay in watch status; no at-risk alert.
- Level 300 completion is sufficient for pass/fail; L400 is optional.
