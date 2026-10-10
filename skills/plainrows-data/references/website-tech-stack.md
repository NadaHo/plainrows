# Website Technology Checker: Tech Stack & CMS Detector (`plainrows/website-tech-stack`)

Find the tech stack of any list of websites: CMS, ecommerce platform, analytics, tag managers, CDN, hosting, frameworks, payments, live chat and email provider, with versions. Bulk domains in, one spreadsheet-ready row per site. Pay only per site analysed.

Store page and full documentation: https://apify.com/plainrows/website-tech-stack

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | Domains or URLs, one per line: "shopify.com", "https://www.example.org/page". The homepage of each site is analysed ("www." and paths are ignored). Up to 10,000 per run; duplicates are removed. |
| `minConfidence` | integer | 0 | Hide technologies detected with a lower confidence (0 = show all, like Wappalyzer; 100 = only certain detections). It does not change the price. |

## Example input

```json
{
  "domains": [
    "shopify.com",
    "wordpress.org",
    "nextjs.org"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Website**: $0.001 / $0.0009 / $0.0008 / $0.0006. One website whose homepage was loaded and analysed (technologies, versions, categories, title). Sites that cannot be loaded (no DNS, timeout, HTTP error, bot protection) are free.
