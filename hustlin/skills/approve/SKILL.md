---
name: approve
description: Walk through Hustlin's queued growth actions one by one and approve, skip or edit them on the user's say-so. Use when the user wants to review drafts, approve posts or outreach, or asks what is waiting.
---

# /approve

Needs the `hustlin` MCP server. Approving runs the action through the accounts connected on hustlin.ai (a post is posted, an email is sent), so this skill never approves without an explicit yes for that action in this session.

## Steps

1. `actions` with `status: queued` (and `productId` from `HUSTLIN.md` when present). If empty, say so and suggest `/launch` or `/grow`.
2. **Stale rows first, as a batch.** Rows with `stale: true` were scheduled more than two weeks ago; the moment passed. List them in one table (channel, date, first line of the draft) and ask once: skip them all, keep some, or look at each. Skip with `approve` `decision: skip` per row only after that yes. Never approve a stale row without rescheduling it (`edit` cannot reschedule; say so and leave it).
3. For each live action, in order: show channel, scheduled date, the full `draft`, what it is `waitingFor`, and the `automationLevel` (manual: guidance for the founder; ai_assisted: Hustlin drafts, the founder posts on platforms that forbid automated posting; one_tap and auto: Hustlin publishes). The `brief` is the planning instruction, not the post; show it only when asked. If `waitingFor` says autopilot runs it at its scheduled time, say so and move on unless the user wants it out now. Ask one question: approve, skip, edit, or stop.
4. On **approve**: `approve` with `decision: approve`. Report the `delivery` the server returns (guidance, draft or run) in one line.
   On **skip**: `approve` with `decision: skip`.
   On **edit**: take the user's changes (or draft a revision if they describe it), show the new text, and on their OK call `approve` with `decision: edit` and `content`; then ask again whether to approve it.
   On **stop**: end and summarize.
5. After the last one: one table of what was approved, skipped, edited and left, and a reminder that run results show up in `actions` and in `/report`.

## Rules

- Never batch-approve. Never approve on "looks good" said before the draft was shown.
- Keep the user's voice: edits follow the Voice section of `HUSTLIN.md`.
- Manual actions are tasks for the founder; approving one does not run anything.
- An action that is already `approved` (autopilot or a teammate approved it; it is waiting for its calendar slot) is not re-approved here. If the user wants it out now, call `run` with its id; `run` refuses drafts, so it never approves on its own.
