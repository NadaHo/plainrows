# Marktplaats Scraper: Dutch Listings & Prices (`plainrows/marktplaats-scraper`)

Paste marktplaats.nl search URLs or keywords, get every listing: title, price, price type, city, date, image, condition, delivery, business seller name. No login, no browser. Pay per listing.

Store page and full documentation: https://apify.com/plainrows/marktplaats-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a keyword ("racefiets", "iphone 15") or a search URL copied from marktplaats.nl (/q/… or a category /l/…). Filters after # in the address bar are applied by your browser, not by the site: use a... |
| `maxResultsPerSearch` | integer | 100 | Marktplaats shows 30 listings per page; the Actor reads up to 20 pages (600 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "racefiets",
    "https://www.marktplaats.nl/l/auto-s/volkswagen/q/golf/"
  ],
  "maxResultsPerSearch": 30
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One marktplaats.nl listing returned with its details (title, price, price type, city, date, image, condition, delivery, business seller or not). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
