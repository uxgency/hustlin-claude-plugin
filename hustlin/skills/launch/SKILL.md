---
name: launch
description: Commercialize what was just built. Reads the repo, writes HUSTLIN.md, creates the product on Hustlin, generates the growth plan and queues the first actions for approval. Use after a ship, when the user says launch, go to market, get users, or asks how to get the product in front of people.
---

# /launch

Hustlin is the growth team for new products. This skill takes a repo from "it works" to "the first week of growth is drafted and waiting for approval". Needs the `hustlin` MCP server (key from https://hustlin.ai → Settings → Advanced).

## Steps

1. **Read the product from the repo.** README, package manifest, landing page copy, `llms.txt`, pricing page, App Store or store listing if any. Extract: name, one-paragraph description, public URL, stage, who it is for, how it makes money. Do not guess what you cannot find; ask.
2. **Write or update `HUSTLIN.md`** at the repo root from the template below. Fill every field you can from the repo; leave the rest blank and ask the user for target audience, pricing and funnel destination if they are missing. Voice: propose three lines from how the README talks, plus "no invented numbers, no comparisons to named competitors" unless the user says otherwise. Show the file and get an OK before any tool call.
3. **Find or create the product.** Call `products`. If one matches by URL or title, reuse its id. Otherwise `create_product` with title, description, url, stage, targetAudience, pricing and mode from the file. Write the returned id into `HUSTLIN.md` under `product_id`.
4. **Sync context.** `sync_context` with every filled field (voice, goals, north star, funnel destination, mode).
5. **Plan.** `plan` with the product id. It returns the step list immediately; the plan, listings, first posts, launch timeline, outreach and ad drafts arrive over the next few minutes.
6. **Show what was queued.** After two or three minutes, call `actions` with `status: queued`. Summarize by channel in a short table: what, where, when. Then hand over to `/approve`: never approve anything here.
7. **Wire up conversions.** Ask once: "Should your signup handler report signups to Hustlin so channels get credit?" On a yes, call `conversion_snippet` with the product id. It returns the five-line snippet (JavaScript, Swift, curl), the env var name and a venture key shown once. Put the snippet where the product creates an account (and, for payments, where it records a purchase, as `type: "purchase"` with `valueCents`), capture the `hlc` query parameter on the landing page as the result's `capture` text describes, and tell the user to set the env var in the product's deployment secrets. Never write the key into a tracked file; never print it twice. Record `conversion_key_prefix` in `HUSTLIN.md`.
8. **Close with the two things only the founder can do:** connect accounts (`connect` gives the URLs) and pick the tracked-link destination (`track_link` mints a link for any channel once the destination is set).

## HUSTLIN.md template

Copy from `templates/HUSTLIN.md` in this plugin: Product (name, url, description, stage, funnel_destination), Customers (target_audience, pricing), Voice, Goals (north_star, goals), Mode (observe | approve | auto), Hustlin (product_id, conversion_key_prefix).

## Rules

- `approve` publishes through the user's connected accounts. This skill does not call it, and never calls `run`.
- The conversion key is a secret: it goes in the deployment's environment, not in `HUSTLIN.md`, `.env` files that are committed, or chat transcripts more than once.
- One product per repo unless the user says otherwise.
- If `create_product` says the plan's product limit is reached, say so and stop; upgrades happen on hustlin.ai/pricing.
