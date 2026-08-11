# Slideable — agent plugin

Connects [Slideable](https://slideable.ai) to your coding agent, so it can build
and edit decks out of your own template library.

```bash
npx plugins add M-alk/slideable-plugin
```

That detects the agents you have installed — Claude Code, Codex, Cursor, VS
Code, Copilot CLI and the rest — and adds Slideable to all of them.

## What this repository is

Two manifest files. That is the whole thing.

The `plugins` CLI installs from a public git repository, so the manifests it
reads have to live in one. They point at [`slideable-mcp`](https://www.npmjs.com/package/slideable-mcp)
on npm, which is where the server itself is published. Slideable's source is not
here and is not public.

## Installing without the plugin

Every client can also be pointed straight at the npm package.

| Client | |
| --- | --- |
| Claude Code | `claude mcp add slideable -- npx -y slideable-mcp` |
| Codex CLI | `codex mcp add slideable -- npx -y slideable-mcp` |
| VS Code | `code --add-mcp '{"name":"slideable","command":"npx","args":["-y","slideable-mcp"]}'` |
| Copilot CLI | `copilot mcp add` — interactive; the command is `npx -y slideable-mcp` |

Cursor, Gemini CLI, Claude Desktop, Zed and Windsurf all read a config file:

```json
{
  "mcpServers": {
    "slideable": {
      "command": "npx",
      "args": ["-y", "slideable-mcp"]
    }
  }
}
```

ChatGPT on the web is not supported yet. It reaches MCP only over hosted HTTP
and cannot start a local process. Codex CLI is a separate product and works
today.

## What the agent can do

Once connected it can read the layout catalogue, build a deck from an outline,
rewrite slides without touching their design, switch a deck to Arabic with a
mirrored layout, and audit every slide for text that overflows its box.

It never sends geometry. It picks a layout id and supplies strings for that
layout's named slots — position, size, colour, type scale and spacing stay owned
by the templates, so a generated slide is identical to one built by hand.

## Licence

The manifests in this repository are published so the plugin installer can read
them. Slideable itself is proprietary; nothing here grants a licence to the
product or to the `slideable-mcp` package.
