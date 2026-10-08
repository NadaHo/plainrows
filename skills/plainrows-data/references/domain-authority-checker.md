# Domain Authority Checker: Bulk Rank, Backlinks & Spam Score (`plainrows/domain-authority-checker`)

Check domain authority for up to 10,000 domains per run: domain rank (0-100), spam score, backlinks, referring domains and nofollow counts in one row per domain. Licensed backlink data, results in seconds. Pay only per domain with data.

Store page and full documentation: https://apify.com/plainrows/domain-authority-checker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | Domains to check, one per line: "example.com", "blog.example.com" or a full URL (it is reduced to its domain; "www." is removed). Duplicates are removed. Up to 10,000 domains per run, checked in batches of 1,000. |
| `includeSpamScore` | boolean | true | Add the spam score (0-100). Each metric group adds one batch lookup per 1,000 domains; see Pricing. |
| `includeBacklinks` | boolean | true | Add the total number of live backlinks. Adds one batch lookup per 1,000 domains. |
| `includeReferringDomains` | boolean | true | Add referring domains, referring main domains and their nofollow counts. Adds one batch lookup per 1,000 domains. |

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

- **Domain**: $0.002 / $0.0015 / $0.0012 / $0.001. One domain returned with its domain rank, spam score, backlinks and referring domains. Domains the backlink index has no data for are free.
- **Batch lookup**: $0.04 / $0.035 / $0.033 / $0.032. One lookup of one metric group (rank, spam score, backlinks or referring domains) for a batch of up to 1,000 domains. A run of up to 1,000 domains with all four metric groups = 4 batch lookups.
