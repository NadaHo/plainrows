# Standvirtual Scraper: Portugal Car Listings & Prices (`plainrows/standvirtual-scraper`)

Type a make and model or paste standvirtual.com search URLs, get every car listing: price, price evaluation, year, mileage, fuel, gearbox, power, city, district, dealer or private. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/standvirtual-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One per line: a make ("bmw"), a make and model ("bmw 320", "bmw/320") or a standvirtual.com search URL copied from the address bar after setting filters (price, year, mileage, district, fuel…) and sort order. Up to 100... |
| `maxResultsPerSearch` | integer | 96 | Standvirtual shows 32 listings per page; the Actor reads up to 20 pages (640 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "bmw 320",
    "https://www.standvirtual.com/carros/renault?search%5Bfilter_float_first_registration_year%3Afrom%5D=2018"
  ],
  "maxResultsPerSearch": 32
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.0004. One Standvirtual car listing returned with its details (title, price, price evaluation, year, mileage, fuel, gearbox, engine, power, location, dealer or private). Searches without listings, unknown makes, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
