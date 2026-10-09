# Google Shopping Prices Scraper: Products, Stores & Deals (`plainrows/google-shopping-prices`)

Get Google Shopping prices for any search or product: price, old price and discount, seller, rating, delivery, image, plus each store's offer with domain, shipping and total price. 20 countries, no browser, no proxies. Pay only per result.

Store page and full documentation: https://apify.com/plainrows/google-shopping-prices

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchQueries` | array |  | What you would type in Google Shopping, one per line: a product name, model or category, e.g. "sony wh-1000xm5", "espresso machine". Up to 1,000 per run. Leave empty if you only use Product IDs below. |
| `productIds` | array |  | Google Shopping product IDs (the productId column of a search run, or a Google Shopping link that contains one). For each product you get every store's offer: store domain, link, price, shipping and total price. Search... |
| `country` | string (20 codes, see the Store page) | "US" | Google Shopping market (prices and stores of this country). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxProductsPerQuery` | integer | 40 | Google Shopping shows up to about 120 products per search. Each product returned is billed; see Pricing. |
| `maxOffersPerProduct` | integer | 20 | Popular products can have 40 or more store offers (Google's order: best known stores first). Each offer returned is billed. |
| `sortBy` | string: `relevance`, `price_low_to_high`, `price_high_to_low`, `review_score` | "relevance" | Order of the search results, as on Google Shopping. Applies to search queries only. |
| `minPrice` | integer |  | Only products from this price, in the country's currency (whole number). Applies to search queries only. |
| `maxPrice` | integer |  | Only products up to this price, in the country's currency (whole number). Applies to search queries only. |

## Example input

```json
{
  "searchQueries": [
    "sony wh-1000xm5"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Product offer**: $0.002 / $0.0015 / $0.0012 / $0.001. One Google Shopping product listing or one store offer returned with its price and details. Searches or product IDs with no result, and sponsored listings, are free.
