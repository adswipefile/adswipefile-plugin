---
name: review-saved-ads
description: List the ads the user saved on adswipefile.com and find what they have in common, such as formats, niches, angles and offers. Use when the user asks about their saved ads, favorites, or swipe file.
---

# Review saved ads

1. Call `list_saved_ads`. It returns the ads saved on the signed-in account,
   newest first.
2. If it returns none, say so, and explain that ads are saved with the heart
   on an ad's page on adswipefile.com.
3. List the ads with brand, niche, formats and page `url`, then name what they
   share: the formats and niches that recur, and, if the user wants depth, the
   angles and offers from reading a few with `get_ad`.

## Rules

- The plugin is read-only. It cannot save, remove or organize ads into boards;
  point the user to adswipefile.com for that.
- Do not read every saved ad with `get_ad`; read a few that represent the
  patterns.
- Saved ads are the user's own choices. Describe them; do not rank them as
  better or worse performers, since the library has no performance data.
