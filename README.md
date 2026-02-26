# AgenticOdyssey

Agentic workshop/demo repository spanning **Microsoft Foundry**, **Copilot Studio**, and **Agent Framework**.

## Repository Status
This repo is being rebaselined. Content and structure may change as new specs are introduced.

## Spec-Kit: From Spec -> Tasks
Use this flow to turn a feature idea into executable tasks.

1. **Start on a feature branch**
   - `git checkout -b <feature-branch>`

2. **Create the feature spec**
   - In chat: `/speckit.specify <feature description>`
   - Output: `.specify/specs/<feature-id>/spec.md`

3. **Clarify requirements (optional but recommended)**
   - In chat: `/speckit.clarify`
   - Updates: `.specify/specs/<feature-id>/spec.md`

4. **Generate technical plan**
   - In chat: `/speckit.plan`
   - Output: `.specify/specs/<feature-id>/plan.md`

5. **Generate implementation tasks**
   - In chat: `/speckit.tasks`
   - Output: `.specify/specs/<feature-id>/tasks.md`

6. **Execute implementation**
   - In chat: `/speckit.implement`

## New-Spec Starter Prompt (Copy/Paste)
Use this directly in chat to kick off a new feature spec:

```text
/speckit.specify Create a new feature called "<feature-name>".
Problem to solve: <what problem this feature solves>.
Target users: <who benefits>.
In scope: <key capabilities>.
Out of scope: <explicit exclusions>.
Success criteria: <measurable outcomes>.
Constraints: <tech/business/compliance constraints>.
```

## Customer-Demo Wake-Up (No Strategery)
```text
Wake-up (customer demo mode):
1) Use current filesystem state only.
2) Confirm branch/worktree:
   - git --no-pager branch --show-current
   - git --no-pager status --short
3) Focus outputs on:
   - end-user "aha" insights
   - churn/retention actions
   - Copilot Studio topic design
   - click-by-click steps in https://copilotstudio.preview.microsoft.com/
4) Keep outputs concise, business-first, and demo-ready.
```
