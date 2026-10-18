# Amazon Reviews Scraper: Ratings, Text & Dates (`plainrows/amazon-reviews-scraper`)

Paste amazon.com ASINs or product URLs, get the top customer reviews shown on each product page: rating, title, text, date, country, verified purchase, helpful votes. No login. Pay per review plus small product and start fees.

Store page and full documentation: https://apify.com/plainrows/amazon-reviews-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `products` (required) | array |  | One product per line: an ASIN (e.g. 0593139135) or a product URL copied from amazon.com (/dp/, /gp/product/ or /product-reviews/ links). amazon.com only. Up to 500 products per run; duplicates are removed. Each product... |
| `minRating` | integer | 1 | Keep only reviews rated at least this many stars (1 to 5). Filtered-out reviews are not charged; the product page fee still is. |
| `maxRating` | integer | 5 | Keep only reviews rated at most this many stars, e.g. 2 for critical reviews only. |
| `onlyNewReviews` | boolean | false | Return (and charge) only reviews that earlier runs with this option have not delivered yet. Useful on a schedule. The product page fee is still charged for each page read with reviews. |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered reviews (default "plainrows-amazon-reviews-monitor"). Use another name per monitoring task to keep separate histories. Lowercase letters, digits... |

## Example input

```json
{
  "products": [
    "0593139135",
    "https://www.amazon.com/dp/B0BSHF7WHW"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Review**: $0.0006 / $0.00055 / $0.0005 / $0.00045. One customer review returned with its details (rating, title, text, date, country, verified purchase, helpful votes). Reviews filtered out by your rating range, already delivered (only new reviews) or unreadable are not charged.
- **Product page read**: $0.008 / $0.008 / $0.008 / $0.008. Charged once per product page read that shows at least one review (it pays the residential proxy traffic of the page, about 1.5 MB, up to 2 reads). Blocked, missing or unreadable pages and products without reviews in the page are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
