# Validation Checklist and Evidence Record

## T011 - Foundry Navigation/Auth Checklist Coverage
| Check | Status | Evidence |
|---|---|---|
| New Foundry toggle check exists in Foundry lab | Pass | `labs/customer-lifecycle/level-300/foundry.md` Step 1 |
| "No Project API key" path is explicitly documented | Pass | `labs/customer-lifecycle/level-300/foundry.md` Portal Assumptions + Step 3 |
| Build -> Data steps are explicitly present | Pass | `labs/customer-lifecycle/level-300/foundry.md` Steps 5-6 |
| Build -> Workflows steps are explicitly present | Pass | `labs/customer-lifecycle/level-300/foundry.md` Steps 4, 7-16 |

## T012 - 4-Agent Sequencing + Recency Threshold Validation
Artifacts checked:
- `common/customer-lifecycle/risk-rules.md`
- `labs/customer-lifecycle/level-300/foundry.md`
- `labs/customer-lifecycle/level-300/output-contract.md`
- `docs/customer-lifecycle/facilitator-guide.md`

| Validation point | Status | Findings |
|---|---|---|
| Four Foundry agents are documented in sequence | Pass | Foundry Goal + Steps 8-12 + Step 13 handoff chain |
| Agent handoff mapping is explicit | Pass | Foundry Step 13 and output-contract Foundry handoff table |
| Agent 3 uses same threshold text as risk rules | Pass | Exact text `tier='VIP' AND recency_days > 60` appears in both files |
| Agent 3 threshold evidence is required in outputs | Pass | `output-contract.md` requires `vip_recency_threshold_days` + `agent3_rule_text` |

## T013 - Synthetic News Scope + Exception Coverage Validation
Artifacts checked:
- `common/customer-lifecycle/signal-dictionary.md`
- `common/customer-lifecycle/action-mapping.md`
- `labs/customer-lifecycle/level-300/foundry.md`

| Validation point | Status | Findings |
|---|---|---|
| Dataset name is canonical (`synthetic_regional_news_24m`) | Pass | Present in all three artifacts |
| Scope constrained to last 24 months | Pass | Present in all three artifacts |
| Regional events + fictional-company references required | Pass | Present in Foundry guidance + common docs |
| Exception handling covers required paths | Pass | Missing region, non-fictional company, malformed date, stale record documented and excluded from correlation |

## T014 - Cross-Doc Consistency Validation
Artifacts checked:
- `README.md`
- `docs/customer-lifecycle/learner-guide.md`
- `docs/customer-lifecycle/facilitator-guide.md`
- `.specify/specs/customer-lifecycle/traceability.md`

| Validation point | Status | Findings |
|---|---|---|
| New Foundry assumptions trace from README/guides to Foundry lab | Pass | Guides and traceability point to Foundry navigation/auth assumptions |
| Build -> Data and Build -> Workflows expectations are mirrored in guides | Pass | Learner/facilitator include explicit navigation checkpoints |
| 4-agent workflow and threshold checks are traceable end-to-end | Pass | Traceability FR-013/FR-014 mappings and facilitator rubric enforce completion evidence |

Remediation items: None.
