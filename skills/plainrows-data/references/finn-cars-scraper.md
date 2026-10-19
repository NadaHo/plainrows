# FINN.no Car Scraper: Norway Used Car Listings (`plainrows/finn-cars-scraper`)

Type a keyword or paste finn.no car search URLs, get every car: make, model, year, mileage, fuel, gearbox, price, city, private or dealer, dealer name, photos. No login. Pay per car plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/finn-cars-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One per line: a keyword ("tesla model y", "volvo xc60") or a finn.no car search URL (https://www.finn.no/mobility/search/car?...), copied from the address bar after setting filters (make and model, year, mileage, price,... |
| `maxResultsPerSearch` | integer | 100 | FINN shows about 50 cars per page; the Actor reads up to 20 pages (1,000 cars) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "tesla model y",
    "https://www.finn.no/mobility/search/car?variant=0.818"
  ],
  "maxResultsPerSearch": 50
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Car listing**: $0.0008 / $0.0007 / $0.0006 / $0.0006. One FINN car listing returned with its details (make, model, year, mileage, fuel, gearbox, price, city, private or dealer, photos, date). Searches without listings, blocked or unreadable pages, other sections of the site, cards without year, make or price, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
