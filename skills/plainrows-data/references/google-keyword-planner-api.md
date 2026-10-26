# Google Keyword Planner API: Google Ads Search Volume & CPC (`plainrows/google-keyword-planner-api`)

Google Keyword Planner API and MCP tool: real Google Ads search volume, CPC, competition, top-of-page bids and 12-month trend for up to 10,000 keywords, long tail included. A keyword planner alternative without an Ads account. Fee per 1,000-keyword lookup + per keyword found.

Store page and full documentation: https://apify.com/plainrows/google-keyword-planner-api

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | One keyword per line, up to 10,000 per run, at most 80 characters and 10 words each, without symbols such as ! @ % ( ) ? or emojis (Google Ads rules; others get a free INVALID_KEYWORD row). Duplicates (case and spaces... |
| `country` | string (94 codes, see the Store page) | "US" | Country whose Google Ads search data you want (94 countries). |
| `languageCode` | string |  | Language code, e.g. "en", "fr" or "zh-TW". Leave empty to use the country's main language (for example German for Switzerland, Turkish for Turkey). A language Google Ads does not offer stops the run with a clear message... |

## Example input

```json
{
  "keywords": [
    "coffee maker",
    "espresso machine",
    "french press"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword with search volume**: $0.003 / $0.003 / $0.003 / $0.003. One keyword with a Google Ads search volume: monthly volume, CPC, competition, top-of-page bids and 12-month trend. Keywords without data are free rows.
- **Lookup batch (up to 1,000 keywords)**: $0.15 / $0.15 / $0.15 / $0.15. Once per batch of up to 1,000 keywords looked up in Google Ads, even when no keyword in it has a volume (the data source bills every lookup, $0.09). Failures, refused batches and keywords not reached are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
