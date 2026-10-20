---
name: brand-teardown
description: Summarize what a brand advertises in AdSwipeFile, the formats, angles, hooks and offers it repeats, with a link to every ad cited. Use for competitor research, "what does this brand run", or brand creative teardowns.
---

# Brand teardown

1. Find the brand with `search_library`. If no brand matches, say the library
   does not have it; do not tear down a similar brand instead.
2. Call `list_ads` with the brand slug (`limit` 20 to 30). Count the formats
   and niches across the results.
3. Read a sample of five to eight ads with `get_ad`, spread across the formats
   you counted, for their copy and audiences. Every call counts against the
   account's monthly allowance, so do not read every ad.
4. Report:
   - **Formats**: which ones the brand leans on, with counts from step 2.
   - **Angles and hooks**: the recurring promises, pains and openings, each
     with a link to an ad that shows it.
   - **Offers**: discounts, bundles, guarantees or free trials that appear.
   - **Audiences**: who the ads address, from the `audiences` field.

## Rules

- Base every claim on an ad you listed or read, and link that ad's `url`.
- Say the teardown covers the brand's ads in this library, not everything the
  brand has run.
- The library has no spend or performance data. Do not call an ad a winner, a
  top performer or a scaled ad because it appears more than once.
- If `get_ad` returns no copy and a line on how to unlock it, base the angles
  on the ad's name, description and formats, and pass that line on once.
