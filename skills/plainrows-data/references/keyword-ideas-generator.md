# Keyword Research Tool: Keyword Ideas, Volume & Difficulty (`plainrows/keyword-ideas-generator`)

Turn seed keywords into up to 1,000 keyword ideas each: long-tail suggestions, Google related searches or same-topic ideas, with search volume, CPC, keyword difficulty, intent and 12-month trend. 20 countries. Pay only per idea returned.

Store page and full documentation: https://apify.com/plainrows/keyword-ideas-generator

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `seedKeywords` (required) | array |  | One topic per line, e.g. "coffee maker" or "crm for small business". Each seed is expanded into its own list of ideas. Up to 100 seeds per run, max 80 characters and 10 words each. |
| `mode` | string: `suggestions`, `related`, `ideas` | "suggestions" | Suggestions = phrases that contain your seed ("best coffee maker with grinder"). Related = Google's "related searches", followed a few levels deep. Ideas = keywords from the same product or topic category, even without... |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google search volumes and CPC you want. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxIdeasPerSeed` | integer | 100 | 10 to 1,000. Each idea returned is billed; see Pricing. An idea already returned for an earlier seed is not repeated. |
| `depth` | integer | 2 | How many levels of Google related searches to follow: 1 = up to about 8 ideas, 2 = about 70, 3 = about 580, 4 = about 4,700. Deeper levels drift further from the seed. Used only with the Related source. |
| `sortBy` | string: `volume`, `difficulty`, `cpc`, `relevance` | "volume" | Also decides which ideas you get when a seed has more than your maximum. |
| `minSearchVolume` | integer |  | Keep ideas with at least this many monthly searches. Leave empty for no limit. |
| `maxSearchVolume` | integer |  | Keep ideas with at most this many monthly searches, e.g. to find long-tail keywords. |
| `maxKeywordDifficulty` | integer |  | 0 (easy) to 100 (hard). For example 30 to keep keywords that are easier to rank for. |
| `includeWords` | array |  | Keep only ideas containing at least one of these words or phrases, e.g. "best", "how to". Matching is on parts of words: "cheap" also keeps "cheapest". |
| `excludeWords` | array |  | Drop ideas containing any of these words, e.g. competitor brands. At most 8 filters in total (each word counts as one, and each volume or difficulty limit as one). |
| `includeSimilarKeywords` | boolean | false | Off (recommended): close variants of the same search, such as misspellings or reordered words, are left out so you are not billed for near-duplicates. |

## Example input

```json
{
  "seedKeywords": [
    "coffee maker"
  ],
  "mode": "suggestions",
  "country": "US",
  "maxIdeasPerSeed": 100
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword**: $0.004 / $0.003 / $0.0025 / $0.002. One keyword idea returned with its search volume, CPC, competition, difficulty, intent and 12-month history. Ideas removed by your filters, duplicates and seeds with no idea are not billed as ideas.
- **Seed keyword**: $0.01 / $0.01 / $0.01 / $0.01. Charged once per seed keyword sent to the data source, which bills a fixed fee for every search, even one that finds no idea. Not charged when the request is rejected or the data source is down.
