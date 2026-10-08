# Keyword Search Volume, CPC & Difficulty (`plainrows/keyword-search-volume`)

Get Google search volume, CPC, competition, keyword difficulty, search intent and up to 8 years of monthly history for up to 10,000 keywords per run in 20 countries. You only pay for keywords that have data.

Store page and full documentation: https://apify.com/plainrows/keyword-search-volume

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | One keyword per line, up to 10,000 per run. Max 80 characters and 10 words each. Duplicates (case-insensitive) are removed for free before lookup. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google search data you want. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). Only languages offered by the data source for that country work;... |
| `historyMonths` | integer | 12 | How many months of monthly search volumes to include per keyword, most recent first. 0 = none. Up to 96 months (data goes back to 2018 for most keywords). No extra cost. |

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

- **Keyword**: $0.01 / $0.008 / $0.007 / $0.006. One keyword returned with data: search volume, CPC, competition, keyword difficulty, search intent, trends and monthly history. Keywords without data, duplicates and invalid keywords are never charged. No fee per run.
