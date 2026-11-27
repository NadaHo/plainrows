# ASO Keyword Rankings: App Store & Google Play Search (`plainrows/aso-keyword-rankings`)

ASO keyword rank tracker, API and MCP tool: for each keyword, the apps ranked in App Store and Google Play search (rank, app ID, name, developer, rating, ratings count, price, link), 20 countries. Pay per ranked app, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/aso-keyword-rankings

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | One per line: the words people type in the store search, e.g. habit tracker or budget app. Up to 500 keywords per run. |
| `store` | string: `both`, `app_store`, `google_play` | "both" | Which store to search, e.g. both. |
| `country` | string (20 codes, see the Store page) | "US" | Store country, e.g. US. The ranking differs from one country to another. |
| `languageCode` | string |  | Two-letter search language, e.g. en. Empty = the main language of the country. |
| `maxResults` | integer | 30 | How many top-ranked apps to return per keyword and store, e.g. 30. The App Store goes up to 100, Google Play shows about 30. |

## Example input

```json
{
  "keywords": [
    "habit tracker"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Ranked app**: $0.0008 / $0.0008 / $0.0008 / $0.0008. One app ranked for a keyword in App Store or Google Play search, with its rank, ID, name, rating, ratings count, price and link. Keywords without results, store failures and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
