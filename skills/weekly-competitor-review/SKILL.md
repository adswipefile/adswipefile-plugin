---
name: weekly-competitor-review
description: Write a short weekly review of the new Meta ads the user's followed brands launched on AdSwipeFile, what changed against each brand's usual patterns, and three ideas to try, with a link to every ad. Runs by hand or as a scheduled Claude routine or ChatGPT task. Use for "weekly competitor review", "what did my competitors launch this week", "competitor ads digest" or a recurring competitor report.
---

# Weekly competitor review

A short read of what followed brands launched in the window, set against what each brand usually
runs. Words and evidence rules: the creative-strategy skill's `REFERENCE.md`.

The window is the last 7 days, or since the date the user gives.

## Steps

1. `list_followed_ads`. Its `following` lists every follow, library brands and Facebook pages
   alike. If it is empty, the account follows nothing: explain that brands are followed on
   adswipefile.com/app/track (by name or Facebook page link), or offer `follow_brand` for brands the
   user names, and follow only with their go-ahead. Stop there.
2. Keep the ads whose `started` date falls in the window. Each followed page also carries
   `launched_last_7_days`. Count per brand: ads, formats, and the hooks and offers their copy
   (`title`, `body`, `cta`) shows.
3. `list_followed_brands` for the library slugs only (a page outside the library has none, so
   it has no filed ads to compare). For up to 5 library brands with new ads, in order of most new ads, `list_ads`
   with `brand`. The first page
   carries `brand_patterns` (most common structure, top visual format and hook tactic) to compare
   the new ads against, and lists the brand's filed ads newest first, with `run.started`.
4. Read 3 to 6 of the newest filed ads that started in the window with `get_ads`, one call, spread
   across brands, for their hook, structure and offer. Skip this step when none are filed yet.

## The review

Aim for under 350 words:

- **Headline**: one line on the week.
- **Per brand**: what launched (count, formats, hooks, offers) and what is new against its usual
  patterns, each point with a linked ad.
- **Across brands**: patterns more than one brand shows.
- **Three ideas to try** for the user's own ads, each tied to a linked ad.
- **Nothing new**: the followed brands with no ads in the window, in one line.

End with the window covered and the line: this covers only followed brands' ads AdSwipeFile pulled;
followed pages are checked weekly, so a brand's newest ad can be a few days old.

## Run unattended

When run as a scheduled routine or task: ask no questions, make no writes (no follows, saves or
boards), and say which window the review covered. When `list_followed_ads` shows no follows
(neither brands nor pages), say so in one line and point to adswipefile.com/app/track.

## Rules

- No results: never spend, ROAS, conversions, or that an ad works or beat another. A long run is a
  reason to study an ad, never proof.
- Link every ad by its `url`.
- Keep calls few: one `list_followed_brands`, one `list_followed_ads`, at most 5 `list_ads` and one
  `get_ads`.

Done when the review is written with every cited ad linked and the window stated. Next:
`teach-ad-breakdown` for an ad worth a closer look, or `generate-ad-concepts` to act on an idea.
