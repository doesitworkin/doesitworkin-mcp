# Does It Work In MCP server and agent skill

[Does It Work In](https://doesitworkin.com) verifies whether essential digital services—travel eSIMs, VPN protocols, foreign Visa/Mastercard linking on Alipay and WeChat Pay, Apple Wallet IC transit cards (Suica, PASMO, ICOCA), navigation apps (Google Maps, Naver Map, KakaoMap, Amap) and AI tools—actually work in China, Japan, Hong Kong, South Korea, Thailand, Vietnam, Taiwan, Europe and other destinations. Every guide separates official marketing claims from verified on-the-ground reality and lists pre-departure steps. This repository holds the connection details for its remote MCP server and an [Agent Skill](skills/doesitworkin/SKILL.md). The service is hosted; there is nothing to install or run.

- **MCP endpoint:** `https://doesitworkin.com/mcp` (Streamable HTTP)
- **Auth:** none. Free, no API key, no account. Rate limit: 60 requests per minute per IP.
- **Registry name:** `com.doesitworkin/doesitworkin` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.doesitworkin/doesitworkin)
- **Docs:** [doesitworkin.com/about](https://doesitworkin.com/about) · [llms.txt](https://doesitworkin.com/llms.txt)

## Connect

**Claude Code**

```bash
claude mcp add --transport http doesitworkin https://doesitworkin.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "doesitworkin": { "url": "https://doesitworkin.com/mcp" }
  }
}
```

**Codex** (`~/.codex/config.toml`)

```toml
[mcp_servers.doesitworkin]
url = "https://doesitworkin.com/mcp"
```

In Claude Desktop or ChatGPT, add `https://doesitworkin.com/mcp` as a custom connector.

## Tools

| Tool | What it does |
| --- | --- |
| `search_guides` | Search destination guides and provider comparisons by query (`q`), `country` slug (e.g. `china`, `japan`, `hong-kong`), or `topic` (`esim`, `vpn`, `payments`, `maps`, `ai`, `transit`) |
| `get_guide` | Full guide for a path (e.g. `/china/esim`, `/china/alipay`, `/compare/airalo-vs-holafly-vs-saily`): official claim vs. verified reality, `beforeYouFly` checklist, limits/gotchas, providers and FAQs |
| `get_country` | Destination compatibility matrix (`works`, `conditional`, `workaround_required`, `blocked`), guides and recommended providers for a country `slug` |
| `list_providers` | Tested travel eSIM, VPN, payment and booking providers with starting prices, routing notes and promo codes |
| `list_referrals` | Active travel eSIM and booking referral links and codes with plain-English disclosures of what you get and what Does It Work In earns |
| `report_outdated_info` | Submit a field report if a carrier rule, app status, payment threshold or provider price has changed |

## HTTP & Markdown endpoints

Every guide and country hub can also be read directly without MCP:

- `https://doesitworkin.com/api/v1/guides`, `/api/v1/countries`, `/api/v1/providers`, `/api/v1/referrals`
- Append `.md` or `.json` to any page (for example `https://doesitworkin.com/china/alipay.md`)

## Agent skill

[`skills/doesitworkin/SKILL.md`](skills/doesitworkin/SKILL.md) follows the [Agent Skills](https://agentskills.io) format. Install it with

```bash
npx skills add doesitworkin/doesitworkin-mcp
```

or copy the folder into your agent's skills directory (for Claude Code, `~/.claude/skills/doesitworkin/`).


### One-line prompt for any AI agent

Paste into Claude Code, Cursor, Codex, or Gemini CLI:

```text
Read https://raw.githubusercontent.com/doesitworkin/doesitworkin-mcp/main/skills/doesitworkin/SKILL.md and check whether an AI or streaming service works in a given country.
```

## Support

support@doesitworkin.com

## License

The files in this repository are MIT licensed. Guide content on doesitworkin.com is covered by the site's terms at [doesitworkin.com/about](https://doesitworkin.com/about).
