# AliExpress Scraper: Products, Prices, Orders & Ratings (`plainrows/aliexpress-scraper`)

AliExpress scraper and MCP tool: paste AliExpress search URLs or keywords, get every product: title, price in USD, original price, discount, rating, orders sold, ship-from country, image, ad or not. No login, no browser. Pay per product, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/aliexpress-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a keyword ("usb c cable", "wireless earbuds") or a search URL copied from aliexpress.com with your filters and sort order (e.g. sorted by orders). Up to 100 searches per run; duplicates are removed. |
| `maxResultsPerSearch` | integer | 120 | AliExpress shows 60 products per page; the Actor reads up to 20 pages (1,200 products) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "wireless earbuds",
    "https://www.aliexpress.com/w/wholesale-phone-case.html"
  ],
  "maxResultsPerSearch": 60
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Product**: $0.0015 / $0.0013 / $0.0011 / $0.001. One AliExpress product returned with its details (title, price, original price, discount, rating, orders, ship-from country, image, ad or not). Searches without products, blocked or unreadable pages, products already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
