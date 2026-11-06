# Hustlin for Claude Code

The growth team for new products, in your terminal. You shipped; now `/launch` reads the repo, writes a `HUSTLIN.md`, creates the product on [Hustlin](https://hustlin.ai), generates the growth plan and queues the first week of actions for you to approve. `/approve` walks through them. `/report` tells you what worked, per channel, with credited customers.

This repository is a Claude Code plugin marketplace with one plugin, `hustlin`.

## Install

```
claude plugin marketplace add uxgency/hustlin-claude-plugin
claude plugin install hustlin@uxgency
```

The first tool call opens your browser to sign in to Hustlin and allow Claude Code (OAuth 2.1 with PKCE). Revoke the connection any time under Settings → Advanced on hustlin.ai.

The MCP server alone, in any client that supports OAuth:

```
claude mcp add --transport http hustlin https://hustlin.ai/api/mcp
```

For CI or a client without a browser, create a key under Settings → Advanced and pass it as `--header "Authorization: Bearer hmk_…"`.

## What is in the plugin

| Skill | Needs an account | Does |
|---|---|---|
| `/launch` | yes | Repo → `HUSTLIN.md` → product → plan → first actions to approve, plus the conversion snippet for your signup handler |
| `/grow <goal>` | yes | Set a goal, refresh the plan, propose the actions that serve it |
| `/approve` | yes | Walk through queued actions one by one; approve, skip or edit |
| `/report` | yes | The weekly what-worked report as markdown, ready to save in the repo |
| `/launch-checklist` | no | The launch-week playbook Hustlin runs, as a checklist |
| `/directories` | no | Where to list a new product, and what each one rewards |

The MCP server exposes thirteen tools (products, plan, actions, approve, results, track_link, report_conversion and more). The full list, the `HUSTLIN.md` template and the permission modes are at [hustlin.ai/mcp](https://hustlin.ai/mcp).

## Permission modes

`HUSTLIN.md` carries a `mode`: `observe` (drafts only), `approve` (default; every action waits for you), `auto` (runs under the daily ceiling you set on hustlin.ai; platforms that forbid automated posting still wait). Approving from the terminal publishes or sends through the accounts connected on hustlin.ai, so the skills only approve what you say yes to in the session.

## Source

The plugin is developed in Uxgency's studio monorepo and published here. Issues and ideas: support@hustlin.ai.
