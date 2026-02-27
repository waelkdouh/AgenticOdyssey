# Learner Guide: VIP Customer Lifecycle Scenario

## Learning Levels (Canonical)
- **L100 (foundational orientation):** Understand scenario context, data sources, and shared vocabulary. No pass/fail completion gate.
- **L200 (intermediate):** Build practical familiarity with tools, transformations, and terminology before baseline grading.
- **L300 (advanced hands-on baseline, WWL-aligned):** Advanced hands-on practice that builds on L100 and L200; this is the required workshop exercise level for completion/pass.
- **L400 (optional complexity):** Extension work that deepens L300 outcomes and is excluded from pass/fail.

## Level 300 Completion Criteria (Pass/Fail)
To pass the workshop baseline, you must deliver all four outputs:
1. At-risk VIP/Gold identification using the **2+ negative-signal rule**.
2. Plain-language explanation for each at-risk VIP/Gold customer.
3. Recommended human action for each at-risk VIP/Gold customer.
4. Portfolio summary with tier counts, at-risk counts, and at-risk % by tier.

Pass/fail boundary:
- **Pass requires L300 completion.**
- **L400 is optional and does not affect pass/fail.**

## Phase Outcomes
| Phase | Outcome artifact |
|---|---|
| Copilot Studio | Built/configured Copilot Studio baseline artifact + conversational at-risk explanation/action outputs |
| Foundry | Structured risk scoring table with 2+ signal rule |
| Agent Framework | Built/configured Agent Framework baseline alert workflow + proactive explain-only alerts |

## Run Sequence (Use This Order)
1. `labs/customer-lifecycle/level-300/copilot-studio.md`
2. `labs/customer-lifecycle/level-300/foundry.md`
3. `labs/customer-lifecycle/level-300/agent-framework.md`
4. Validate against `labs/customer-lifecycle/level-300/output-contract.md`

## Level 300 Build/Configure Checkpoints (Required)
- In Copilot Studio, you must **build/configure** the workshop copilot/topic instructions before running insight prompts.
- In Agent Framework, you must **build/configure** the workshop alert workflow (data binding, trigger gating, alert template) before running proactive alert demonstrations.
- Running conversations against prebuilt assets without completing baseline build/configuration does not satisfy Level 300 expectations.

## Baseline Rule You Must Follow
- Count negative lifecycle signals per customer.
- `2+` negative signals => `at_risk`
- `1` negative signal => `watch`
- `0` negative signals => `healthy`

## Glossary
- Customer health: business view of relationship stability.
- Risk signals: negative shifts in recency, frequency, spend, margin, mix.
- Tiers: VIP, Gold, Silver, Bronze.
- Actions: recommended human steps to reduce lifecycle risk.

## Optional Extensions (After L300 Complete)
- Use `labs/customer-lifecycle/level-400/extensions.md` only after L300 is complete.
- L400 work is enrichment only and is outside workshop pass/fail.
- If class time requires cuts, move non-essential items to `labs/customer-lifecycle/level-400/extensions.md` as after-class extensions. Do not delete deferred learning items.
