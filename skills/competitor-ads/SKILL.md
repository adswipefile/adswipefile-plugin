---
name: competitor-ads
description: Show what ads a brand or competitor is running in the AdSwipeFile ad library, and sum up the formats, hooks, angles and offers it repeats, with a link to every ad cited. Use for "what ads is {brand} running", "show me my competitor's Facebook ads", competitor research, spying on a competitor's creatives, or a brand creative teardown.
---

# Competitor ads

> **Needs the AdSwipeFile connector.** This skill reads the AdSwipeFile ad library of Meta ads
> through its MCP server. If no AdSwipeFile tools (`search_library`, `list_ads`) are available, say
> so before anything else and give the step for this host. Claude Code:
> `claude mcp add --transport http adswipefile https://adswipefile.com/api/mcp`. claude.ai or
> ChatGPT: add `https://adswipefile.com/api/mcp` as a custom connector. Other clients:
> https://adswipefile.com/docs/mcp?utm_source=agent-skill&utm_medium=referral&utm_campaign=competitor-ads.
> Connecting opens a sign-in to an AdSwipeFile account. Steps that need only the user's own material
> can go on; never invent ads, brands or links in place of the library.

1. Find the brand with `search_library`. If no brand matches, say the library
   does not have it; do not tear down a similar brand instead.
2. Call `list_ads` with the brand slug (`limit` 20 to 30). Count the formats
   and niches across the results.
3. Read a sample of five to eight ads with `get_ad`, spread across the formats
   you counted, for their copy and audiences. Keep to that sample; do not
   read every ad.
4. Report:
   - **Formats**: which ones the brand leans on, with counts from step 2.
   - **Angles and hooks**: the recurring promises, pains and openings, each
     with a link to an ad that shows it.
   - **Offers**: discounts, bundles, guarantees or free trials that appear.
   - **Audiences**: who the ads address, from the `audiences` field.
5. If the user follows the brand on AdSwipeFile, `list_followed_ads` adds its
   newest Meta ads, launched since the library last filed them. Cite each with
   its `url`.

## Rules

- Base every claim on an ad you listed or read, and link that ad's `url`.
- Say the teardown covers the brand's ads in this library, not everything the
  brand has run.
- Never state an ad's results: spend, ROAS, conversions, or that one ad beat
  another. The library holds no such data. "Winning" in this library means an
  ad the brand kept running and that was filed as worth studying; a long run
  (`sort: "longest_running"`) or many variants is a reason to study an ad,
  not proof that it performed.
- If `get_ad` returns an ad without its copy, with a line saying so, base the
  angles on the ad's name, description and formats, and pass that line on once.

## Keep watching it

Offer, once, to follow the brand (`follow_brand`) so its new ads show up in
`list_followed_ads` and the weekly review, and to save the ads cited
(`save_ad`) or put them on a board for this competitor (`create_board`,
`add_ad_to_board`). Only on a yes.
