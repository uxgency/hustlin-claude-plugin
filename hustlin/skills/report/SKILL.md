---
name: report
description: What worked. Pulls Hustlin's weekly report (per channel: attempts, reach, clicks, credited signups, purchases, revenue; keep and stop lists; what is waiting) for last week and the last four weeks as markdown. Use when the user asks how growth is going, what worked, or for a weekly update.
---

# /report

Needs the `hustlin` MCP server and a product id (from `HUSTLIN.md` or `products`).

## Steps

1. `report` for the product (or once per product the user names). It returns `markdown`: headline, the week's narrative paragraph when there is one, last week and four weeks by channel, keep and stop with the learning loop's reasons, unattributed signups, tracked-link clicks and what is waiting for approval.
2. Show the markdown as returned. Add at most three sentences of your own underneath: what the numbers mean for the goal in `HUSTLIN.md`, and the one or two queued actions that follow from the data. Do not rewrite the numbers.
3. If the report shows unattributed signups and `HUSTLIN.md` has no `conversion_key_prefix`, say that the conversion snippet (`/launch` step 7, or `conversion_snippet`) is what turns them into credited ones.
4. Offer to save it under the `filename` the tool returns (`reports/YYYY-MM-DD-growth.md`). Only write the file on a yes.

## Rules

- Zero credited customers is a real result: say it plainly and point at the funnel destination and connected accounts rather than softening it.
- Do not invent numbers that `report` did not return. `results` has the same data as JSON when a table of your own is needed.
