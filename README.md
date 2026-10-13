# NutsGrowth MCP server

[![NutsGrowth MCP connector](https://glama.ai/mcp/connectors/com.nutsgrowth/directory/badges/score.svg)](https://glama.ai/mcp/connectors/com.nutsgrowth/directory)

Search [NutsGrowth](https://nutsgrowth.com), a curated directory of startups and SaaS tools, from your AI assistant. Find alternatives to a product, compare listings, and read prices together with the date a person last checked them.

This repository holds no code. The server is hosted at:

```
https://nutsgrowth.com/mcp
```

It speaks Streamable HTTP. No account and no API key are needed. It is listed in the official MCP Registry as `com.nutsgrowth/directory`.

## Connect

**Claude:** Settings → Connectors → Add custom connector, and paste the address.

**Claude Code:**

```bash
claude mcp add --transport http nutsgrowth https://nutsgrowth.com/mcp
```

**Cursor:** add this to `.cursor/mcp.json`. It is also in this repository as `.mcp.json`.

```json
{ "mcpServers": { "nutsgrowth": { "url": "https://nutsgrowth.com/mcp" } } }
```

**VS Code:** add this to `.vscode/mcp.json`.

```json
{ "servers": { "nutsgrowth": { "type": "http", "url": "https://nutsgrowth.com/mcp" } } }
```

**Other clients:** any client that takes a remote server over Streamable HTTP takes the same address.

## Tools

| Tool | What it does |
|---|---|
| `search_tools` | Finds listings by words and filters: category, country, tags, open source, self-hostable, free plan, price checked. |
| `find_alternatives` | Lists what the directory files as a replacement for a named product, such as "Notion". |
| `get_tool` | Returns everything public about one listing: its price as checked, the terms of that price, when it was last checked, its reviews and its positioning. |
| `compare_tools` | Puts two to four listings side by side. |
| `list_filters` | Lists the categories, countries and tags in use, with counts. |
| `submit_tool` | Suggests a product for the directory. A person reviews every suggestion. |

The live list, with each tool's full description, is at https://nutsgrowth.com/mcp.

## How it answers

- **At most 10 listings per call.** Each answer gives the total and a link to the page that holds the rest.
- **Every listing carries two links:** its NutsGrowth page and the product's own website.
- **No adverts and no affiliate links.** Nobody can pay to rank higher.
- **Unchecked prices are labelled.** A price nobody has checked is shown as "Not checked", never guessed.
- **Company text is labelled.** Text a company wrote about itself comes back as plain text, marked `written_by: "vendor"`.

## Limits and privacy

- **Requests:** at most 120 a minute from one address.
- **Suggestions:** assistants can send at most 30 a day across the whole site.
- **What is kept:** what assistants search for — the words, the filters, how many listings matched, and the day. It is kept for 90 days, to see what the directory is missing.
- **What is not kept:** the address a request came from, and anything about who asked.

See the [privacy policy](https://nutsgrowth.com/privacy).

## License

The contents of this repository are MIT-licensed. The directory's data is served by nutsgrowth.com under its [terms](https://nutsgrowth.com/terms).
