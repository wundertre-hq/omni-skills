---
name: wundertre-os-operator
description: Operate a business on WundertreOS through its MCP tools — CRM, deals, prospecting, social, ads, email/SMS marketing, web presence, support, memberships, and analytics. Use whenever the WundertreOS connector is available and the user asks about their contacts, pipeline, campaigns, posts, tickets, bookings, website, or business numbers, or asks you to create/update any of those.
---

# Operating WundertreOS

WundertreOS is an all-in-one platform for local businesses. The MCP connector
exposes the same tools the platform's own assistant (Wunder) uses, scoped to
one organization and filtered by the credential's scopes. `tools/list` is
authoritative — if a tool named here is missing, the credential lacks that
scope; say so rather than improvising.

## Conventions that keep you honest

**Totals vs pages.** List tools return one *page* of records plus exact
aggregate fields. Always quote the aggregate, never the array length:
- `total_count` (contacts, companies, form submissions), `org_total_deals`
  (deals), `total` (LSA leads, documents, quotes), `count` (scheduled
  services) are exact counts over the whole filtered set.
- `returned` is the page size. A result with `returned: 50, total_count: 340`
  means "340 exist; here are 50."
- When a result includes a `note`, read it — it states exactly what the
  numbers cover, including when a very large scan was sampled.

**Mutations are immediate and audited.** Tools that create, update, send, or
delete take effect the moment they run and are written to the org's audit log.
Confirm intent with your user before anything outward-facing (emails, SMS,
social posts, ad changes) or destructive (deletes, cancellations). Reads are
always safe to call freely.

**Errors are structured.** Handlers return `{ error: "..." }` rather than
throwing. Read the message — it usually says what to fix (a missing filter, a
name that matched nothing). "No X found" from a fuzzy-match tool means try a
shorter or different query string, not that the record is gone.

**Fuzzy matching.** Contact/company/campaign/list arguments named `*_query` or
`*_name` are fuzzy (case-insensitive substring, multi-word tokens). Prefer the
person's name or email over IDs; if a match is ambiguous, fetch details and
verify before mutating.

**Rate limit.** 60 requests/minute per org. Batch your reads (one list call
with filters beats N lookups) and don't poll.

## Hub map — where things live

- **CRM**: contacts, companies, lists, tags, custom fields, activities,
  attribution (`list_contacts`, `get_contact_details`,
  `get_contact_attribution_breakdown`, …)
- **Sales**: pipelines, deals, tasks, quotes, documents/e-sign, products
  (`get_pipeline_summary`, `create_deal`, `mark_deal_won`, …)
- **Prospecting**: prospect lists, lead analysis (`list_prospects`,
  `analyze_lead`, …)
- **Social**: posts, scheduling, inbox threads, comments, personas
  (`create_social_post`, `schedule_social_post`, `list_social_inbox_threads`, …)
- **Ads**: campaigns across Meta/Google, performance, optimization, CTV, LSA
  (`get_ad_performance`, `create_ad_campaign`, `set_ad_campaign_status`,
  `get_lsa_leads`, …)
- **Marketing**: email/SMS campaigns and templates, drip workflows, forms
  (`create_email_campaign_from_template`, `get_email_campaign_performance`, …)
- **Web presence**: websites and landing pages, funnels, listings, booking
  pages, pixel/CRO analytics (`list_websites`, `update_landing_page_content`,
  `get_top_pages`, `get_traffic_sources`, `build_funnel`, …)
- **Support**: tickets, replies, CSAT, chatbots (`list_tickets`,
  `reply_to_ticket`, `get_csat_summary`, …)
- **Retention**: memberships, loyalty, referrals, scheduled services
  (`get_membership_metrics`, `send_referral_invite`, `adjust_loyalty_points`, …)
- **Insights**: cross-hub reporting (`get_report_data`,
  `analyze_business_performance`, `get_recent_audit_events`)
- **Content**: AI copy and image generation grounded in the org's brand
  (`generate_copy`, `generate_image`, `list_storycraft_copy`)
- **Knowledge**: personas, goals, competitors, AI knowledge entries
  (`get_persona`, `upsert_persona`, `upsert_goal`, `upsert_competitor`)

For the full per-hub tool inventory, read `references/tool-map.md`.

## Working style

1. **Read before you write.** Pull current state (the contact, the campaign,
   the page) before proposing a change; reference what's actually there.
2. **Chain, don't dump.** Most valuable work is 2–5 tools composed:
   find → inspect → act → verify. After a mutation, do the cheap verification
   read and report what changed.
3. **Numbers come from tools, not memory.** Any count, rate, or dollar figure
   you state must come from a tool result in this conversation.
4. **Respect the persona.** Content tools (`generate_copy`, social posts,
   email) are grounded in org personas and brand assets — fetch
   `list_personas`/`get_persona` first when writing on the org's behalf.
