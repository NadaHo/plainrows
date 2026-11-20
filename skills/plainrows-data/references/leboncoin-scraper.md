# Leboncoin Scraper: Listings, Prices & Locations (`plainrows/leboncoin-scraper`)

France classifieds scraper and MCP tool: paste leboncoin.fr search URLs or keywords, get every listing: title, price, category, city, postcode, department, date, photos, pro or private seller, car and property details. No login. Pay per listing, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/leboncoin-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a keyword searched in all of France ("vélo électrique", "iphone 15") or a search URL copied from leboncoin.fr with your filters (category, city, radius, price, pro/private), e.g.... |
| `maxResultsPerSearch` | integer | 100 | leboncoin shows 35 listings per page and at most 100 pages (3,500 listings) per search, e.g. 100. Pages are read one after the other. |

## Example input

```json
{
  "searches": [
    "https://www.leboncoin.fr/recherche?text=velo"
  ],
  "maxResultsPerSearch": 35
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0012 / $0.0011 / $0.001 / $0.0009. One leboncoin listing returned with its details (title, price, category, city, postcode, department, date, photos, pro or private seller, category details). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.005 / $0.005 / $0.005 / $0.005. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
