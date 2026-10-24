# Amazon Keyword Research: Search Volume & Reverse ASIN (`plainrows/amazon-keyword-research`)

Amazon keyword research tool, Helium 10 alternative and MCP tool: Amazon search volume for up to 10,000 keywords, related Amazon keywords, and reverse ASIN (keywords a product ranks for, with its rank). Volume: 16 markets. Pay $0.0006 per keyword with data + a $0.03 fee per batch, seed or ASIN.

Store page and full documentation: https://apify.com/plainrows/amazon-keyword-research

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `mode` | string: `searchVolume`, `relatedKeywords`, `reverseAsin` | "searchVolume" | Search volume: one row per keyword you list, with its monthly Amazon searches. Related keywords: Amazon keywords related to each seed keyword. Reverse ASIN: the Amazon searches a product (ASIN) ranks for, with its rank. |
| `keywords` | array |  | Search volume mode: keywords to look up, one per line (up to 10,000 per run, 80 characters and 10 words each; lowercased, duplicates removed). Sent in batches of 250: each batch costs one fee, so group your keywords in... |
| `asins` | array |  | Reverse ASIN mode only: Amazon product IDs such as B00R92CL5E, or product URLs containing /dp/ASIN (only the ID is read from the text; no Amazon page is opened). Up to 500 per run, one fee each. |
| `market` | string (16 codes, see the Store page) | "US" | Amazon marketplace the data is for. Search volume: all 16 markets. Related keywords and reverse ASIN: United States, United Arab Emirates, Saudi Arabia and Egypt only (other markets are refused before anything is... |
| `maxResultsPerQuery` | integer | 100 | Related keywords and reverse ASIN modes: most keywords returned per seed keyword or ASIN (1 to 1,000). Each keyword returned is one billed result. |
| `depth` | integer | 3 | Related keywords mode: how far to follow 'related searches' from the seed. About 6 keywords at depth 1, 42 at 2, 258 at 3, 1,554 at 4 (most); the max keywords per seed still applies. |
| `sortBy` | string: `searchVolume`, `rank` | "searchVolume" | Reverse ASIN mode: which keywords come first when the product ranks for more than the max keywords per ASIN. |
| `ignoreSynonyms` | boolean | false | Related keywords and reverse ASIN modes: return core keywords only, without highly similar variants. |

## Example input

```json
{
  "keywords": [
    "phone case",
    "iphone charger",
    "wireless earbuds"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword**: $0.0006 / $0.0006 / $0.0006 / $0.0006. One Amazon keyword returned with data: search volume (all modes), related keyword depth, or the product's rank for it (reverse ASIN). Keywords without volume, seeds or ASINs with nothing found, duplicates and invalid values are never charged.
- **Amazon lookup**: $0.03 / $0.03 / $0.03 / $0.03. One request answered by the Amazon data source: one per seed keyword, per ASIN, or per batch of up to 250 keywords for search volume (1-250 keywords = 1, 251-500 = 2). Not charged when the source refuses the request or is down.
