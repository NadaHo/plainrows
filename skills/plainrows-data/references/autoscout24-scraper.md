# AutoScout24 Scraper: Car Listings, Prices & Mileage (`plainrows/autoscout24-scraper`)

AutoScout24 scraper and MCP tool (unofficial AutoScout24 API): paste search URLs or a make and model, get every car listing: price, price rating, mileage, first registration, fuel, gearbox, power, city, dealer. 8 countries. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/autoscout24-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a make or a make and model ("bmw x5", "volkswagen golf", "land-rover/range-rover") or a search URL copied from AutoScout24 (autoscout24.de, .at, .it, .fr, .nl, .be, .es, .lu) with your filters and... |
| `country` | string: `de`, `at`, `it`, `fr`, `nl`, `be`, `es`, `lu` | "de" | Used for make/model searches only; a pasted URL keeps its own country site. |
| `maxResultsPerSearch` | integer | 100 | AutoScout24 shows 20 listings per page; the Actor reads up to 20 pages (400 listings) per search, one after the other. For more, split the search with filters (price, year, region). |

## Example input

```json
{
  "searches": [
    "bmw x5",
    "https://www.autoscout24.de/lst/volkswagen/golf?sort=price&desc=0"
  ],
  "maxResultsPerSearch": 40
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.0004. One AutoScout24 car listing returned with its details (title, price, price rating, mileage, first registration, fuel, gearbox, power, location, dealer or private). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
