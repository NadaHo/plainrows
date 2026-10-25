# FINN Scraper (FINN.no): Norway Marketplace Listings (`plainrows/finn-scraper`)

Norway marketplace scraper and MCP tool: type a keyword or paste finn.no "for sale" search URLs, get every listing: title, price, city, coordinates, private or business seller, brand, shipping, photos, date. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/finn-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One per line: a keyword ("iphone", "sykkel") or a finn.no search URL from the Torget (for sale) section, copied from the address bar after setting filters (category, price, location, private or business, shipping…) and... |
| `maxResultsPerSearch` | integer | 100 | FINN shows about 50 listings per page; the Actor reads up to 20 pages (1,000 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "iphone",
    "https://www.finn.no/recommerce/forsale/search?q=iphone&price_to=5000"
  ],
  "maxResultsPerSearch": 50
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0005 / $0.00045 / $0.0004 / $0.0004. One FINN listing returned with its details (title, price, city, coordinates, private or business seller, brand, shipping, photos, date). Searches without listings, blocked or unreadable pages, other sections of the site, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
