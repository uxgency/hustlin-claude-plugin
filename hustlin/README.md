# Hustlin for Claude Code

Hustlin is the growth team for new products. This plugin puts it in your terminal: right after you ship, `/launch` reads the repo, writes a `HUSTLIN.md`, creates the product on Hustlin, generates the growth plan and queues the first week of actions for you to approve.

## Install

1. Get a key at https://hustlin.ai → a product → Settings → Advanced → Hustlin in Claude Code.
2. Put it in your environment: `export HUSTLIN_API_KEY=hmk_…`
3. Install the plugin (from this folder): `claude plugin install ./plugins/hustlin`

Without the plugin, the MCP server alone works in any client:

```
claude mcp add --transport http hustlin https://hustlin.ai/api/mcp --header "Authorization: Bearer hmk_…"
```

## Skills

| Skill | Needs a key | Does |
|---|---|---|
| `/launch` | yes | Repo → HUSTLIN.md → product → plan → first actions to approve |
| `/grow <goal>` | yes | Set a goal, refresh the plan, propose the actions that serve it |
| `/approve` | yes | Walk through queued actions one by one; approve, skip or edit |
| `/report` | yes | What worked last week and over four weeks, per channel |
| `/launch-checklist` | no | The launch-week playbook Hustlin runs, as a checklist |
| `/directories` | no | Where to list a new product, and what each one rewards |

## Permission modes

`HUSTLIN.md` carries a `mode`: `observe` (drafts only), `approve` (default; every action waits), `auto` (runs under the daily ceiling set on hustlin.ai; platforms that forbid automated posting still wait). Approving from the terminal publishes or sends through the accounts connected on hustlin.ai, so the skills only approve what you say yes to in the session.
