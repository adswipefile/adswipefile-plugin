---
name: find-winning-ads
description: Find winning Facebook and Instagram ads in the AdSwipeFile ad library by niche, format, brand or keyword, and present them with links. Use for "show me winning ads in {niche}", "what's working in {niche} right now", ad inspiration, ad examples, or examples of a format (UGC, before and after, testimonial, comparison).
---

# Find winning ads

> **Needs the AdSwipeFile connector.** This skill reads the AdSwipeFile ad library of Meta ads
> through its MCP server. If no AdSwipeFile tools (`search_library`, `list_ads`) are available, say
> so before anything else and give the step for this host. Claude Code:
> `claude mcp add --transport http adswipefile https://adswipefile.com/api/mcp`. claude.ai or
> ChatGPT: add `https://adswipefile.com/api/mcp` as a custom connector. Other clients:
> https://adswipefile.com/docs/mcp?utm_source=agent-skill&utm_medium=referral&utm_campaign=find-winning-ads.
> Connecting opens a sign-in to an AdSwipeFile account. Steps that need only the user's own material
> can go on; never invent ads, brands or links in place of the library.

## Resolve names to slugs first

`list_ads` filters on slugs. Turn the user's words into them before listing:

- A product, idea or loose phrase ("protein powder", "sleep gummies"): call
  `search_library` and use the brands, niches or ads it returns.
- An industry ("skincare", "SaaS"): match it against `list_niches`. Niches are
  broad (skincare sits under Beauty / Personal Care), so pick the closest and
  say which one you used.
- A format ("UGC", "before/after", "reviews"): match it against
  `list_visual_formats` and filter `list_ads` by `visual_format`. When the
  user asks what makes an ad that format, or which format an ad is, call
  `get_format` with the slug: it says what must hold, the near misses and the
  formats it is mixed up with.
- A move or a stage ("objection handling", "cold traffic"): filter
  `list_ads` by `mechanic` (the slugs in pick-creative-mechanic) or
  `awareness` (`unaware` to `most-aware`).
- A brand: call `search_library` with its name. If no brand matches, say the
  library does not have it rather than substituting another brand, and offer
  to report it with `submit_feedback`.

Call each list tool at most once per conversation; reuse what it returned.

## List and present

- Call `list_ads` with the slugs, and a `limit` close to what the user asked
  for. Results are the newest additions to the library first. For "what's
  working" or "what's been running longest", pass `sort: "longest_running"`;
  a long run is a reason to study an ad, not proof of its results.
- For each ad give the brand, niche, formats and its page `url`. Show the
  `image` when the host renders images.
- `created_at` is when the ad was added to the library, not when it ran.
  Never call it a launch or run date.
- If fewer ads match than asked, say how many there are. Offer to widen the
  search (drop the format, or try a neighbouring niche) instead of padding.
- Use `nextCursor` only when the user asks for more. When the list answers
  with a `note` that it was cut short, pass it on once with its link and
  narrow with filters instead of paging.

Only read an ad in full with `get_ad` when the user wants its copy, or when the
task needs the copy (see the write-hooks-from-ads skill).

## Keep the ones worth keeping

Offer, once, to keep the ads the user likes: `save_ad`, or a board named for
the search (`create_board`, `add_ad_to_board`), with a `set_ad_note` on why
each is worth studying. Only on a yes.
