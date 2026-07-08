# The five tenets — execution detail

Condensed from the Omni-Revenue Framework master document (v1.0), with the
WundertreOS tools that execute each item. WundertreX delivery
services are noted where the play is human-facilitated rather than
tool-executable.

## Tenet 1 — Omni-Insight

*Know yourself, your offer, your buyer, and your competition.* Nothing else
works without it: Presence needs to know who to surround, Narrative needs to
know what to say, Service needs to know what the best customers look like,
Tracking needs a baseline. Four questions, answered before a dollar is spent:

**Brand identity & offer clarity** — the operating brief, not a tagline:
core brand promise in one sentence (nothing a competitor could copy
verbatim), documented voice, the offer and its transformation, signature
differentiators, visual standards in the Brand Kit.
→ `update_business_profile`, brand kit, `upsert_goal`.

**Buyer intelligence** — define buyers by behavior and intent, not
demographics. 2–3 sharp personas with channel habits, pain points, decision
triggers, and objections. Analyze existing best customers: where they came
from, what converted them, their LTV.
→ `upsert_persona` (full fields), `get_contact_attribution_breakdown`,
`list_contacts` breakdowns, pixel identity resolution (`get_pixel_health`,
`lookup_visitor_identity`), prospecting suite (`list_prospects`).

**Competitive intelligence** — top 3–5 direct + 2–3 indirect competitors:
their positioning, channel presence, pricing/guarantees, and their 1-star
reviews (the unmet needs you can own). The gaps they leave are your
cheapest entry points.
→ `upsert_competitor`, `analyze_competitor`, `analyze_competitor_domain`,
`run_serp_check`.

**Market position** — the measurable baseline: keyword gaps
(`search_keywords`), local rank vs competitors, directory accuracy
(`list_listings`), share of voice in paid.

## Tenet 2 — Omni-Presence

*Not everywhere on the internet — everywhere in your specific buyer's
internet.* Surround-sound marketing that makes you undeniable to that
buyer while spending nothing on people who will never buy.

- **Research, keywords & funnel architecture first**: map awareness /
  consideration / intent queries; build the funnel before producing
  content; every piece of content gets a measurable outcome attached
  (content → landing page → lead magnet/booking → deal).
  → `search_keywords`, `build_funnel`, `get_funnel`, `analyze_funnel`.
- **Multi-channel orchestration**: 3–5 channels from persona work;
  platform-native content carrying one identical promise; sequenced
  touches (awareness → retargeting/email → search/intent). Never break
  the narrative thread.
- **Content as currency**: formats mapped to stages; relentless
  consistency; repurpose one asset into many.
  → `generate_copy`, `generate_image`, `create_social_post`,
  `schedule_social_post`.
- **Paid media precision**: CRM-synced audiences, pixel retargeting,
  sequenced multi-platform campaigns. → `create_ad_campaign`,
  `update_ad_campaign`, `get_ad_performance`, `suggest_ad_optimizations`.
- **Organic omnipresence**: 70+ directories accurate, reviews answered in
  brand voice, local SEO, consistent organic cadence. → `list_listings`,
  website/landing tools (`create_website`, `expand_website`,
  `publish_website`, `generate_landing_page`).

## Tenet 3 — Omni-Narrative

*The biggest revenue leak is not a marketing or sales problem — it's a
handoff problem.* Sales must be the natural continuation of the marketing
conversation; the prospect should feel understood, not pitched.

- **Story continuation**: every lead lands in the CRM with its full
  marketing journey attached; collateral uses the exact language of the
  marketing that attracted them; discovery references the pains the
  marketing surfaced. → contact attribution fields, `get_contact_details`,
  `analyze_lead`, `generate_copy` for collateral.
- **Zero-friction conversion**: booking instant (booking pages
  everywhere), quotes in minutes (templates), signing frictionless
  (e-sign), payment ready. → `list_booking_pages`/`update_booking_page`,
  `create_document_from_template`, `send_document`, quotes tools.
- **Consistent outreach at scale**: drip sequences that read as natural
  follow-ons to the content already consumed; behavior-triggered
  follow-ups (quiet deal, unread quote, missed booking) so nothing falls
  through the cracks. → `create_workflow`, `enroll_in_workflow`,
  `create_email_campaign_from_template`, `create_sms_campaign`,
  `send_email_to_contact`/`send_sms_to_contact`.

## Tenet 4 — Omni-Service

*A closed deal is not revenue locked in — it is revenue at risk.* The
post-sale experience is the most important marketing the business will
ever do; every interaction after the close builds or destroys the referral
pipeline.

- **Effortless onboarding**: automated kickoff the moment a deal hits
  closed-won; structured milestones; a named point of contact; proactive
  Day 7/14/30 check-ins. → workflows triggered on closed-won,
  `create_task`, `list_scheduled_services`.
- **Support that builds trust**: shared inbox with full context; SLAs
  communicated (customers tolerate problems, not silence); AI agent for
  Tier 1; CSAT after every resolution — measured religiously.
  → `list_tickets`, `reply_to_ticket`, `get_csat_summary`, chatbot tools.
- **Loyalty, referrals, expansion**: tiered loyalty; branded referral
  engine with tracked payouts; expansion timed by customer-health signals;
  QBRs with high-LTV customers. → loyalty tools, `send_referral_invite`,
  `get_referral_performance`, `get_membership_metrics`.

## Tenet 5 — Omni-Tracking

*Without it every tenet executes on assumptions; with it, on evidence.*
The journey is a closed loop, and Tenet 4's intelligence must flow back
into Tenet 1.

- **Revenue attribution**: every lead/deal/customer traceable to the
  marketing that produced it — call tracking on every channel, pixels +
  UTMs everywhere, ad data joined to pipeline data; CPL/CPA/LTV by
  channel, not just by campaign. → DNI tools, `get_dni_swap_stats`,
  `get_contact_attribution_breakdown`, `get_ad_performance` +
  `get_pipeline_summary`.
- **Performance dashboards**: revenue dashboard (pipeline value, closed
  revenue, MoM, churn); channel dashboards; sales velocity (deal size,
  cycle, win rate, coverage); customer health in real time.
  → `get_report_data`, the tenet-by-tenet reads in the Revenue Audit.
- **The feedback loop**: monthly — which segments grow, which churn, and
  the common thread; churn refines personas (stop marketing to buyer
  types that churn); referral/expansion data finds the highest-LTV
  profiles to clone in Tenet 2; support-ticket trends become content
  strategy; quarterly framework review before the next cycle.

## The flywheel over cycles

Cycle 1 sets the baseline (brand documented, market mapped, first
coordinated presence). Cycle 2 sharpens everything with real performance
data. Cycle 3: the referral engine produces organic growth and budget moves
to high-LTV sources — CAC drops. Cycle 4+: a positive feedback loop where
every department generates revenue intelligence. Systems compound; single
campaigns don't.

## Implementation order (getting started)

1. Complete Omni-Insight (brand audit, personas, competitive brief,
   keyword gaps) — facilitated by WundertreX or run tool-by-tool.
2. Configure WundertreOS with those outputs: brand kit, personas, goals,
   competitors, knowledge base.
3. Build the channel plan, funnel architecture, and content calendar
   BEFORE producing content or spending budget.
4. Align collateral, pipeline stages, and sequences to the Omni-Narrative
   before the first Presence campaign goes live.
5. Deploy CSAT/loyalty/referral infrastructure BEFORE you close enough
   customers for it to matter.
6. Set the tracking cadence on Day 1: weekly briefings, monthly
   attribution review, quarterly framework reset.
