# Google Keyword Search Volume Checker & API: Ahrefs Alternative (`plainrows/keyword-search-volume`)

Bulk keyword search volume checker, search volume finder and search volume API, keyword research API and SEO MCP tool, Keyword Planner, Ahrefs or Semrush alternative: Google keyword volume, CPC, keyword difficulty, intent, history, 10,000 keywords/run, 94 countries. Pay per keyword, plus AI volume.

Store page and full documentation: https://apify.com/plainrows/keyword-search-volume

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | One keyword per line, up to 10,000 per run. Max 80 characters and 10 words each. Duplicates (case-insensitive) are removed for free before lookup. In ideas mode, each keyword is a seed (up to 100 per run). |
| `mode` | string: `volume`, `ideas` | "volume" | "Search volume": metrics for each keyword you enter. "Keyword ideas": each keyword is a seed and the run returns related keyword ideas with the same metrics (plus seedKeyword), billed per idea with data like a keyword. |
| `country` | string (94 codes, see the Store page) | "US" | Country whose Google search data you want (94 countries). |
| `languageCode` | string |  | Language code, e.g. "en", "fr" or "zh-TW". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). Only languages offered by the data source for that country work; others... |
| `historyMonths` | integer | 12 | How many months of monthly search volumes to include per keyword, most recent first. 0 = none. Up to 96 months (data goes back to 2018 for most keywords). No extra cost. In ideas mode the data source returns 12 months... |
| `includeAiSearchVolume` | boolean | false | Search volume mode only, from October 24, 2026: add aiSearchVolume (estimated monthly use of the keyword in AI tools and chat assistants) and its monthly history to each found keyword. Billed per keyword with a positive... |
| `maxIdeasPerSeed` | integer | 50 | Ideas mode only: most related keyword ideas returned per seed keyword, most relevant first. An idea already returned for another seed is not returned or billed again. Ignored in search volume mode. |

## Example input

```json
{
  "keywords": [
    "coffee maker",
    "espresso machine",
    "french press"
  ],
  "mode": "volume",
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword**: $0.01 / $0.008 / $0.007 / $0.006. One keyword returned with data: search volume, CPC, competition, keyword difficulty, search intent, trends and monthly history. Keywords without data, duplicates and invalid keywords are never charged. No fee per run.
- **AI search volume**: $0.005 / $0.004 / $0.0035 / $0.003. Optional, off by default: one keyword returned with its AI search volume (how often it comes up in AI assistants, with monthly history). Only charged when "Include AI search volume" is on and a volume is found.
