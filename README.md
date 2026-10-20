# AdSwipeFile plugin

Winning ad creative for Claude, ChatGPT and Codex: search a library of ads
from top brands on Meta (Facebook, Instagram), TikTok, LinkedIn and more, by
brand, niche and format.

[AdSwipeFile](https://adswipefile.com) files each ad with its brand, niche
(industry), formats (UGC, before and after, testimonial, comparison…),
audiences and copy. This plugin connects your AI assistant to the library over
MCP and adds skills that tell it how to research and cite ads well.

## What you can ask

- "Show me 5 recent UGC ads from beauty brands."
- "Find ads about protein powder."
- "What does Liquid Death advertise, and which angles does it repeat?"
- "Find testimonial ads for supplements and write 3 hooks for my product."
- "Show me the ads I've saved and what they have in common."

## What is in here

| Path | |
| --- | --- |
| `plugin.json`, `mcp.json` | The plugin in the [Agent Plugins](https://agent-plugins.org) format, for ChatGPT, Codex and other clients |
| `.codex-plugin/plugin.json` | Codex manifest |
| `.claude-plugin/plugin.json` | Claude plugin manifest |
| `.claude-plugin/marketplace.json` | Marketplace entry, so this repo can be added as a Claude Code marketplace |
| `.cursor-plugin/`, `.grok-plugin/` | Cursor and Grok manifests |
| `.mcp.json` | The remote MCP server, `https://adswipefile.com/api/mcp` |
| `skills/` | Five skills: get started, find ad examples, brand teardown, write hooks from ads, review saved ads |
| `assets/` | Icon |

The skills are plain Markdown instructions. The plugin ships no scripts, hooks
or executables and installs no packages.

## Install

**ChatGPT**: use the root `plugin.json` and `mcp.json`.

**Claude Code**

```bash
claude plugin marketplace add adswipefile/adswipefile-plugin
claude plugin install adswipefile@adswipefile
```

**Codex**: install from this repository; it reads `.codex-plugin/plugin.json`.

**Any MCP client, without the skills**

```bash
claude mcp add --transport http adswipefile https://adswipefile.com/api/mcp
```

On claude.ai or ChatGPT, add `https://adswipefile.com/api/mcp` as a custom
connector. Setup for other clients: https://adswipefile.com/docs/mcp.

## Sign-in and the data it sends

Connecting opens a browser sign-in to your AdSwipeFile account (OAuth 2.1). A
free account works; there is no API key to copy. The plugin asks for read
access to the ad library and to the ads you saved on the site. Every tool is
read-only: it cannot change your account, your saved ads or your boards.

The plugin talks to one server, `adswipefile.com`. When the assistant calls a
tool, the tool's arguments, such as a search query or a brand, niche or format,
are sent to that server. AdSwipeFile records each tool call in its product
analytics (PostHog): the tool name, its arguments, timing, errors, the AI
client's name and your account identifier. Each call also counts against your
account's monthly allowance. Nothing else from your conversation or your
machine is sent. See the [privacy policy](https://adswipefile.com/privacy).

## Scope

AdSwipeFile is a reference library of ad creative. It holds no spend, reach or
performance figures, cannot create, run or buy ads, and does not generate
images or video. It is a curated collection updated by periodic imports, not a
live feed of Meta's or TikTok's ad libraries. Depending on your plan, an ad's
copy may need an upgrade on adswipefile.com.

## Support

[adswipefile.com/contact](https://adswipefile.com/contact) or
hello@adswipefile.com. Report security issues as described in
[SECURITY.md](./SECURITY.md).
