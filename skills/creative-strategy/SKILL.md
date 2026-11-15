---
name: creative-strategy
description: Start here for creative strategy on Meta ads with AdSwipeFile as the evidence. Routes research, ideation, making, review and learning to the right skill, from mapping competitors to concepts, scripts and audits. Use for "help me with creative strategy", "where do I start with my ads", "build a creative strategy for my brand", ad concepts, competitor research or a creative brief.
---

# Creative strategy

> **Needs the AdSwipeFile connector.** This skill reads the AdSwipeFile ad library of Meta ads
> through its MCP server. If no AdSwipeFile tools (`search_library`, `list_ads`) are available, say
> so before anything else and give the step for this host. Claude Code:
> `claude mcp add --transport http adswipefile https://adswipefile.com/api/mcp`. claude.ai or
> ChatGPT: add `https://adswipefile.com/api/mcp` as a custom connector. Other clients:
> https://adswipefile.com/docs/mcp?utm_source=agent-skill&utm_medium=referral&utm_campaign=creative-strategy.
> Connecting opens a sign-in to an AdSwipeFile account. Steps that need only the user's own material
> can go on; never invent ads, brands or links in place of the library.

These skills work one loop: research, ideate, make, review, learn. Two kinds of material feed it:

- **Other brands' public Meta ads**, from the AdSwipeFile tools: copy, tags, breakdowns, run dates.
  They show how ads are built, never how they performed.
- **The user's own material**: product facts, customer reviews, their ads and their results. It
  comes from the user: pasted, uploaded, linked, or from another connector they have. Ask for it
  plainly; never invent it.

Words, evidence rules and the tools by job live in [REFERENCE.md](REFERENCE.md). Read it once before
the first skill.

## Skills

| Stage | Skill | Ends in |
| --- | --- | --- |
| Research | `map-competitors` | A competitor map: direct, indirect, admired |
| Research | `track-competitor-ads` | Competitors followed on AdSwipeFile, a first read per brand |
| Research | `weekly-competitor-review` | A short weekly review of what followed brands launched |
| Research | `competitor-ads` | One brand's formats, hooks, angles and offers, linked |
| Research | `map-personas` | Personas with anchors, trigger moments and the user's customer words |
| Research | `find-winning-ads` | Linked reference ads for a niche, format or keyword |
| Ideate | `generate-ad-concepts` | Draft concepts, one per anchor, persona and moment |
| Ideate | `pick-creative-mechanic` | The mechanic each concept uses, with reference ads |
| Ideate | `write-hooks-from-ads` | Original hooks and headlines in patterns from real ads |
| Review | `audit-ad-creative` | Feedback on one ad and an iteration brief |
| Learn | `teach-ad-breakdown` | A breakdown of one ad and the takeaway to reuse |
| Learn | `review-saved-ads` | What the user's saved ads have in common |
| Learn | `record-creative-learning` | A scoped learning from the user's own results |

## Usual order for a new brand

1. `map-competitors`, then `track-competitor-ads` to follow them and read what they keep running.
2. `map-personas` from the user's reviews and customer words.
3. `generate-ad-concepts`, picking a mechanic per concept with `pick-creative-mechanic` and hooks
   with `write-hooks-from-ads`.
4. `audit-ad-creative` on what is about to ship.
5. Once the user has results from their own ads, `record-creative-learning`.
6. Every week, `weekly-competitor-review`, by hand or as a scheduled task.

Pick up at any stage the user is already at. A single question ("what is this brand running?")
goes straight to its skill.

## Rules

- Outputs go in the reply, or in a file when the client can write files. Keep references on
  AdSwipeFile (`save_ad`, `add_ad_to_board`, `create_board`, `set_ad_note`) only when the user asks
  or agrees.
- Every cited ad is linked by its `url`. The library holds no spend, ROAS or conversions: a long
  run is a reason to study an ad, never proof it worked.
- Results-type calls count against the user's calls: read samples with `get_ads`, keep calls few.
  Before a long run of calls (a batch of concepts, several competitors), `get_usage` says how many
  are left, at no cost.
- A list or search cut short answers with a `note`: pass it on once with its link, work from what
  came, and narrow with filters instead of paging.
- One client or brand among several (an agency): `list_workspaces` once, then pass that client's
  `workspace` to every save, follow and board, so each client's research stays apart.
- A board of references is the deliverable a client or team sees: once it is filed, offer
  `share_board` for a read-only link.
- A brand or result the library is missing: offer to report it with `submit_feedback`, once, with
  the user's go-ahead.
