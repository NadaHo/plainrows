# Google Keyword Planner Alternative: Bulk Search Volume & CPC (`plainrows/keyword-planner-alternative`)

Google Keyword Planner alternative, Keyword Planner API, keyword CPC checker and MCP tool: Google Ads keyword planner, no Ads account. Bulk keyword search volume, ≤ 10,000 keywords, per row: CPC, bid range, competition, difficulty, intent, history. $0.70-1 per 1,000 keywords with data + $0.02/run.

Store page and full documentation: https://apify.com/plainrows/keyword-planner-alternative

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | One keyword per line, up to 10,000 per run. Max 80 characters and 10 words each. Duplicates (case-insensitive) are removed for free before lookup. Free Apify plan: only the first 20 keywords of each run are looked up... |
| `mode` | string: `volume`, `ideas` | "volume" | "Search volume": metrics for each keyword you enter. "Keyword ideas": each keyword is a seed and the run returns related keyword ideas with the same metrics (plus seedKeyword), billed per idea with data like a keyword. |
| `country` | string (94 codes, see the Store page) | "US" | Country whose Google search data you want (94 countries). |
| `languageCode` | string |  | Language code, e.g. "en", "fr" or "zh-TW". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). Only languages offered by the data source for that country work; others... |
| `historyMonths` | integer | 12 | How many months of monthly search volumes to include per keyword, most recent first. 0 = none. Up to 96 months (data goes back to 2018 for most keywords). No extra cost. In ideas mode the data source returns 12 months... |
| `maxIdeasPerSeed` | integer | 50 | Ideas mode only: most related keyword ideas returned per seed keyword, most relevant first. An idea already returned for another seed is not returned or billed again. Free Apify plan: at most 20 per seed. Ignored in... |

## Example input

```json
{
  "keywords": [
    "coffee maker",
    "espresso machine",
    "french press",
    "cold brew coffee"
  ],
  "mode": "volume",
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword**: $0.001 / $0.0009 / $0.0008 / $0.0007. One keyword returned with data: search volume, CPC, competition, keyword difficulty, search intent, trends and monthly history. Keywords without data, duplicates and invalid keywords are never charged.
- **Actor Start**: $0.02 / $0.02 / $0.02 / $0.02. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
