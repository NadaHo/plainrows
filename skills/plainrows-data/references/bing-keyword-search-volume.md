# Bing Keyword Search Volume: Bulk Bing Ads Volume & CPC (`plainrows/bing-keyword-search-volume`)

Bing keyword search volume API and MCP tool: Bing Ads search volume, CPC, competition, 12-month history for up to 10,000 keywords per run (batches of 1,000). US, UK, Canada, Australia, Germany, France. Pay $0.0001 per keyword with data, plus $0.15 per batch and a small start fee.

Store page and full documentation: https://apify.com/plainrows/bing-keyword-search-volume

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | Keywords to look up on Bing, one per line (up to 100 characters each; they are lowercased, duplicates removed). Up to 10,000 keywords per run, sent to the source in batches of 1,000: each batch costs one batch fee, so... |
| `country` | string: `US`, `GB`, `CA`, `AU`, `DE`, `FR` | "US" | Bing Ads market the volumes are for. |
| `languageCode` | string: `en`, `fr`, `de` |  | Language of the searches. Bing keyword data exists in English, French and German only. Empty = the country's usual language (English, or German for DE/AT/CH, French for FR/BE). |
| `device` | string: `all`, `desktop`, `mobile`, `tablet` | "all" | Volumes for all devices or one device type. |
| `includeSearchPartners` | boolean | false | Off: Bing, AOL and Yahoo searches. On: also Microsoft's syndicated search partner sites. |
| `speed` | string: `standard`, `live` | "live" | Live (default) gets the data in seconds. Standard sends the same request through the data provider's queue: same data and same price for you, but each batch of up to 1,000 keywords usually takes a few minutes (a batch... |

## Example input

```json
{
  "keywords": [
    "coffee maker",
    "espresso machine",
    "french press"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword**: $0.0001 / $0.0001 / $0.0001 / $0.0001. One keyword returned with Bing data: monthly search volume, CPC, competition and 12-month history. Keywords without data, duplicates and invalid keywords are never charged.
- **Keyword batch**: $0.15 / $0.15 / $0.15 / $0.15. One batch of up to 1,000 keywords sent to Bing data source, charged once the source has answered (a source error is free). 1-1,000 keywords = 1 batch, 1,001-2,000 = 2.
- **Actor Start**: $0.02 / $0.02 / $0.02 / $0.02. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
