# Kleinanzeigen Scraper: Listings, Prices & Locations (`plainrows/kleinanzeigen-scraper`)

Germany classifieds scraper and MCP tool: paste kleinanzeigen.de search URLs or keywords, get every listing: title, price, VB, postcode, city, date, image, shipping, private or business seller. No login, no browser. Pay per listing, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/kleinanzeigen-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a keyword searched in all of Germany ("fahrrad", "iphone 15") or a search URL copied from kleinanzeigen.de with your filters (category, city, radius, price, private/business). Up to 200 searches per... |
| `maxResultsPerSearch` | integer | 100 | Kleinanzeigen shows 25 listings per page and at most 50 pages (1,250 listings) per search. Pages are read one after the other. |

## Example input

```json
{
  "searches": [
    "https://www.kleinanzeigen.de/s-berlin/fahrrad/k0l3331",
    "iphone 15"
  ],
  "maxResultsPerSearch": 50
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.001 / $0.0009 / $0.0008 / $0.0007. One Kleinanzeigen listing returned with its details (title, price, VB, postcode, city, date, image, shipping, private or business seller). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
