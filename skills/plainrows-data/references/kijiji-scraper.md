# Kijiji Scraper: Canada Listings, Prices & Cars (`plainrows/kijiji-scraper`)

Paste kijiji.ca search URLs or keywords, get every listing: title, price, city, province, date, image, attributes (mileage, bedrooms…), car price rating, dealer or owner. No login, no browser. Pay per listing.

Store page and full documentation: https://apify.com/plainrows/kijiji-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a keyword ("road bike", "iphone 15"), searched in all of Canada and all categories, or a search URL copied from kijiji.ca with your city, category, filters and sort order (cars, real estate, buy &... |
| `maxResultsPerSearch` | integer | 100 | Kijiji shows 40 listings per page; the Actor reads up to 20 pages (800 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "road bike",
    "https://www.kijiji.ca/b-cars-trucks/ontario/honda-civic/k0c174l9004"
  ],
  "maxResultsPerSearch": 40
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One kijiji.ca listing returned with its details (title, price, city, province, date, image, attributes, dealer or owner). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
