# SEO Audit API: On-Page SEO Checker & Meta Tags (`plainrows/seo-audit-api`)

SEO audit API and MCP tool: on-page SEO checker for up to 1,000 URLs per run. One row per page: HTTP status, title and meta description with length, H1, canonical, nofollow, word count, links, missing image alt, load time, on-page score, failed checks. Pay per page, plus a small fee per run.

Store page and full documentation: https://apify.com/plainrows/seo-audit-api

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `urls` (required) | array |  | Pages to audit, one per line: "https://example.com/page" or "example.com/page" (https:// is added). Duplicates are removed. Up to 1,000 URLs per run (50 on the free Apify plan). Each URL is one page: the Actor does not... |

## Example input

```json
{
  "urls": [
    "https://apify.com",
    "https://example.com"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Page audited**: $0.004 / $0.003 / $0.0025 / $0.002. One web page read and audited: status, title and description (length), H1, canonical, word count, links, images, load time, on-page score and failed checks. Broken, redirected, refused or invalid URLs get a free row.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
