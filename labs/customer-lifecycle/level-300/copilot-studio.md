# Level 300 Lab: Copilot Studio (30 Minutes)

## Goal
Build/configure the Level 300 Copilot Studio workshop artifact, then produce required baseline outputs: at-risk VIP/Gold identification, plain-language explanations, recommended actions, and portfolio summary metrics.

## Required Inputs
- `data/Zava Sales Data - FY2024-2026.xlsx`
- `data/customer-lifecycle/derived-fields.md`
- `common/customer-lifecycle/signal-dictionary.md`
- `common/customer-lifecycle/risk-rules.md`
- `labs/customer-lifecycle/level-300/output-contract.md`

## Step-by-Step (Navigate / Click / Type)
1. Open Copilot Studio and select environment.
   - **Navigate:** Go to `https://copilotstudio.preview.microsoft.com/`.
   - **Click:** Select your workshop environment.
   - **Verify:** Copilot Studio home is visible.

2. Create or open a Level 300 workshop copilot artifact.
   - **Click:** New copilot (or open facilitator-provided draft for editing).
   - **Type:** Name `Customer Lifecycle L300 Baseline`.
   - **Click:** Create/Open.
   - **Verify:** Copilot build canvas is editable.

3. Configure baseline instruction contract before conversation testing.
   - **Click:** Instructions / System behavior panel.
   - **Type:** Add instruction text that enforces:
     1. use workshop dataset + derived fields only,
     2. classify `at_risk` only when `negative_signal_count >= 2`,
     3. keep 1-signal customers as `watch`,
     4. return business-language explanations and human actions.
   - **Click:** Save.
   - **Verify:** Instruction panel shows saved rule language.

4. Configure required output shape for Level 300 responses.
   - **Click:** Topics/Prompt behavior (or equivalent response settings).
   - **Type:** Require fields for at-risk outputs: `customer_id`, `tier`, `triggered_signals`, `negative_signal_count`, explanation, recommended_action.
   - **Click:** Save.
   - **Verify:** Output expectations are part of configured artifact.

5. Create a fresh test conversation from configured artifact.
   - **Navigate:** Open test chat panel.
   - **Click:** New conversation / Reset.
   - **Type:** `Start Level 300 customer lifecycle analysis for VIP and Gold tiers only.`
   - **Click:** Send.

6. Confirm configured rule is active.
   - **Type:** `Confirm the risk gate exactly: at_risk only when negative_signal_count >= 2; watch when =1; healthy when =0.`
   - **Click:** Send.
   - **Verify:** Assistant echoes exact 0/1/2+ contract.

7. Request at-risk VIP/Gold identification.
   - **Type:** `List all customers where tier is VIP or Gold and risk_status is at_risk. Include customer_id, tier, triggered_signals, and negative_signal_count. Exclude any record with negative_signal_count < 2.`
   - **Click:** Send.
   - **Verify:** Every returned at-risk customer has `negative_signal_count >= 2`.

8. Request plain-language explanations and mapped actions.
   - **Type:** `For each listed at-risk VIP/Gold customer, provide a plain business explanation of risk drivers and one recommended human action with a short justification.`
   - **Click:** Send.
   - **Verify:** Each customer has readable explanation and one concrete action.

9. Request mandatory portfolio summary metrics.
   - **Type:** `Provide a portfolio summary table with tier counts, at-risk counts, and at-risk percentage by tier for VIP, Gold, Silver, and Bronze.`
   - **Click:** Send.
   - **Verify:** All three metrics are present for each tier.

10. Run boundary check for 0/1/2/3+ signals.
    - **Type:** `Show one example each for customers with 0, 1, 2, and 3+ negative signals and confirm risk_status for each example according to the 2+ rule.`
    - **Click:** Send.
    - **Verify:** 0=healthy, 1=watch, 2+=at_risk.

11. Save Level 300 evidence.
    - **Click:** Export/copy configured instruction screenshot plus conversation outputs.
    - **Type:** Save notes with sections: Build/config checkpoints, At-risk list, explanations/actions, portfolio summary, boundary check.
    - **Verify:** Evidence includes both build/configuration and required Level 300 outputs from `output-contract.md`.

## Timebox Guidance
1. **0-10 min:** Build/configure copilot artifact and instruction contract.
2. **10-20 min:** Run at-risk listing plus explanations/actions.
3. **20-27 min:** Produce portfolio summary.
4. **27-30 min:** Run boundary check and save evidence.

## Guardrails
- Level 300 requires build/configuration before prompt execution (not conversation-only use of prebuilt flow).
- Use only workshop-provided inputs.
- Never label 0/1-signal customers as at-risk.
- Keep language business-friendly.
