# WundertreOS tool map (by hub)

`tools/list` on the MCP server is always authoritative — a credential only
sees tools its scopes allow. This map is for orientation: what lives where and
which tools chain naturally. Mutating tools are marked ✎ (they take effect
immediately and are audit-logged).

## CRM (crm:read / crm:write)
- Find & read: `list_contacts` (filters: status, source, days, search, tag,
  list_name; returns exact `total_count` + `by_status`/`by_source`),
  `get_contact_details`, `get_contact_activities`, `list_companies`,
  `get_company`, `list_contact_lists`, `get_contact_attribution_breakdown`
- Write ✎: `create_contact`, `update_contact`, `add_contact_note`,
  `add_contact_tag`/`remove_contact_tag`, `add_contact_to_list`/
  `remove_contact_from_list`, `set_contact_custom_field`, `create_company`,
  `update_company`, `link_contact_to_company`, `delete_contact`,
  `unsubscribe_contact`

## Sales (crm family)
- Read: `get_pipeline_summary` (org-wide totals + by-stage),
  `get_deals`, `get_deal_activities`, `list_pipelines_and_stages`,
  `list_tasks`, `list_quotes`, `get_quote`, `get_quote_pipeline_stats`,
  `list_documents`, `get_document`, `get_document_pipeline`, `list_products`
- Write ✎: `create_deal`, `update_deal`, `mark_deal_won`/`mark_deal_lost`,
  `add_deal_note`, `create_task`/`complete_task`, pipeline stage editing,
  `create_document_from_template`, `create_product`/`update_product`

## Prospecting (prospecting:*)
- `list_prospect_lists`, `get_prospect_list`, `list_prospects`,
  `analyze_lead`, `delete_prospect_list` ✎

## Social (social:*)
- Read: `get_social_post_performance`, `list_social_inbox_threads`,
  `get_social_thread_messages`, `list_social_comments`
- Write ✎: `create_social_post` (publish now or draft),
  `schedule_social_post`, `reply_social_comment`
- Personas ground the voice: `list_personas`, `get_persona`

## Ads (ads:*)
- Read: `get_ad_performance` (window totals + by-platform),
  `get_top_creatives`, `suggest_ad_optimizations`, `search_ads`,
  `get_lsa_leads` (Google Local Services), `get_ctv_status`
- Write ✎: `create_ad_campaign`, `update_ad_campaign`,
  `set_ad_campaign_status` (pauses/resumes the LIVE platform campaign),
  `duplicate_ad_campaign`, `launch_ctv_campaign`

## Marketing (marketing:*)
- Read: `list_email_campaigns`, `get_email_campaign_performance`
  (open/click rates are over delivered), `list_sms_campaigns`,
  `get_sms_campaign_performance`, `list_email_templates`, `list_workflows`
- Write ✎: `create_email_campaign_from_template`, `create_sms_campaign`,
  pause/resume/cancel tools, `send_email_to_contact`, `send_sms_to_contact`,
  `create_workflow`/`update_workflow`, `enroll_in_workflow`

## Web presence (web:*)
- Read: `list_websites`, `list_website_pages`, `get_website_content` (yes,
  you can read the actual page HTML/copy), `list_landing_pages`,
  `get_landing_page_content`, `list_forms`, `get_form_submissions` (exact
  `total_count`), `get_website_generation_status`, `list_funnels`,
  `get_funnel`, `list_listings`, `list_booking_pages`, `get_booking_stats`
- Write ✎: `create_website` (AI-generates a new site + homepage draft,
  ~30-60s), `expand_website` (background multi-page build — poll
  `get_website_generation_status`), `publish_website` (deploys live),
  `generate_landing_page`, `publish_landing_page`,
  `update_landing_page_content`, `create_form`/`update_form`, `build_funnel`
  (end-to-end funnel in one call), `update_booking_page`

## Analytics / CRO (insights:read, web:read)
- `get_funnel_metrics` (sessions → events → form captures + conversion rate),
  `get_top_pages`, `get_traffic_sources`, `get_pixel_health`,
  `lookup_visitor_identity`, `get_dni_swap_stats`, `get_report_data`,
  `analyze_business_performance`, `get_recent_audit_events`

## Support (support:*)
- Read: `list_tickets`, `get_ticket`, `get_open_tickets`, `get_csat_summary`,
  `list_kb_articles`, `get_chatbot_conversations`
- Write ✎: `create_ticket`, `reply_to_ticket` (emails the contact),
  `update_ticket`, `close_ticket`/`reopen_ticket`, `update_chatbot_config`,
  `add_chatbot_knowledge`

## Retention (support/crm families)
- Memberships: `get_membership_metrics` (MRR), `list_memberships`,
  `enroll_member` ✎, `change_membership_plan` ✎, `cancel_membership` ✎
- Loyalty: `get_loyalty_account`, `adjust_loyalty_points` ✎
- Referrals: `get_referral_performance`, `list_referrals`,
  `send_referral_invite` ✎ (creates the lead + sends the email),
  `mark_referral_converted` ✎
- Scheduled services: `list_scheduled_services`

## Content & knowledge (content:*, knowledge:*)
- `generate_copy`, `generate_image` (brand-grounded), `list_storycraft_copy`
- `get_persona`/`upsert_persona` ✎, `upsert_goal` ✎, `list_competitors`/
  `upsert_competitor` ✎, `update_business_profile` ✎
- Research: `search_keywords`, `run_serp_check`, `analyze_competitor_domain`,
  `get_trending_content`, `analyze_buzz`
