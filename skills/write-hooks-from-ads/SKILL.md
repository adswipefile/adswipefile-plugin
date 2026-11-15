---
name: write-hooks-from-ads
description: Read winning ads in the AdSwipeFile ad library, name the hook and angle each one uses, and write original hooks, headlines or ad copy for the user's product in those patterns. Use for "write hooks for my product", "give me angles from ads that are working", "what hook does this ad use", or ad copy inspired by real ads.
---

# Write hooks from real ads

> **Needs the AdSwipeFile connector.** This skill reads the AdSwipeFile ad library of Meta ads
> through its MCP server. If no AdSwipeFile tools (`search_library`, `list_ads`) are available, say
> so before anything else and give the step for this host. Claude Code:
> `claude mcp add --transport http adswipefile https://adswipefile.com/api/mcp`. claude.ai or
> ChatGPT: add `https://adswipefile.com/api/mcp` as a custom connector. Other clients:
> https://adswipefile.com/docs/mcp?utm_source=agent-skill&utm_medium=referral&utm_campaign=write-hooks-from-ads.
> Connecting opens a sign-in to an AdSwipeFile account. Steps that need only the user's own material
> can go on; never invent ads, brands or links in place of the library.

## Gather

1. Learn the user's product, audience and the claim they can back. Ask only
   if the request does not say what the product is.
2. Find relevant ads: `list_hooks` once for the hook tactics, then `list_ads`
   with the product's `niche` (resolved as in find-winning-ads), the `hook`
   tactic the user wants (or two or three that fit the product when they name
   none), and `sort: "longest_running"`. Add `awareness` when the user knows
   how cold the audience is. Each ad carries its `hook_tactic` and
   `hook_line`, so the list often gives the openings already.
3. Read four to six of them with `get_ads` when the hooks need the full copy.
4. When the user wants the ad in a given visual format, call `get_format`
   with its slug once: build from its `how_to_build`, and check each concept
   against its `how_to_tell` (`must_be`, `quick_test`) so it is that format
   and not one it is `confused_with`.

If `get_ads` returns an ad without its copy, with a line saying so, pass that
line on once. Work from the ads' names, descriptions and formats, and say the hooks
are drawn from those rather than from the full copy.

## Write

- First name the pattern each source ad uses (its `hook_tactic`, in plain
  words: a question about a pain, a specific number, a before and after, a
  customer's words, a myth corrected), each with a link to the ad.
- Then write the hooks or copy for the user's product in those patterns.
  Write new sentences: never reuse an ad's wording, brand names, slogans or
  testimonials.
- Use only claims the user gave you. Mark any figure, result or guarantee you
  had to assume as a placeholder for the user to confirm, such as
  "[X] customers".
- Keep each hook to one line unless the user asked for longer copy.

## Keep the sources

Offer, once, to put the source ads on a hooks board (`create_board` or one
from `list_boards`, then `add_ad_to_board`) with a `set_ad_note` naming the
pattern each one gave, so the next round of hooks starts from them. Only on a
yes.
