# Bulk Domain Authority Checker & API: DA, Spam Score & Backlinks (`plainrows/domain-authority-checker`)

SEO domain authority checker and API, bulk DA checker MCP tool: ≤ 10,000 domains a run: domain rank (0-100), SEO spam score, backlinks, referring domains and nofollow counts, one row per domain. A Moz DA checker and Ahrefs Domain Rating (DR) alternative. Pay per domain with data plus lookup fees.

Store page and full documentation: https://apify.com/plainrows/domain-authority-checker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | Domains to check, one per line: "example.com", "blog.example.com" or a full URL (it is reduced to its domain; "www." is removed). Duplicates are removed. Up to 10,000 domains per run, checked in batches of 1,000. Free... |
| `includeSpamScore` | boolean | true | Add the spam score (0-100). Each metric group adds one batch lookup per 1,000 domains; see Pricing. |
| `includeBacklinks` | boolean | false | Add the total number of live backlinks (off by default). Adds one batch lookup per 1,000 domains. |
| `includeReferringDomains` | boolean | false | Add referring domains, referring main domains and their nofollow counts (off by default). Adds one batch lookup per 1,000 domains. |

## Example input

```json
{
  "domains": [
    "apify.com",
    "forbes.com",
    "bbc.co.uk"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Domain**: $0.002 / $0.0015 / $0.0012 / $0.001. One domain returned with its domain rank, spam score, backlinks and referring domains. Domains the backlink index has no data for get a free row (only the domain lookup fee applies).
- **Batch lookup**: $0.04 / $0.037 / $0.036 / $0.035. One lookup of one metric group (rank, spam score, backlinks or referring domains) for a batch of up to 1,000 domains. A run of up to 1,000 domains with all four metric groups = 4 batch lookups.
- **Domain lookup**: $0.0002 / $0.0002 / $0.0002 / $0.0002. One domain sent to the backlink index, with or without data (the source bills every domain). Charged only once the domain rank lookup has answered.
