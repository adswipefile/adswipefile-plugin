---
name: write-hooks-from-ads
description: Read winning ads in the AdSwipeFile ad library, name the hook and angle each one uses, and write original hooks, headlines or ad copy for the user's product in those patterns. Use for "write hooks for my product", "give me angles from ads that are working", "what hook does this ad use", or ad copy inspired by real ads.
---

# Write hooks from real ads

## Gather

1. Learn the user's product, audience and the claim they can back. Ask only
   if the request does not say what the product is.
2. Find relevant ads (see find-winning-ads): the product's niche, and the
   format the user wants, or Testimonial, Pain Point, Before & After and
   Comparison when they name none.
3. Read four to six of them with `get_ads` for their copy.
4. When the user wants the ad in a given visual format, call `get_format`
   with its slug once: build from its `how_to_build`, and check each concept
   against its `how_to_tell` (`must_be`, `quick_test`) so it is that format
   and not one it is `confused_with`.

If `get_ads` returns an ad without its copy, with a line saying so, pass that
line on once. Work from the ads' names, descriptions and formats, and say the hooks
are drawn from those rather than from the full copy.

## Write

- First name the pattern each source ad uses (a question about a pain, a
  specific number, a before and after, a customer's words, a myth corrected),
  each with a link to the ad.
- Then write the hooks or copy for the user's product in those patterns.
  Write new sentences: never reuse an ad's wording, brand names, slogans or
  testimonials.
- Use only claims the user gave you. Mark any figure, result or guarantee you
  had to assume as a placeholder for the user to confirm, such as
  "[X] customers".
- Keep each hook to one line unless the user asked for longer copy.
