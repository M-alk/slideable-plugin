# Slideable — agent plugin

<img src="assets/logo.png" alt="Slideable" width="96" height="96">

Connects [Slideable](https://slideable.ai) to your agent, so it can build and
edit presentation decks out of a fixed template library.

## Install

**Grok Bot and Cursor** — install *Slideable* from the marketplace, or:

```bash
npx plugins add M-alk/slideable-plugin
```

That detects the agents you have installed — Grok Bot, Cursor, Claude Code,
Codex, VS Code, Copilot CLI and the rest — and adds Slideable to all of them.

The first time a Slideable tool runs, your agent opens a browser window to sign
in. Create a free account at [slideable.ai](https://slideable.ai/app) first if
you do not have one. The decks the agent builds are the ones you see when you
open the app.

## What is in the plugin

| | |
| --- | --- |
| `mcp.json` | The hosted MCP server, `https://www.slideable.ai/mcp`. Streamable HTTP, OAuth sign-in. |
| `skills/deck-research` | Turns a topic, notes or a document into an outline before any slide exists. |
| `skills/deck-build` | Builds the outline into a deck, then runs the overflow check and fixes what it finds. |
| `skills/deck-review` | Critiques an existing deck — the layout and the argument — and fixes it. |
| `skills/deck-translate` | Moves a deck between English and Arabic, mirroring the layout for right-to-left. |

## Try it

After installing, ask your agent:

- *Build me a 6-slide quarterly review for a Dubai cafe chain.*
- *Read the deck "Q1 Review" and tighten every headline to under six words.*
- *Make that deck Arabic and mirror the layout.*

Every write returns an audit; the agent fixes overflowing or low-contrast slides
before it tells you the deck is done. Open [slideable.ai](https://slideable.ai/app)
to see, present or export the result.

## How it works

The agent never sends geometry. It reads the layout catalogue (`list_layouts`),
picks a layout id and supplies strings for that layout's named slots. Position,
size, colour, type scale and spacing stay owned by the templates, so a generated
slide is identical to one built by hand.

## Adding the server without the plugin

Any MCP client that speaks Streamable HTTP can use the URL directly.

| Client | |
| --- | --- |
| Claude Code | `claude mcp add --transport http slideable https://www.slideable.ai/mcp` |
| VS Code | `code --add-mcp '{"name":"slideable","type":"http","url":"https://www.slideable.ai/mcp"}'` |

Grok Bot, Cursor, Claude Desktop, Windsurf and others read a config file:

```json
{
  "mcpServers": {
    "slideable": {
      "url": "https://www.slideable.ai/mcp"
    }
  }
}
```

## Privacy and terms

[Privacy policy](https://slideable.ai/privacy) ·
[Terms of service](https://slideable.ai/terms)

Once connected, the agent can see the decks in your library and create or edit
decks. It never sees your password: sign-in happens on slideable.ai.

## Licence

The files in this repository are published so plugin installers can read them.
Slideable itself is proprietary; nothing here grants a licence to the product.
