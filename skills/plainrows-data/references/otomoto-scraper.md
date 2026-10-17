# Otomoto Scraper: Polish Car Listings & Prices (`plainrows/otomoto-scraper`)

Type a make and model or paste otomoto.pl search URLs, get every car listing: price, price evaluation, year, mileage, fuel, gearbox, power, city, region, dealer or private. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/otomoto-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One per line: a make ("toyota"), a make and model ("toyota corolla", "bmw/seria-3") or an otomoto.pl search URL copied from the address bar after setting filters (price, year, mileage, region, fuel…) and sort order. Up... |
| `maxResultsPerSearch` | integer | 96 | Otomoto shows 32 listings per page; the Actor reads up to 20 pages (640 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "toyota corolla",
    "https://www.otomoto.pl/osobowe/volkswagen/golf?search%5Bfilter_float_year%3Afrom%5D=2018"
  ],
  "maxResultsPerSearch": 32
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.0004. One Otomoto car listing returned with its details (title, price, price evaluation, year, mileage, fuel, gearbox, engine, power, location, dealer or private). Searches without listings, unknown makes, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
