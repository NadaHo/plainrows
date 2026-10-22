# Redfin Scraper: US Homes for Sale, Prices & Details (`plainrows/redfin-scraper`)

US real estate scraper and MCP tool: paste Redfin search URLs (city, ZIP code, neighborhood, county, with filters), get every home for sale: address, coordinates, price, beds, baths, sqft, lot, year built, HOA, days on market, photo. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/redfin-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One redfin.com search URL per line: a city, ZIP code, neighborhood or county page, with or without filters (price, beds, property type…), copied from the address bar. Up to 100 searches per run; duplicates are removed. |
| `maxResultsPerSearch` | integer | 100 | Redfin shows at most 350 homes per search. For more, split a search (ZIP codes, neighborhoods, price bands). |

## Example input

```json
{
  "searches": [
    "https://www.redfin.com/city/17151/CA/San-Francisco",
    "https://www.redfin.com/zipcode/94110"
  ],
  "maxResultsPerSearch": 40
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.00035. One redfin.com home for sale returned with its details (address, coordinates, price, beds, baths, square feet, lot size, year built, type, status, days on market, HOA, photo). Searches without homes, blocked or unreadable pages, homes already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
