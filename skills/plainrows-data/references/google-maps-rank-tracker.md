# Google Maps Rank Tracker: Geo-Grid Local SEO (`plainrows/google-maps-rank-tracker`)

See where a business ranks on Google Maps at every point of a grid around it (3x3 to 9x9) for up to 5 keywords: rank per point, top 3 competitors, average rank and share of local voice. A Local Falcon and BrightLocal alternative: pay per grid point plus a small start fee, no subscription.

Store page and full documentation: https://apify.com/plainrows/google-maps-rank-tracker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `business` (required) | string |  | The business to track: its name and city ("Monmouth Coffee, Borough, London"), its Google Maps link, place ID ("ChIJ...") or CID. One business per run. If it cannot be found, the run stops and no grid point is charged. |
| `keywords` (required) | array |  | What customers type in Google Maps, 1 to 5 keywords: "coffee shop", "espresso bar". Do not add the city: each search is made from the grid point itself. |
| `gridSize` | string: `3`, `5`, `7`, `9` | "5" | Points per side: 3 (9 points), 5 (25), 7 (49) or 9 (81). Each point is one Google Maps search per keyword. |
| `gridSpacingKm` | string | "1" | Distance between two neighbouring points, from 0.1 to 20 km. 0.5-1 km for a city centre, 2-5 km for a suburb or a service area. |
| `country` | string (20 codes, see the Store page) | "US" | Country of the business (sets the default language and the search used to find the business). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxRank` | integer | 20 | How many Google Maps results to check at each point. A business beyond this rank is reported as not ranked (rank null). The price per grid point does not depend on this value. |
| `centerLat` | string |  | Centre the grid somewhere else than the business, e.g. "51.5074". Set both latitude and longitude. |
| `centerLng` | string |  | e.g. "-0.1278". |
| `zoom` | integer | 15 | Zoom of the Google Maps view at each point (15 = a few streets around the searcher, as on a phone). Keep the same value between runs to compare them. |

## Example input

```json
{
  "business": "Monmouth Coffee Company, Borough, London",
  "keywords": [
    "coffee shop"
  ],
  "gridSize": "5",
  "country": "GB"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Grid point checked**: $0.01 / $0.008 / $0.007 / $0.006. One grid point searched on Google Maps for one keyword: the business's rank there (or not ranked) and the top 3 places. Charged only when Google Maps returned places. The business lookup, the summary per keyword, a business not found, points with no place and unreadable answers are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
