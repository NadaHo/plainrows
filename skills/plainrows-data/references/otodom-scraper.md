# Otodom Scraper: Poland Property Listings & Prices (`plainrows/otodom-scraper`)

Poland real estate scraper and MCP tool: paste otodom.pl search URLs, get every property listing: price, price per m², rent, area, rooms, floor, city, district, agency or private owner, date. Flats, houses, plots, sale or rent. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/otodom-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One otodom.pl search URL per line, copied from the address bar after choosing the property type, sale or rent, location and filters (price, area, rooms, owner type…). Up to 100 searches per run; duplicates are removed. |
| `maxResultsPerSearch` | integer | 108 | Otodom shows 36 listings per page; the Actor reads up to 20 pages (720 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "https://www.otodom.pl/pl/wyniki/sprzedaz/mieszkanie/mazowieckie/warszawa",
    "https://www.otodom.pl/pl/wyniki/wynajem/mieszkanie/malopolskie/krakow"
  ],
  "maxResultsPerSearch": 36
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.001 / $0.0009 / $0.0008 / $0.0007. One otodom.pl property listing returned with its details (title, price, price per m², rent, area, rooms, floor, city, district, agency or private owner, date). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
