---
name: orf-lead-engine
description: Omni-Revenue Framework play (Tenet 3, Omni-Narrative) — build or repair the lead engine on WundertreOS. Zero-friction conversion plus follow-up that runs itself, so interest becomes booked business and nothing falls through the cracks. Use when the user says leads are slipping, follow-up is manual, forms aren't converting, or they want "more leads" / "a lead system".
---

# Play: The Lead Engine (Tenet 3 — Omni-Narrative)

The framework's diagnosis: the biggest revenue leak is not a marketing
problem or a sales problem — it's a **handoff problem**. This play closes
the leak: every visitor has a way to raise their hand (the Tenet 2 capture
seam), every raised hand gets a next touch automatically, and the sales
conversation continues the marketing story instead of restarting it. Run
stages in order; each stage verifies before the next builds on it.

## 1. Verify the plumbing

- `get_pixel_health` — if the pixel isn't installed/firing, stop and fix
  that first (nothing downstream is measurable).
- `get_funnel_metrics` (30 days) — baseline: sessions, form captures,
  conversion rate. Save these numbers; you'll quote them at the end.
- `list_forms` + `get_form_submissions` — which forms exist and which
  actually receive submissions. `total_count` is exact.

## 2. Capture points

For each gap found:
- No landing page for the main offer → `generate_landing_page` (fetch
  `get_persona` first so the copy is persona-true), then
  `publish_landing_page` once the user approves the draft.
- No form on a high-traffic page → check `get_top_pages`, then
  `create_form` and place it.
- Phone-first business → confirm DNI (`list_dni_numbers`,
  `get_dni_swap_stats`) so calls attribute to sources.
- After-hours leads → `update_chatbot_config` + `add_chatbot_knowledge` so
  the chatbot answers and captures instead of losing them.

## 3. Follow-up that runs itself

- `list_workflows` — is there a new-lead workflow? If not:
  `create_workflow` with trigger on new contact/form submission, steps =
  immediate email (persona voice), SMS after N hours if no reply, task for
  the owner on day 2. Present the whole plan in one confirm.
- Wire the capture points to it: `enroll_in_workflow` for existing recent
  leads that never got touched (find them: `list_contacts` filtered by
  `days` + status "new").

## 4. Pipeline discipline

- `get_pipeline_summary` — stages sane? Deals rotting?
- For each recent lead with buying intent (check `get_contact_details` /
  `analyze_lead`), `create_deal` in the right stage and `create_task` for
  the next human touch.

## 5. Report the loop closed

End with before/after: "X sessions were producing Y leads/mo with no
follow-up; now every form/chat/call lands in the CRM, triggers the workflow
within minutes, and deals are created for sales-ready leads. Re-measure with
`get_funnel_metrics` in 2 weeks." Schedule that re-measure as part of
`orf-weekly-revenue-review`.

## Guardrails

- Outward-facing sends (email/SMS) and publishes always get explicit user
  approval first — preview the copy, don't just describe it.
- Never enroll contacts who are unsubscribed; the tools enforce it, but
  don't fight the error if it comes back.
- Quote only tool-returned numbers and URLs.
