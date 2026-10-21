# Autovit Scraper: Romania Car Listings & Prices (`plainrows/autovit-scraper`)

Type a make and model or paste autovit.ro search URLs, get every car listing: price, price evaluation, year, mileage, fuel, engine, power, city, county, dealer or private. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/autovit-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One per line: a make ("dacia"), a make and model ("dacia duster", "dacia/logan") or an autovit.ro search URL copied from the address bar after setting filters (price, year, mileage, county, fuel…) and sort order. Up to... |
| `maxResultsPerSearch` | integer | 96 | Autovit shows 32 listings per page; the Actor reads up to 20 pages (640 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "dacia duster",
    "https://www.autovit.ro/autoturisme/volkswagen/golf?search%5Bfilter_float_year%3Afrom%5D=2018"
  ],
  "maxResultsPerSearch": 32
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.0004. One Autovit car listing returned with its details (title, price, price evaluation, year, mileage, fuel, engine, power, location, dealer or private). Searches without listings, unknown makes, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
