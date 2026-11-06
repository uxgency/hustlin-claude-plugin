# Hustlin for Claude Code

Hustlin is the growth team for new products. This plugin puts it in your terminal: right after you ship, `/launch` reads the repo, writes a `HUSTLIN.md`, creates the product on Hustlin, generates the growth plan and queues the first week of actions for you to approve.

## Install

```
claude plugin marketplace add uxgency/hustlin-claude-plugin
claude plugin install hustlin@uxgency
```

The first tool call opens your browser to sign in to Hustlin and allow Claude Code (OAuth 2.1 with PKCE). Revoke it any time at https://hustlin.ai → a product → Settings → Advanced.

Without the plugin, the MCP server alone works in any client that supports OAuth:

```
claude mcp add --transport http hustlin https://hustlin.ai/api/mcp
```

No browser (CI, a server)? Create a key under Settings → Advanced and pass it as a header: `--header "Authorization: Bearer hmk_…"`.

## Skills

| Skill | Needs an account | Does |
|---|---|---|
| `/launch` | yes | Repo → HUSTLIN.md → product → plan → first actions to approve, plus the conversion snippet for the signup handler |
| `/grow <goal>` | yes | Set a goal, refresh the plan, propose the actions that serve it |
| `/approve` | yes | Walk through queued actions one by one; approve, skip or edit |
| `/report` | yes | The weekly what-worked report as markdown, per channel, ready to save in the repo |
| `/launch-checklist` | no | The launch-week playbook Hustlin runs, as a checklist |
| `/directories` | no | Where to list a new product, and what each one rewards |

## Permission modes

`HUSTLIN.md` carries a `mode`: `observe` (drafts only), `approve` (default; every action waits), `auto` (runs under the daily ceiling set on hustlin.ai; platforms that forbid automated posting still wait). Approving from the terminal publishes or sends through the accounts connected on hustlin.ai, so the skills only approve what you say yes to in the session.
