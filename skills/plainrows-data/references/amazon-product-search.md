# Amazon Product Search Scraper: Prices, ASINs & Ratings (`plainrows/amazon-product-search`)

Search Amazon by keyword in 15 marketplaces and get every product: ASIN, title, price, rating, reviews count, Best Seller and Amazon's Choice badges, bought last month, image and rank. Fast API results, no browser. Pay only per product found.

Store page and full documentation: https://apify.com/plainrows/amazon-product-search

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchQueries` (required) | array |  | What you would type in the Amazon search box, one per line: "wireless earbuds", "yoga mat", "usb c charger 65w". Up to 1,000 keywords per run. |
| `marketplace` | string (15 codes, see the Store page) | "US" | Amazon site to search. Prices are in that marketplace's currency. |
| `maxProductsPerQuery` | integer | 50 | From 10 to 700 (about 50 products per Amazon results page). Each product returned is billed; see Pricing. |
| `sortBy` | string: `relevance`, `featured`, `price_low_to_high`, `price_high_to_low`, `avg_customer_review`, `newest_arrival` | "relevance" | Amazon's own sort order for the results. |
| `minPrice` | integer |  | Amazon price filter, whole amount in the marketplace currency (e.g. 20 = $20 on amazon.com). Leave empty for no limit. |
| `maxPrice` | integer |  | Amazon price filter, whole amount in the marketplace currency. Leave empty for no limit. |
| `minRating` | number | 0 | Keep only products rated at least this (0 = no filter). Filtered products are not billed. |
| `minReviews` | integer | 0 | Keep only products with at least this many ratings (0 = no filter). Filtered products are not billed. |
| `includeSponsored` | boolean | false | Also return sponsored (ad) placements, flagged isSponsored: true and billed like other products. Off by default: only organic results. |
| `languageCode` | string (19 codes, see the Store page) |  | Amazon interface language, e.g. fr_FR on amazon.ca or es_US on amazon.com. Leave empty for the marketplace default. |

## Example input

```json
{
  "searchQueries": [
    "wireless earbuds"
  ],
  "marketplace": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Product**: $0.002 / $0.0015 / $0.0012 / $0.001. One Amazon product from the search results with its details (ASIN, title, price, rating, reviews count, badges, image, rank). Keywords with no result and products removed by your filters are free.
