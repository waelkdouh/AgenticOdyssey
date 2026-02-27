# Action Mapping Matrix

Recommended human actions tied to observed risk patterns.

## Matrix
| Risk pattern (2+ negatives) | Typical triggered signals | Recommended actions | Owner | SLA target |
|---|---|---|---|---|
| Engagement slowdown | Recency + Frequency | 1) Retention outreach call, 2) Confirm blockers, 3) Schedule follow-up in 7 days | Account owner | Contact in 2 business days |
| Revenue softening | Frequency + Spend | 1) Usage/value conversation, 2) Targeted offer, 3) 30-day recovery check | Account owner + Sales ops | Plan in 3 business days |
| Profitability pressure | Spend + Margin | 1) Pricing/margin review, 2) Discount governance check, 3) Offer redesign | Sales ops + Finance partner | Review in 5 business days |
| Relationship narrowing | Recency + Mix | 1) Cross-sell discovery, 2) Portfolio recommendation, 3) Executive sponsor touchpoint | Account owner | Outreach in 3 business days |
| Broad deterioration | 3+ across Recency/Frequency/Spend/Margin/Mix | 1) Escalated retention plan, 2) Weekly health checkpoint, 3) Leadership visibility note | Account owner + Manager | Start same week |

## Level 300 Usage
- Select one primary action bundle per at-risk VIP/Gold customer.
- Explain action in plain business language linked to triggered signals.
- Do not introduce predictive probability language in Level 300.

## Agent 4 Synthetic News Input Contract
- Required dataset: **`synthetic_regional_news_24m`**.
- Allowed analysis window: **most recent 24 months only** from run date.
- Event scope: regional events (for example natural disasters, major public events, and supply disruptions) with fictional-company references.
- Required exception handling before action mapping:
  - `exception_missing_region`
  - `exception_non_fictional_company`
  - `exception_malformed_date`
  - `exception_stale_record`
- Exception rows are excluded from action correlation and must be reported in validation notes.
