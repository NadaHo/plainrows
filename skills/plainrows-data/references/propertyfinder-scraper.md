# Property Finder Scraper: UAE Property Listings (`plainrows/propertyfinder-scraper`)

Dubai real estate scraper and MCP tool: paste propertyfinder.ae search URLs, get every property listing in Dubai, Abu Dhabi and the UAE: price, type, bedrooms, size, location, coordinates, brokerage, listed date. Sale or rent. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/propertyfinder-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One propertyfinder.ae search URL per line, copied from the address bar after choosing buy or rent, location, property type and filters (price, bedrooms, furnished…). Up to 100 searches per run; duplicates are removed. |
| `maxResultsPerSearch` | integer | 100 | Property Finder shows 25 listings per page; the Actor reads up to 20 pages (500 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "https://www.propertyfinder.ae/en/buy/dubai/apartments-for-sale.html",
    "https://www.propertyfinder.ae/en/rent/abu-dhabi/villas-for-rent.html"
  ],
  "maxResultsPerSearch": 25
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One propertyfinder.ae listing returned with its details (title, price, type, bedrooms, bathrooms, size, location, brokerage, listed date). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
