# Agent Team: Full Software Development Team

A comprehensive agent team configuration that covers **all 129 sub-agents** across the entire catalog. The orchestrator (team lead) delegates tasks to specialized teammates, who invoke the right sub-agents via the Task tool.

## Architecture

```
                    ┌─────────────────────┐
                    │   ORCHESTRATOR      │
                    │   (Team Lead)       │
                    │                     │
                    │ agent-organizer     │
                    │ multi-agent-coord   │
                    │ workflow-orchestr   │
                    │ task-distributor    │
                    │ context-manager     │
                    │ knowledge-synth     │
                    │ performance-mon     │
                    │ error-coordinator   │
                    └────────┬────────────┘
                             │ delegates to
        ┌────────────────────┼────────────────────┐
        │                    │                    │
   ┌────┴─────┐    ┌────────┴───────┐    ┌───────┴──────┐
   │ PLANNING │    │  ENGINEERING   │    │   QUALITY    │
   │  LAYER   │    │    LAYER       │    │   LAYER      │
   ├──────────┤    ├────────────────┤    ├──────────────┤
   │Architect │    │ Frontend Lead  │    │ QA & Test    │
   │Product   │    │ Backend Lead   │    │ Security     │
   │Designer  │    │ Fullstack Dev  │    │ DevOps & SRE │
   │          │    │ Data & AI Lead │    │ DX & Tooling │
   └──────────┘    │ Systems Eng    │    └──────────────┘
                   └────────────────┘
                             │
                   ┌─────────┴──────────┐
                   │   SUPPORT LAYER    │
                   ├────────────────────┤
                   │ Technical Writer   │
                   │ Research & Intel   │
                   │ IT & Platform Ops  │
                   │ Domain Specialist  │
                   └────────────────────┘
```

## Team Roster (14 teammates + 1 lead)

| #  | Role                    | Sub-agents covered | Model  | Layer       |
|----|-------------------------|--------------------|--------|-------------|
| -- | **Orchestrator (Lead)** | 8 meta-orchestration agents | opus | Coordination |
| 1  | Solutions Architect     | 7 architecture + infra design agents | opus | Planning |
| 2  | Product Strategist      | 10 business/product/research agents | sonnet | Planning |
| 3  | UX/UI Designer          | 3 design + accessibility agents | sonnet | Planning |
| 4  | Frontend Lead           | 11 frontend/mobile/UI framework agents | sonnet | Engineering |
| 5  | Backend Lead            | 11 backend framework + server agents | sonnet | Engineering |
| 6  | Fullstack Developer     | 9 cross-stack + language agents | sonnet | Engineering |
| 7  | Data & AI Lead          | 14 data/ML/AI/DB agents | sonnet | Engineering |
| 8  | Systems Engineer        | 5 low-level/compiled/embedded agents | sonnet | Engineering |
| 9  | QA & Test Lead          | 9 quality/review/test agents | opus | Quality |
| 10 | Security Lead           | 7 security/compliance/risk agents | opus | Quality |
| 11 | DevOps & SRE            | 10 infra/deploy/reliability agents | sonnet | Quality |
| 12 | DX & Tooling            | 7 developer experience agents | sonnet | Quality |
| 13 | Technical Writer        | 7 docs/content/research agents | haiku | Support |
| 14 | IT & Platform Ops       | 7 Windows/PowerShell/M365 agents | sonnet | Support |

**Total: 129 sub-agents covered**

## How It Works

1. You give the **orchestrator** a task (or set of tasks)
2. Orchestrator analyzes scope, breaks into subtasks, identifies dependencies
3. Orchestrator assigns subtasks to the right **teammates**
4. Each teammate uses the **Task tool** to invoke specialized sub-agents from the catalog
5. Results flow back through the shared task list
6. Orchestrator synthesizes, validates, and reports completion

## Usage

### Prerequisites

Enable agent teams:
```json
// ~/.claude/settings.json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

### Start the Team

Copy the contents of `full-dev-team.md` and paste it as your prompt to Claude Code.

The orchestrator will only spin up teammates that are relevant to the current task. You don't pay for all 14 if you only need 3.

### Tips

- **Use delegate mode** (`Shift+Tab`) to keep the lead coordinating, not implementing
- **Pre-approve permissions** in settings to reduce prompt spam across teammates
- **Separate file ownership** per teammate to avoid write conflicts
- **Split panes** (`"teammateMode": "tmux"`) for visibility into all teammates
- Use `Shift+Up/Down` to message teammates directly

## Cost

Each active teammate is a separate Claude instance (~3-4x token cost vs single session). The orchestrator is designed to be selective — it won't spawn all 14 teammates for a simple bug fix.

## Customization

Fork `full-dev-team.md` and:
- Remove roles you don't need
- Adjust model assignments (opus/sonnet/haiku) per role
- Add project-specific context to teammate descriptions
- Modify sub-agent mappings to match your stack
