---
name: orf-weekly-revenue-review
description: Omni-Revenue Framework play (Tenet 5, Omni-Tracking) — the weekly operating review on WundertreOS. Measures everything, closes the loop, and feeds the machine - pulls the numbers across every tenet, names the constraint, and queues next actions. Use when the user asks "how's the business doing", wants a weekly/monthly report, or on a recurring schedule.
---

# Play: The Weekly Revenue Review (Tenet 5 — Omni-Tracking)

Measure everything. Close the loop. Feed the machine. Without tracking,
every tenet executes on assumptions; with it, on evidence. One honest page
a week — numbers, the constraint, the next moves — is the cadence that
makes the flywheel compound. (The framework's full cadence: weekly
briefings, monthly attribution review, quarterly framework reset.)

## 1. Pull the stage numbers (reads only — safe to run unprompted)

Run these for the last 7 days AND last 30 days (trend beats snapshot):
- Omni-Presence: `get_traffic_sources`, `get_social_post_performance`,
  `get_ad_performance` (spend, CTR, CPA), `get_lsa_leads`
- Omni-Narrative (capture → close): `get_funnel_metrics` (conversion rate),
  `get_form_submissions` (`total_count`), `get_bookings`,
  `get_dni_swap_stats`, `get_email_campaign_performance` /
  `get_sms_campaign_performance` for anything sent this week,
  `get_pipeline_summary` (open value, won/lost this window),
  `get_quote_pipeline_stats`, `get_document_pipeline` (stuck signatures)
- Omni-Service: `get_membership_metrics` (MRR), `get_csat_summary`,
  `get_open_tickets`, `get_referral_performance`
- Cross-check: `get_report_data` and `analyze_business_performance` for
  anything the per-tool reads missed.

## 2. Write the page

Structure:
1. **Headline** — the one sentence the owner needs ("Pipeline added $18k;
   the constraint is capture: 900 sessions produced 6 leads").
2. **Scoreboard** — tenet table, this week vs last, only tool-returned
   numbers. If a channel shows zero activity, say zero — never soften it.
3. **The constraint** — the single weakest tenet, with the evidence.
   Insights here feed back into Omni-Insight: churn patterns refine
   personas; referral data identifies the highest-LTV profiles to clone.
4. **Three moves** — concrete plays (from `orf-lead-engine`,
   `orf-social-engine`, ads/retention plays), each executable by tools in
   this connector, effort-sized. Offer to run move #1 now.

## 3. Queue the work

For accepted moves: create the artifacts immediately (`create_task` for
human work, workflows/campaigns/posts for automated work — with the usual
approval on outward-facing sends). Don't leave the review as a document;
leave it as queued work.

## Guardrails

- Trend honestly: one week of data is noise for small orgs — say so and
  lean on the 30-day window.
- If tool data is thin ("not enough data to call a driver"), that IS the
  finding: the move becomes "instrument the gap" (pixel, DNI, forms).
