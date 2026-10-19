# coches.net Scraper: Spain Car Listings, Prices & Mileage (`plainrows/coches-net-scraper`)

Paste coches.net search URLs or a make and model, get every used car listing in Spain: price, market average price, year, mileage, fuel, power, province, dealer. No login, no browser. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/coches-net-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a make or a make and model ("seat leon", "volkswagen golf", "mercedes-benz/clase c") or a search URL copied from coches.net (e.g. https://www.coches.net/segunda-mano/toyota/c-hr/). Up to 100... |
| `maxResultsPerSearch` | integer | 100 | coches.net shows about 35 listings per page; the Actor reads up to 6 pages (robots.txt allows no more), so up to 200 listings per search. For more, split by model or region (e.g. /segunda-mano/seat/leon/madrid/). |

## Example input

```json
{
  "searches": [
    "seat leon",
    "https://www.coches.net/segunda-mano/volkswagen/golf/"
  ],
  "maxResultsPerSearch": 40
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.0004. One coches.net car listing returned with its details (title, price, market average price, year, mileage, fuel, power, province and city, dealer or private). Searches without listings, blocked or unreadable pages, listings without price, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
