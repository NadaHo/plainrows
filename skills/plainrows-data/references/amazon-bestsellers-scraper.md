# Amazon Best Sellers Scraper: Ranks, Prices & Ratings (`plainrows/amazon-bestsellers-scraper`)

Paste amazon.com Best Sellers or New Releases URLs (or category slugs), get the ranked products: rank, ASIN, title, price, rating, ratings count, image, author and format for books. No login. Pay per product plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/amazon-bestsellers-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `lists` (required) | array |  | One list per line: a Best Sellers or New Releases URL copied from amazon.com (any department or sub-category, e.g. https://www.amazon.com/gp/bestsellers/kitchen/289913/), or a category slug ("electronics", "books",... |
| `maxResultsPerList` | integer | 60 | 10 to 60. Amazon shows 30 products per page in the page itself: page 1 gives ranks 1-30, page 2 gives ranks 51-80 (ranks 31-50 are loaded later by the page's script and are not included). |

## Example input

```json
{
  "lists": [
    "https://www.amazon.com/gp/bestsellers/electronics/",
    "https://www.amazon.com/gp/new-releases/books/"
  ],
  "maxResultsPerList": 30
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Product**: $0.0015 / $0.0012 / $0.001 / $0.0008. One ranked Amazon product returned with its details (rank, ASIN, title, price, rating, ratings count, image, author and format for books). Lists without products, blocked or unreadable pages and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
