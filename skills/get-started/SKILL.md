---
name: get-started
description: Set up AdSwipeFile after installation, check its connection when asked, and help the user try a first question about ad creative. Use for get started, onboarding, setup, connection checks, or questions about what the library holds.
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

- AdSwipeFile is a curated library of real ads from brands on Meta (Facebook,
  Instagram), filed by brand, niche (industry) and format (UGC, before and
  after, testimonial, comparison…).
- Each ad has its brand, niche, formats, audiences, an image and a page link.
  When `get_ad` returns an ad without its copy, it adds a line saying so: pass
  that line on.
- Every tool is read-only. Signing in also lets it list the ads the user saved
  on adswipefile.com.

## What it cannot do

Say so plainly if asked: it has no spend, reach, CTR or ROAS figures; it
cannot create, run or buy ads; it does not generate images or video; it is a
curated collection, not a live feed of Meta's ad library; and it cannot save or remove ads.

## Suggested first questions

Offer one, adapted to what the user mentioned:

- "Show me 5 recent UGC ads from beauty brands."
- "What does Liquid Death advertise, and which angles does it repeat?"
- "Find testimonial ads for supplements and write 3 hooks for my product."
