# Shopify Scraper: Products, Prices, Variants & Stock (`plainrows/shopify-products-scraper`)

Shopify scraper and MCP tool: products, prices, compare-at prices, stock, variants with SKU, options, images, tags and descriptions from any Shopify store, collection or product URL. Reads the store's public product feed. Pay per product + start fee.

Store page and full documentation: https://apify.com/plainrows/shopify-products-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `startUrls` (required) | array |  | Store domains ("allbirds.com"), store URLs, collection URLs ("https://www.colourpop.com/collections/lips") or product URLs ("https://www.allbirds.com/products/mens-wool-runner-nz-mid-waterproof-natural-black"). Up to... |
| `maxProductsPerInput` | integer | 100 | Products read per store or collection (the store feed gives 250 per page, newest first). Each product returned is billed; see Pricing. Example: 100. |

## Example input

```json
{
  "startUrls": [
    "allbirds.com",
    "https://www.colourpop.com/collections/lips"
  ],
  "maxProductsPerInput": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Product**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One Shopify product with its data. Sites not on Shopify, closed stores and refused requests are free rows.
- **Actor Start**: $0.0005 / $0.0005 / $0.0005 / $0.0005. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
