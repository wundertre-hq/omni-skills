# Wundertre Omni Skills

Agent Skills that teach an AI agent (Claude, or any agent that supports the
[Agent Skills](https://github.com/anthropics/skills) standard) how to run a
business on **WundertreOS** — powered by the **Omni-Revenue Framework**,
Wundertre's five-tenet operating system for engineering revenue.

The WundertreOS MCP connector gives an agent **ability**: 200+ tools across
CRM, sales, prospecting, social, ads, email/SMS marketing, websites, support,
and analytics. These skills give it **judgment**: when to reach for which
tool, and the framework plays that chain tools into revenue.

## The skills

| Skill | What it teaches |
| --- | --- |
| [`wundertre-os-operator`](wundertre-os-operator/) | The base skill — install this one always. Tool conventions (exact totals vs pages, mutation safety, fuzzy matching), the hub map, and working style. |
| [`omni-revenue-framework`](omni-revenue-framework/) | The Omni-Revenue Framework: five tenets (Omni-Insight → Omni-Presence → Omni-Narrative → Omni-Service → Omni-Tracking), the flywheel, and the Revenue Audit entry play — all wired to live tools. |
| [`orf-lead-engine`](orf-lead-engine/) | Play (Tenet 3, Omni-Narrative): zero-friction conversion + follow-up that runs itself. |
| [`orf-social-engine`](orf-social-engine/) | Play (Tenet 2, Omni-Presence): persona-grounded content engine — plan, generate, schedule, measure, iterate. |
| [`orf-weekly-revenue-review`](orf-weekly-revenue-review/) | Play (Tenet 5, Omni-Tracking): measure everything, close the loop, feed the machine. |

## Prerequisites

A WundertreOS account with the MCP connector added. In Claude: **Settings →
Connectors → Add custom connector** → `https://os.wundertre.com/mcp` — the
sign-in flow is discovered automatically. Headless agents can use a
WundertreOS API key (created in Settings → API) as a bearer token instead.

Skills are plain markdown — no runtime, no dependencies, and they contain no
credentials. Your data access is governed entirely by the connector sign-in.

## Installing

**Claude Code (CLI, desktop, or web)**

```sh
npx skills add wundertre/omni-skills
```

or manually:

```sh
git clone https://github.com/wundertre/omni-skills
cp -r omni-skills/wundertre-os-operator ~/.claude/skills/   # plus any plays you want
```

(Use a project's `.claude/skills/` instead of `~/.claude/skills/` to scope
skills to one project.)

**Claude.ai / Claude Desktop (Skills capability)**

Zip a skill folder (the folder containing `SKILL.md`) and upload it under
**Settings → Capabilities → Skills**. Team/Enterprise admins can enable
skills org-wide.

**Other agents**

Any agent implementing the Agent Skills standard loads these folders as-is.
For agents without skills support, paste the relevant `SKILL.md` into the
system prompt — each file is written to stand alone.

## Using them

Once installed alongside the connector, just talk to your agent:

- *"Run a revenue audit on my business"* → the Revenue Audit play scores all
  five tenets from your live data and recommends a plan.
- *"Set up a lead system"* → the lead engine play builds capture + automatic
  follow-up end to end.
- *"Plan two weeks of social"* → the social engine play grounds a calendar
  in your personas and schedules it.
- *"How's the business doing?"* → the weekly revenue review, with honest
  numbers and next moves.

## Layout

Each skill is a folder with a `SKILL.md` (YAML frontmatter + instructions).
Heavier reference material lives in `references/` and is read only when
needed, so skills stay cheap in the agent's context until used.

## Versioning & source of truth

- The **tool surface** is versioned by the MCP server — `tools/list` is
  always authoritative for tool names and parameters.
- The **framework** is authoritative in its master document; these skills
  are its agent-executable edition.

## About

The Omni-Revenue Framework and these skills are © Wundertre
([wundertre.com](https://wundertre.com) · hello@wundertre.com).
WundertreOS is Wundertre's all-in-one revenue platform for local businesses.
