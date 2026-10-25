# Google Search API: Google SERP Scraper & Web Results (`plainrows/google-search-api`)

Google Search API and MCP tool, Google Custom Search API alternative: Google organic results as JSON (position, URL, domain, title, snippet, SERP features) for any query, country, language, device. $0.0024 per query with results plus $0.0003 per result, $0.0026 per extra page of 10, $0.001 per run.

Store page and full documentation: https://apify.com/plainrows/google-search-api

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | One Google search per line, exactly as you would type it. Up to 1,000 queries per run, max 700 characters each. Advanced operators (site:, intitle:, filetype:...) are not supported. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google results you want. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `device` | string: `desktop`, `mobile` | "desktop" | Google results as seen on a desktop computer or on a mobile phone. |
| `maxResults` | integer | 10 | How many organic results to return per query: 10 = first Google page (the normal case; Google often shows 7 to 9 organic results on it, the rest being ads, maps or other blocks). Each further page of 10 is billed as an... |

## Example input

```json
{
  "queries": [
    "crm software",
    "best project management tool"
  ],
  "country": "US",
  "device": "desktop",
  "maxResults": 10
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Organic result**: $0.0003 / $0.0003 / $0.0003 / $0.0003. One Google organic result returned: position, URL, domain, title and snippet. Queries with no result, failures and unreadable answers are free.
- **Search query with results**: $0.0024 / $0.0024 / $0.0024 / $0.0024. Charged once per query that returns at least one organic result (the data source charges a whole Google results page, even for one result). Queries with no result are free.
- **Extra results page**: $0.0026 / $0.0026 / $0.0026 / $0.0026. Only when you raise "Max organic results per query" above 10: one per extra page of 10 results that Google returned. Not charged at the default of 10.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
