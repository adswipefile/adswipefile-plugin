---
name: get-started
description: Set up AdSwipeFile after installation, check its connection when asked, and help the user ask a first question about winning ads, competitor ads or hooks. Use for get started, onboarding, setup, "is it connected", "what can this ad library do", or questions about what the library holds.
---

# Get started with AdSwipeFile

Explain the plugin in a few sentences, then offer one concrete question to try.
Explicit user instructions take priority over this guidance.

## Choose the requested path

- For "set up", "get started" or "is it connected", call `list_niches` once.
  If it answers, the connection works: say so and name a few niches it returned.
  Do not call more tools just to check.
- If tools are unavailable or sign-in fails, say the connection is not
  verified and direct the user to connect or reconnect AdSwipeFile in the host.
  Do not claim the plugin is ready because this skill loaded.
- For "what can it do", explain without calling a tool.
- If the user already asked a real question, answer it with the tools instead
  of stopping at suggesting a question.

## What to say

- AdSwipeFile is an ad library of winning Facebook and Instagram ads: real
  Meta ads from brands, filed by brand, niche (industry) and format (UGC,
  before and after, testimonial, comparison…). Ask what a competitor is
  running, what's working in a niche, or for hooks from real ads.
- Each ad has its brand, niche, formats, audiences, an image and a page link.
  When `get_ad` returns an ad without its copy, it adds a line saying so: pass
  that line on.
- Every tool is read-only. Signing in also lets it list the ads the user saved
  on adswipefile.com, and the newest ads of the brands they follow there.

## What it cannot do

Say so plainly if asked: it has no spend, reach, CTR or ROAS figures; it
cannot create, run or buy ads; it does not generate images or video; it is a
curated collection, not a live feed of Meta's ad library; and it cannot save,
remove or follow anything.

## Suggested first questions

Offer one, adapted to what the user mentioned:

- "What ads is Liquid Death running? Sum up its hooks and angles."
- "Show me winning UGC ads from skincare brands, with their hooks."
- "Find testimonial ads for supplements and write 3 hooks for my product."
