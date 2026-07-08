---
name: orf-social-engine
description: Omni-Revenue Framework play (Tenet 2, Omni-Presence) — run a persona-grounded social content engine on WundertreOS. Plan a content calendar, generate on-brand posts and images, schedule them, and iterate from performance. Use when the user wants social posts, a content calendar, "post for me", or asks why social isn't producing.
---

# Play: The Social Engine (Tenet 2 — Omni-Presence)

Omni-Presence is not being everywhere on the internet — it's being
everywhere in **your specific buyer's** internet, with one identical promise
carried natively on each channel. Content is currency: the primary mechanism
for building authority and trust before the sales conversation begins. This
play makes that consistent instead of random acts of posting, and it feeds
the lead engine.

## 1. Ground in the brand

Always before writing anything:
- `list_personas` → `get_persona` for the audience being addressed.
- `get_persona`'s tone + pains drive angles; `list_competitors` /
  `get_trending_content` / `analyze_buzz` supply topical hooks.
- `get_social_post_performance` (last 30-90 days) — what already worked?
  Double down on formats/topics with real engagement; don't repeat duds.

## 2. Plan the calendar

Propose a 2-week calendar: mix of value (educate), proof (reviews, befores/
afters), offer (CTA to the landing page / booking page), and local/timely
(`lookup_holidays`). Each entry: platform(s), angle, CTA, asset needed. Get
one approval on the whole calendar, not per post.

## 3. Produce

Per post:
- `generate_copy` (persona + platform in the prompt) — present the copy,
  refine to taste.
- Visual: `generate_image` when no brand asset fits.
- CTA links only to URLs that exist (`list_landing_pages`,
  `list_booking_pages` — never invent slugs).

## 4. Ship

- `schedule_social_post` for calendar entries (returns the scheduled time —
  quote it); `create_social_post` for post-now.
- Stagger platforms; don't fire everything at the same minute.

## 5. Close the loop

- Weekly: `get_social_post_performance` — engagement by post; feed learnings
  into the next calendar.
- Inbox is part of social: `list_social_inbox_threads` (unread),
  `list_social_comments` — flag threads needing a human, draft replies with
  `reply_social_comment` for approval.

## Guardrails

- Publishing is outward-facing: the user approves copy + image + timing
  before anything ships.
- The voice belongs to the persona doc, not to you — when in doubt, quote
  the persona's tone words back and ask.
