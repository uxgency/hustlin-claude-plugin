---
name: grow
description: Point Hustlin at a growth goal ("50 paying customers by January", "200 beta signups"). Records the goal, rebuilds the plan against it and shows how each queued action serves it. Use when the user names a growth target or asks what to do next for growth.
---

# /grow <goal>

Needs the `hustlin` MCP server and a product (run `/launch` first if `HUSTLIN.md` has no `product_id`).

## Steps

1. Read `HUSTLIN.md` for the product id and current goals. If the user gave a goal in the command, use it; otherwise ask for one sentence with a number and a date.
2. `sync_context` with `goals` (existing goals plus the new one, newest first, at most five) and, if the goal is clearly the one metric, `northStar`. Update the Goals section of `HUSTLIN.md` to match.
3. `results` for the product. If there is any credited data, say which channels the learning loop marks do-more and stop before planning more work.
4. `plan` with `force: true` when the product already has a completed plan and the goal is new; otherwise `plan` without it. The result's `goal` field is the goal as Hustlin read it (metric, number, deadline, weeks left, actions per week) and the channel families it leans into and holds back. Show that in two lines before the actions arrive, so the user can correct the reading now (a wrong number or date means fixing the goal sentence and calling `sync_context` again).
5. After two or three minutes, `actions` with `status: queued`. Present the ones with a `goalFit` as a numbered list: channel, what it does, the `goalFit` line (that is why it serves the goal; do not invent another reason), when. Rows without a `goalFit` were planned before the goal existed: list them under "parked" in one line each and suggest skipping them in `/approve` unless the user wants them.
6. Hand over to `/approve`. Do not approve anything here.

## Rules

- Goals are the founder's words; do not rewrite the number or the date.
- Stop channels the learning loop says to stop, even if they look busy.
- The `goalFit` line comes from the plan; quote it, do not paraphrase it into a promise of results.
