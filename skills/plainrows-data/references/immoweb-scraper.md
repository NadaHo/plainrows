# Immoweb Scraper: Belgium Property Listings & Prices (`plainrows/immoweb-scraper`)

Belgium real estate scraper and MCP tool: paste immoweb.be search URLs, get every listing: price, type, bedrooms, living area, energy class (EPC), locality, postal code, agency, date. Houses, flats, land, buy or rent. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/immoweb-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One immoweb.be search URL per line, copied from the address bar after choosing the property type, buy or rent and the location (e.g. https://www.immoweb.be/en/search/house/for-sale/gent/9000). English, French or Dutch... |
| `maxResultsPerSearch` | integer | 90 | Immoweb shows 30 listings per page; the Actor reads up to 20 pages (600 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "https://www.immoweb.be/en/search/apartment/for-sale/brussels/1000",
    "https://www.immoweb.be/en/search/house/for-rent/antwerp/2000"
  ],
  "maxResultsPerSearch": 30
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.00055 / $0.0005 / $0.00045 / $0.0004. One immoweb.be property listing returned with its details (price, type, bedrooms, area, energy class, locality, postal code, agency, date). Searches without listings, blocked or unreadable pages, listings without a price, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
