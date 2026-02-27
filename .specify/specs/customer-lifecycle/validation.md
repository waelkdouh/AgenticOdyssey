# Validation Checklist and Evidence Record

## T012 - FR-006 Build/Config Validation Rules
| Check | Status | Evidence |
|---|---|---|
| Copilot Studio lab includes concrete artifact creation/configuration before execution prompts | Pass | `labs/customer-lifecycle/level-300/copilot-studio.md` Steps 2-4 before Steps 5-10 |
| Agent Framework lab includes concrete workflow creation/configuration before proactive demo | Pass | `labs/customer-lifecycle/level-300/agent-framework.md` Steps 1-5 before Step 6 |
| Validation language explicitly rejects conversation-only baseline completion | Pass | Guardrails/constraints sections in both files |

## T013 - "Not Conversation-Only" Parity Validation
Artifacts checked:
- `labs/customer-lifecycle/level-300/copilot-studio.md`
- `labs/customer-lifecycle/level-300/agent-framework.md`
- `docs/customer-lifecycle/learner-guide.md`
- `docs/customer-lifecycle/facilitator-guide.md`

| Validation point | Status | Findings |
|---|---|---|
| Learner guidance states build/configuration required in Level 300 | Pass | Learner guide section "Level 300 Build/Configure Checkpoints (Required)" |
| Facilitator grading states build/configuration required | Pass | Facilitator guide "Grading Enforcement (L300-Only)" and checkpoint table |
| Copilot Studio baseline is build/configure then execute | Pass | Copilot Studio Steps 2-4 then prompt execution |
| Agent Framework baseline is build/configure then execute | Pass | Agent Framework Steps 1-5 then test run |

## T014 - FR-012 Scope-Cut Deferral Validation
Artifacts checked:
- `docs/customer-lifecycle/learner-guide.md`
- `docs/customer-lifecycle/facilitator-guide.md`
- `labs/customer-lifecycle/level-400/extensions.md`

| Validation point | Status | Findings |
|---|---|---|
| Scope-cut policy says non-essential items move to Level 400 after class | Pass | Learner/facilitator explicit policy text |
| Scope-cut policy says deferred content is not deleted | Pass | Facilitator "Scope-Cut Policy (FR-012)" and learner optional extensions notes |
| Level 400 file provides receiving path for deferred items | Pass | Extensions section "Deferred In-Class Scope Cuts (After-Class Intake)" |

## T015 - Level Model/Pathing Parity Validation
Artifacts checked:
- `README.md`
- `docs/customer-lifecycle/learner-guide.md`
- `docs/customer-lifecycle/facilitator-guide.md`
- `labs/customer-lifecycle/level-300/copilot-studio.md`
- `labs/customer-lifecycle/level-300/foundry.md`
- `labs/customer-lifecycle/level-300/agent-framework.md`
- `labs/customer-lifecycle/level-300/output-contract.md`
- `labs/customer-lifecycle/level-400/extensions.md`

| Validation point | Status | Findings |
|---|---|---|
| `level-300` is the required baseline path for completion | Pass | README, learner/facilitator guides, output contract |
| `level-400` is optional complexity and excluded from pass/fail | Pass | README, learner/facilitator guides, Level 400 extension header |
| Pathing language is consistent across docs/labs | Pass | No conflicting pass/fail or level-boundary wording found |

## T016 - Baseline Output and Risk-Rule Validation
Artifacts checked:
- `labs/customer-lifecycle/level-300/output-contract.md`
- `common/customer-lifecycle/risk-rules.md`
- `docs/customer-lifecycle/facilitator-guide.md`
- `labs/customer-lifecycle/level-300/foundry.md`

| Required validation | Status | Evidence |
|---|---|---|
| Level 300 outputs include at-risk VIP/Gold + explanation + action + portfolio summary | Pass | Output contract Section 5-11 and learner/facilitator grading references |
| Portfolio summary requires tier counts, at-risk counts, at-risk % by tier | Pass | Output contract Section A; Foundry Step 9 |
| Risk examples cover 0/1/2/3+ signal cases | Pass | Risk rules "Example Cases" table |
| At-risk threshold is strictly 2+ negative signals | Pass | Risk rules baseline contract and Foundry Step 7 |

Remediation items: None.
