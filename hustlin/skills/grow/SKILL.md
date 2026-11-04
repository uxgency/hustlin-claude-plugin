---
name: grow
description: Point Hustlin at a growth goal ("50 paying customers by January", "200 beta signups"). Records the goal, refreshes the plan and shows the actions that serve it. Use when the user names a growth target or asks what to do next for growth.
---

# /grow <goal>

Needs the `hustlin` MCP server and a product (run `/launch` first if `HUSTLIN.md` has no `product_id`).

## Steps

1. Read `HUSTLIN.md` for the product id and current goals. If the user gave a goal in the command, use it; otherwise ask for one sentence with a number and a date.
2. `sync_context` with `goals` (existing goals plus the new one, newest first, at most five) and, if the goal is clearly the one metric, `northStar`.
3. `results` for the product. If there is any credited data, say which channels the learning loop marks do-more and stop before planning more work.
4. `plan` with `force: true` only when the product already has a completed plan and the goal is new; otherwise skip (the weekly replan picks the goal up).
5. `actions` with `status: queued`. Pick the actions that serve the goal and present them as a numbered list: channel, what it does, why it serves the goal, when. Mark the rest as "parked".
6. Hand over to `/approve`. Do not approve anything here.

## Rules

- Goals are the founder's words; do not rewrite the number or the date.
- Stop channels the learning loop says to stop, even if they look busy.
