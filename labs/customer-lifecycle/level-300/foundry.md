# Level 300 Lab: Microsoft Foundry (60 Minutes)

## Goal
Build a four-agent Foundry workflow that turns raw sales data into business-ready lifecycle guidance:
1. Agent 1: Compute RFM (Recency, Frequency, Monetary),
2. Agent 2: Compute tiers + simple health indicators,
3. Agent 3: Apply rule `tier='VIP' AND recency_days > 60`,
4. Agent 4: Evaluate short-term actions using synthetic regional news signals.

## Why this lab matters (Story Arc Mapping)
| Story arc outcome | Foundry multi-agent output |
|---|---|
| Identify who needs attention now | Agent 3 alert table for VIP high-recency risk |
| Explain why risk is emerging | Agent 1 + Agent 2 scoring features and health signals |
| Recommend next human step | Agent 4 short-term action justification |
| Leadership visibility | Portfolio summary (tier counts, at-risk counts, at-risk % by tier) |

## Required Inputs
- `data/Zava Sales Data - FY2024-2026.xlsx`
- `data/customer-lifecycle/derived-fields.md`
- `common/customer-lifecycle/signal-dictionary.md`
- `common/customer-lifecycle/risk-rules.md`
- `labs/customer-lifecycle/level-300/output-contract.md`

## Portal Assumptions (Tenant-Specific)
- Use the **New Foundry** portal experience for this lab (turn on the New Foundry toggle in the UI).
- **Project API key authentication is disabled** in this tenant; use signed-in user/project access only.
- Navigation path assumptions:
  - Optional project creation: **Start building -> Design workflow**.
  - Data ingestion: **Build -> Data**.
  - Agent authoring/orchestration: **Build -> Workflows**.

## Synthetic News Guidance (for Agent 4)
- Use synthetic dataset **`synthetic_regional_news_24m`** covering the **most recent 24 months** only.
- Include regional events such as:
  - natural disasters,
  - major public events that may increase short-term demand,
  - supply disruptions affecting operations.
- Include fictional company references (for example: Contoso, Fabrikam, Northwind) in some events.
- Minimum recommended fields per news event:
  - `event_id`, `region`, `event_date`, `event_type`, `severity`,
  - `demand_signal` (`increase` or `decrease`),
  - `affected_companies`,
  - `event_summary`.
- Correlation guidance: compare customer behavior windows before/after events (for example 30 days pre vs 30 days post) to justify tactical actions.
- Exception handling rules:
  - Missing `region` -> `exception_missing_region` (exclude from correlation),
  - Non-fictional company references -> `exception_non_fictional_company` (exclude),
  - Malformed `event_date` -> `exception_malformed_date` (exclude),
  - Event outside last 24 months -> `exception_stale_record` (exclude).

## Step-by-Step (Navigate / Click / Type)
1. Open Foundry and enable New Foundry experience.
   - **Navigate:** Go to `https://ai.azure.com`.
   - **Type:** Log in with your tenant credentials.
   - **Click:** Turn on the **New Foundry** toggle in the page header (if not already on).
   - **Verify:** New Foundry layout is active.

2. (Optional) Create a new workshop project if one does not already exist.
   - **Click:** **Start building** -> **Design workflow**.
   - **Click:** Create project (if prompted).
   - **Type:** Name `customer-lifecycle-l300`.
   - **Click:** Create and open project.
   - **Verify:** Project opens successfully.

3. Open project and confirm authentication model.
   - **Click:** Open the workshop project (existing or newly created).
   - **Verify:** You can access project resources with signed-in user access.
   - **Verify:** Do **not** configure Project API keys (disabled in this tenant).

4. Create/open the workflow artifact.
    - **Click:** **Build** -> **Workflows**.
    - **Click:** Create new workflow artifact.
    - **Type:** Name `level-300-foundry-multi-agent`.
    - **Verify:** Workflow artifact is editable and runnable.

5. Ingest canonical sales source data.
    - **Click:** **Build** -> **Data**.
    - **Click:** Upload/Add data.
    - **Type/Select:** `data/Zava Sales Data - FY2024-2026.xlsx`.
    - **Click:** Confirm upload.
    - **Verify:** Dataset is available in project assets.

6. Create synthetic news source with exception-ready schema.
    - **Click:** **Build** -> **Data**.
    - **Click:** Create new table/dataset.
    - **Type:** Name `synthetic_regional_news_24m`.
    - **Type:** Add fields `event_id`, `region`, `event_date`, `event_type`, `severity`, `demand_signal`, `affected_companies`, `event_summary`.
    - **Type:** Add synthetic rows limited to last 24 months, including regional events and fictional companies.
    - **Verify:** Dataset exists and includes both increase/decrease demand examples.

7. Return to workflow authoring for multi-agent flow.
    - **Click:** **Build** -> **Workflows**.
    - **Click:** Open `level-300-foundry-multi-agent`.
    - **Verify:** Workflow can access both uploaded datasets.

8. Build Agent 1 (RFM).
    - **Type:** Implement Recency, Frequency, Monetary calculations from source data.
    - **Click:** Run Agent 1 transform.
    - **Type:** Save output as `agent1_rfm`.
    - **Verify:** `recency_days`, `frequency_90d`, `monetary_90d` fields exist.

9. Build Agent 2 (tiers + simple health indicators).
    - **Type:** Use RFM output to derive tiers (VIP/Gold/Silver/Bronze) and simple health indicators.
    - **Type:** Calculate `negative_signal_count`, `triggered_signals`, and `risk_status` (0=healthy, 1=watch, 2+=at_risk).
    - **Click:** Run Agent 2 transform.
    - **Type:** Save output as `agent2_tier_health`.
    - **Verify:** Tier, signal, and risk-status fields are populated.

10. Build Agent 3 (VIP recency threshold alert).
    - **Type:** Apply canonical rule `tier='VIP' AND recency_days > 60`.
    - **Type:** Add evidence fields `vip_recency_threshold_days` (=60) and `agent3_rule_text` (`tier='VIP' AND recency_days > 60`).
    - **Type:** Keep baseline risk gate aligned with `common/customer-lifecycle/risk-rules.md` (`2+` negative signals => `at_risk`).
    - **Click:** Run Agent 3 logic.
    - **Type:** Save output as `agent3_vip_recency_alerts`.
    - **Verify:** Alert rows are explainable, rule-driven, and include threshold evidence fields.

11. Build Agent 4 (synthetic-news scope enforcement).
    - **Type:** Validate `synthetic_regional_news_24m` rows before join:
      - flag missing region as `exception_missing_region`,
      - flag non-fictional company references as `exception_non_fictional_company`,
      - flag malformed dates as `exception_malformed_date`,
      - flag stale/out-of-window rows as `exception_stale_record`.
    - **Type:** Exclude exception rows from event correlation pipeline.
    - **Verify:** Only in-scope rows continue to action evaluation.

12. Build Agent 4 (news-based short-term action evaluation).
     - **Click:** **Build** -> **Workflows**.
     - **Type:** Join customer/region/time context with validated synthetic news events.
     - **Type:** Generate short-term action rationale (for example outreach, promotion, retention focus) based on internal + external signal alignment.
     - **Click:** Run Agent 4 logic.
     - **Type:** Save output as `agent4_news_action_eval`.
     - **Verify:** Each recommended action includes event-based justification plus `event_scope_status`.

13. Verify inter-agent handoff chain.
    - **Verify:** `agent1_rfm` -> `agent2_tier_health` -> `agent3_vip_recency_alerts` -> `agent4_news_action_eval`.
    - **Verify:** Each downstream agent references required upstream artifact fields.

14. Produce required Level 300 outputs.
     - **Type:** Compile final outputs:
       - at-risk VIP/Gold list,
       - explanation fields,
       - recommended actions,
       - portfolio summary (tier counts, at-risk counts, at-risk % by tier).
     - **Click:** Run and save final table(s).
     - **Verify:** Output matches `labs/customer-lifecycle/level-300/output-contract.md`.

15. Validate rule boundaries and agent coherence.
     - **Type:** Pull samples for 0/1/2/3+ negative-signal scenarios.
     - **Click:** Confirm status mapping (`0=healthy`, `1=watch`, `2+=at_risk`).
     - **Click:** Confirm Agent 3 rule text matches exactly `tier='VIP' AND recency_days > 60`.
     - **Click:** Spot-check at least 2 records where Agent 4 adds external context to justify short-term action.
     - **Verify:** Multi-agent outputs remain consistent with baseline rule contract.

16. Save outputs for downstream Agent Framework lab.
    - **Click:** Persist/export `agent2_tier_health`, `agent3_vip_recency_alerts`, and final output table.
    - **Verify:** Outputs are ready for `labs/customer-lifecycle/level-300/agent-framework.md`.

## Timebox Guidance
1. **0-10 min:** Ingest source + create orchestration artifact.
2. **10-25 min:** Build Agent 1 and Agent 2.
3. **25-35 min:** Build Agent 3 rule output.
4. **35-50 min:** Build synthetic news dataset + Agent 4 evaluation.
5. **50-60 min:** Final output assembly + boundary validation.

## Scope-Cut Rule
If time runs short, keep Agents 1-3 and baseline outputs in class, then move deeper Agent 4 expansion to `labs/customer-lifecycle/level-400/extensions.md` (do not delete).
