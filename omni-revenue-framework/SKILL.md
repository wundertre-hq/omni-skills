---
name: omni-revenue-framework
description: The Omni-Revenue Framework — Wundertre's five-tenet operating system for engineering revenue, and how to run it on WundertreOS. Use when the user asks for growth strategy, "how do I get more customers/revenue", marketing planning, or wants their business diagnosed — it turns those questions into a tenet-by-tenet audit and concrete, tool-executable plays.
---

# The Omni-Revenue Framework

> **Revenue is not a department. It is the natural byproduct of a unified,
> frictionless customer experience across every touchpoint of a business.**

The modern buyer researches you on LinkedIn, sees you on Instagram, Googles
your reviews, and receives your email — often within the same 24 hours. If
those touchpoints feel like four different companies, trust is broken before
they ever speak to your team. The businesses that consistently win are not
the ones with the biggest budgets or the most tactics — they are the ones
where marketing, sales, operations, and customer service all understand
their role in generating and multiplying revenue. When all four departments
speak the same language and share the same data, revenue stops being
something you chase and starts being something you engineer.

The framework is proprietary to Wundertre. This skill is the agent-executable
edition: the same five tenets, wired to the WundertreOS tools.

## Five tenets. One closed loop.

Implemented in order — each tenet creates the foundation the next stands on.
Tenet 5 feeds intelligence back into Tenet 1: a flywheel, not a checklist.

| # | Tenet | It in one line | Active hubs |
| - | ----- | -------------- | ----------- |
| 1 | **Omni-Insight** | Know before you grow — yourself, your offer, your buyer, your competition | Core, LeadSprout |
| 2 | **Omni-Presence** | Be everywhere that matters — surround your buyer on every channel *they* actually use | MarketBOOST, StoryCraft, Ardament |
| 3 | **Omni-Narrative** | Tell the story that converts — sales as the frictionless continuation of the marketing conversation | LeadSprout, StoryCraft |
| 4 | **Omni-Service** | Deliver and delight — ops and CX as the revenue multiplier, not the finish line | Buffollow, Core |
| 5 | **Omni-Tracking** | Measure everything. Close the loop. Feed the machine. | Core, MarketBOOST |

Omni means nothing ever stops: all five tenets run simultaneously, and the
flywheel only accelerates — Omni-Tracking insights sharpen Omni-Insight
targeting; Omni-Service advocacy generates Omni-Presence and Omni-Narrative
leads directly (delighted clients shortcut the flywheel).

Per-tenet execution detail — what "done" looks like and which tools do the
work — lives in `references/tenets.md`. Read it before executing inside any
single tenet.

## The Revenue Audit (the entry play)

When a user asks "how do I grow?", "what's wrong?", or "where should I
start?" — run the Revenue Audit: score each tenet from live data, name the
biggest growth gaps, and recommend a plan. Answer from where the business
**is today**, not where they want to be.

1. **Omni-Insight** — do they know exactly who they're chasing?
   `get_persona`/`list_personas` (are personas real or empty?),
   `list_competitors`, business profile completeness,
   `get_contact_attribution_breakdown` (do they know where customers come
   from?), `get_pixel_health` (is first-party data even being collected?).
2. **Omni-Presence** — do they show up everywhere their buyers look?
   `get_traffic_sources` (channel spread vs one-channel dependence),
   `get_social_post_performance` (cadence + engagement), `list_listings`,
   `get_ad_performance`, `list_websites`/`get_website_content`.
3. **Omni-Narrative** — does interest turn into booked business without
   friction? `get_funnel_metrics` (capture rate), `get_form_submissions`,
   `list_booking_pages`/`get_booking_stats` (is booking instant?),
   `list_workflows` (does follow-up run itself?), `get_pipeline_summary`
   (is the pipeline worked?), quote/document velocity
   (`get_quote_pipeline_stats`, `get_document_pipeline`).
4. **Omni-Service** — is every client a growth engine? `get_csat_summary`,
   `get_open_tickets` (speed + silence), `get_membership_metrics`
   (recurring revenue), `get_referral_performance` (is the referral engine
   producing?).
5. **Omni-Tracking** — can they see what drives the money?
   Attribution coverage (`get_contact_attribution_breakdown`, DNI call
   tracking via `get_dni_swap_stats`), whether reports exist and get read
   (`get_report_data`).

Present: a per-tenet readiness read (strong / partial / gap) with the
numbers as evidence, the 1–2 biggest growth gaps, and a recommended plan of
2–3 plays. **Respect tenet order**: running Omni-Presence spend on top of an
empty Omni-Insight tenet is "technically possible, reliably expensive, and
usually disappointing" — if Tenet 1 is hollow, fix it first. Offer to start
play #1 immediately.

## The plays

- `orf-lead-engine` — Tenet 3, Omni-Narrative (plus the Tenet 2 capture
  seam): zero-friction conversion and follow-up that never drops a lead.
- `orf-social-engine` — Tenet 2, Omni-Presence: persona-grounded content on
  a cadence, native to each channel, one narrative thread.
- `orf-weekly-revenue-review` — Tenet 5, Omni-Tracking: the operating
  cadence that closes the loop and feeds the machine.

The framework's deeper corpus (channel guides, industry playbooks, training)
lives in the Wundertre Omni Hub — the master framework document there is
authoritative if anything here seems ambiguous. Ask Wundertre
(hello@wundertre.com) for access.

## Voice

Talk about the framework the way it talks about itself: engineer revenue,
don't chase it; departments are revenue generators; every touchpoint earns
or loses the sale; the flywheel compounds. Never present the framework as a
bag of tactics — it is an operating discipline, and the order matters.
