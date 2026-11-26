# Baidu Search Scraper & API: Baidu SERP Results (`plainrows/baidu-search-scraper`)

Baidu search scraper and MCP tool: Baidu organic results as JSON (position, URL, domain, title, snippet) for any query, China, desktop or mobile. $0.003 per query with results + $0.0004 per result, $0.0026 per extra page of 50, $0.001 start fee per run. Empty queries free.

Store page and full documentation: https://apify.com/plainrows/baidu-search-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | One Baidu search per line, exactly as you would type it (Chinese or Latin script). Up to 1,000 queries per run, max 700 characters each. Advanced operators (site:, intitle:, filetype:...) are not supported. Results are... |
| `device` | string: `desktop`, `mobile` | "desktop" | Baidu results as seen on a desktop computer or on a mobile phone (m.baidu.com). |
| `maxResults` | integer | 10 | How many organic results to return per query: 10 is the normal case. Baidu pages hold about 50 results: above 50, the second page is billed as an extra results page (see Pricing). |

## Example input

```json
{
  "queries": [
    "笔记本电脑",
    "python 教程"
  ],
  "device": "desktop",
  "maxResults": 10
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Organic result**: $0.0004 / $0.0004 / $0.0004 / $0.0004. One Baidu organic result returned: position, URL, domain, title and snippet. Queries with no result, failures and unreadable answers are free.
- **Search query with results**: $0.003 / $0.003 / $0.003 / $0.003. Charged once per query that returns at least one organic result (the data source charges a whole Baidu results page, even for one result). Queries with no result are free.
- **Extra results page**: $0.0026 / $0.0026 / $0.0026 / $0.0026. Only when you raise "Max organic results per query" above 50: one per extra Baidu page (about 50 results) that Baidu returned. Not charged at the default of 10.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
