# Steam Scraper: Games, Prices & Reviews (`plainrows/steam-scraper`)

Steam scraper and MCP tool: game details, prices, discounts, release dates, developers, genres and review scores for any list of Steam games, or their user reviews (recommended, hours played, votes, text). App IDs, store URLs or names. Pay per row + start fee.

Store page and full documentation: https://apify.com/plainrows/steam-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `games` (required) | array |  | Steam app IDs ("1145360"), store or community URLs ("https://store.steampowered.com/app/1145360/Hades/") or game names ("Hades": the exact title match wins, else the first store result). Up to 2,000 per run; duplicates... |
| `mode` | string: `games`, `reviews` | "games" | "games": price, discount, release date, developers, publishers, genres, review score. "reviews": the game's user reviews (recommended or not, hours played, date, helpful votes, text). |
| `maxReviewsPerGame` | integer | 50 | Reviews mode only. Each review returned is billed; see Pricing. |
| `reviewSort` | string: `mostrecent`, `toprated` | "mostrecent" | Reviews mode only. |
| `reviewLanguage` | string (31 codes, see the Store page) | "all" | Reviews mode only. Steam language name; "all" = every language. |
| `country` | string | "US" | Steam store country: currency and prices of the game rows (and availability). |

## Example input

```json
{
  "games": [
    "1145360",
    "https://store.steampowered.com/app/292030/The_Witcher_3_Wild_Hunt/",
    "Stardew Valley"
  ],
  "mode": "games",
  "maxReviewsPerGame": 20,
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Row**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One Steam game with its data (games mode) or one user review (reviews mode). Games not found, blocked or without reviews are free rows.
- **Actor Start**: $0.0005 / $0.0005 / $0.0005 / $0.0005. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
