---
name: review-saved-ads
description: List the ads the user saved on adswipefile.com and find what they have in common: formats, niches, hooks, angles and offers. Use for "show me the ads I saved", "what do my saved ads have in common", their favorites, boards or swipe file.
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

- To organize them, use the board tools when the user asks: `list_boards`
  for the boards they have, then `add_ad_to_board`, `remove_ad_from_board`,
  `create_board`, `rename_board` or `share_board`; `set_ad_note` to write down
  why an ad is worth keeping; `save_ad` and `unsave_ad` for the saves
  themselves. Confirm before `delete_board`, and before `unsave_ad` on an ad
  that is on a board. Change nothing the user did not ask for.
- Do not read every saved ad with `get_ad`; read a few that represent the
  patterns.
- Saved ads are the user's own choices. Describe them; do not rank them as
  better or worse performers, since the library has no performance data.
