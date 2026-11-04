---
name: report
description: What worked. Pulls Hustlin's per-channel results (attempts, reach, credited signups, purchases, revenue, tracked-link clicks) for last week and the last four weeks and writes a short report. Use when the user asks how growth is going, what worked, or for a weekly update.
---

# /report

Needs the `hustlin` MCP server and a product id (from `HUSTLIN.md` or `products`).

## Steps

1. `results` for the product (or for each product the user names).
2. Write the report in this shape, in plain words, about 150 words:
   - **Headline:** credited signups and revenue last week vs the four-week average. "Credited" means it came through a Hustlin tracked link; say so once.
   - **By channel:** a table with channel, attempts, reach, clicks, signups, purchases, revenue. Only channels with activity.
   - **Keep / stop:** the `doMore` and `stop` lists from the learning loop, one line each on why.
   - **Unattributed:** the number of signups not tied to any channel, if any, with a note that the tracked-link destination decides this.
   - **Next:** one or two actions from `actions` (status queued) that follow from the data.
3. Offer to save it as `reports/YYYY-MM-DD-growth.md` in the repo. Only write the file on a yes.

## Rules

- Zero credited customers is a real result: say it plainly and point at the funnel destination and connected accounts rather than softening it.
- Do not invent numbers that `results` did not return.
