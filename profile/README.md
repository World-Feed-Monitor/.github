## World Feed Monitor

News from publishers in every country and language, through one REST API or an MCP server.

World Feed Monitor reads news sources worldwide, categorises and deduplicates their articles, and serves them as structured JSON. Every article comes with its publisher, country, language, topics, publication time and a link to the original. You query the news; you don't build or maintain the crawling.

- **REST API.** Search by keywords, country, language, topic, publisher and date, with 25 results per page. Metadata endpoints list the countries, languages, topics and publishers you can filter by.
- **MCP server.** Let an AI agent search the news directly with four tools: `search_news`, `get_latest_news`, `get_sources` and `get_coverage`. It works with clients that can send a request header, such as Claude Code, Cursor and VS Code.
- **Worldwide on every plan.** Every plan reaches every country we cover, the Free plan included. Plans differ in volume, not coverage.

### Get started

1. Create a free account at [worldfeedmonitor.com/register](https://worldfeedmonitor.com/register). No card is needed. Confirm your email address.
2. In the dashboard, create API credentials: a key and a secret.
3. Make a request. Authentication is HTTP Basic, with the key as username and the secret as password:

```bash
curl -u "YOUR_API_KEY:YOUR_API_SECRET" \
  "https://api.worldfeedmonitor.com/v1/feeds/search?keywords=energy&country=DE"
```

Or connect an AI agent over MCP, with the same credentials:

```bash
claude mcp add --transport http worldfeedmonitor https://api.worldfeedmonitor.com/mcp \
  --header "Authorization: Basic $(printf 'YOUR_API_KEY:YOUR_API_SECRET' | base64 | tr -d '\n')"
```

To try a search before signing up, use the [API Playground](https://worldfeedmonitor.com/playground). It needs no key.

The Free plan includes the REST API and the MCP server, with 30 requests a minute, 1,000 a day and 10,000 a month, and the first 100 results of each search.

### Documentation

- [API reference](https://worldfeedmonitor.com/docs)
- [OpenAPI document](https://worldfeedmonitor.com/openapi.json)
- [API Playground](https://worldfeedmonitor.com/playground)
- [MCP server](https://worldfeedmonitor.com/#mcp)
- [Plans and pricing](https://worldfeedmonitor.com/#pricing)

### Examples

- [worldfeedmonitor-python-example](https://github.com/World-Feed-Monitor/worldfeedmonitor-python-example): a small Python client for the REST API, with search, latest-news and CSV/JSON export scripts.
- [worldfeedmonitor-nextjs-example](https://github.com/World-Feed-Monitor/worldfeedmonitor-nextjs-example): a global news dashboard in Next.js and TypeScript, calling the API from the server.
- [worldfeedmonitor-mcp-agent-example](https://github.com/World-Feed-Monitor/worldfeedmonitor-mcp-agent-example): a Python research agent that searches the news through the MCP server and cites its sources.
