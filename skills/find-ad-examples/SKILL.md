---
name: find-ad-examples
description: Find real ad examples in AdSwipeFile by niche, format, brand or keyword and present them with links. Use when the user wants ad inspiration, examples of a format (UGC, before and after, testimonial, comparison), or ads from an industry.
---

# Find ad examples

## Resolve names to slugs first

`list_ads` filters on slugs. Turn the user's words into them before listing:

- A product, idea or loose phrase ("protein powder", "sleep gummies"): call
  `search_library` and use the brands, niches or ads it returns.
- An industry ("skincare", "SaaS"): match it against `list_niches`. Niches are
  broad (skincare sits under Beauty / Personal Care), so pick the closest and
  say which one you used.
- A format ("UGC", "before/after", "reviews"): match it against `list_formats`.
- A brand: call `search_library` with its name. If no brand matches, say the
  library does not have it rather than substituting another brand.

Call each list tool at most once per conversation; reuse what it returned.

## List and present

- Call `list_ads` with the slugs, and a `limit` close to what the user asked
  for. Results are the newest additions to the library first.
- For each ad give the brand, niche, formats and its page `url`. Show the
  `image` when the host renders images.
- `created_at` is when the ad was added to the library, not when it ran.
  Never call it a launch or run date.
- If fewer ads match than asked, say how many there are. Offer to widen the
  search (drop the format, or try a neighbouring niche) instead of padding.
- Use `nextCursor` only when the user asks for more.

Only read an ad in full with `get_ad` when the user wants its copy, or when the
task needs the copy (see the write-hooks-from-ads skill).
