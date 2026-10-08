---
name: plainrows-data
description: Get structured web data as JSON rows by calling PlainRows Actors on Apify - Keyword Search Volume, CPC & Difficulty; Keyword Ideas Generator; Website Organic Traffic & Top Keywords; Bulk Domain Authority Checker; Backlink Checker; Google Maps Businesses Scraper; Google Ads Transparency Scraper; Amazon Product Search Scraper; Google News Scraper; YouTube Search Scraper. Use when a task needs SEO metrics, business leads or search data and the user has (or can create) an Apify API token. Pay per use.
compatibility: Needs network access to api.apify.com and an APIFY_TOKEN environment variable (free Apify account).
metadata:
  author: PlainRows
  homepage: https://nadaho.github.io/plainrows/
---

# PlainRows data tools

Each tool is an Apify Actor that returns flat JSON rows. All tools share one API and one token.

## How to call a tool

1. The user needs an Apify API token (Apify Console > Settings > API & Integrations; the free plan includes monthly usage).
   Read it from the `APIFY_TOKEN` environment variable. Never print it or write it to a file.
2. Pick the tool in the table below and read its reference file for the input fields.
3. Run it and get the rows in one call (waits up to 300 seconds):

```bash
curl -s -X POST "https://api.apify.com/v2/acts/plainrows~<slug>/run-sync-get-dataset-items?maxTotalChargeUsd=1" \
  -H "Authorization: Bearer $APIFY_TOKEN" -H "Content-Type: application/json" \
  -d '<input JSON>'
```

`maxTotalChargeUsd` caps what the run can cost: the run stops cleanly at that amount. Keep it low for a first try.

For long runs, start the run without waiting (`POST /v2/acts/plainrows~<slug>/runs`), poll `GET /v2/actor-runs/<runId>`
until `status` is `SUCCEEDED`, then read `GET /v2/datasets/<defaultDatasetId>/items?clean=true`.

## Rules that matter

- Rows with `"found": false` mean the source had no data for that input; they are not billed as results (some tools charge a small fixed fee per search, listed on their pricing table).
- Missing values are `null`, never guessed.
- Invalid inputs end the run without charge; the reason is in the run's status message and in the `OUTPUT` record of its key-value store.
- Prices are per result (see each reference file). Tell the user the expected cost before large runs.

## Tools

| Actor | What it returns | Price | Input reference |
|---|---|---|---|
| `plainrows/amazon-product-search` | Amazon Product Search Scraper: Prices, ASINs & Ratings | from $0.001 per product | [references/amazon-product-search.md](references/amazon-product-search.md) |
| `plainrows/backlink-checker` | Backlink Checker API: Backlinks, Referring Domains & Anchors | from $0.0012 per backlink | [references/backlink-checker.md](references/backlink-checker.md) |
| `plainrows/domain-authority-checker` | Domain Authority Checker: Bulk Rank, Backlinks & Spam Score | from $0.001 per domain | [references/domain-authority-checker.md](references/domain-authority-checker.md) |
| `plainrows/domain-seo-overview` | Website Traffic Checker: Organic Traffic & Keywords | from $0.003 per domain | [references/domain-seo-overview.md](references/domain-seo-overview.md) |
| `plainrows/google-ads-transparency` | Google Ads Transparency Scraper: Competitor Ads Library | from $0.0006 per ad | [references/google-ads-transparency.md](references/google-ads-transparency.md) |
| `plainrows/google-maps-businesses` | Google Maps Businesses Scraper: Leads, Phones & Ratings | from $0.001 per place | [references/google-maps-businesses.md](references/google-maps-businesses.md) |
| `plainrows/google-news-scraper` | Google News Scraper API: Articles, Sources & Dates | from $0.0009 per article | [references/google-news-scraper.md](references/google-news-scraper.md) |
| `plainrows/keyword-ideas-generator` | Keyword Ideas Generator: Volume, CPC & Difficulty | from $0.002 per keyword | [references/keyword-ideas-generator.md](references/keyword-ideas-generator.md) |
| `plainrows/keyword-search-volume` | Keyword Search Volume, CPC & Difficulty | from $0.006 per keyword | [references/keyword-search-volume.md](references/keyword-search-volume.md) |
| `plainrows/youtube-search-scraper` | YouTube Search Scraper: Videos, Views & Channels by Keyword | from $0.001 per video | [references/youtube-search-scraper.md](references/youtube-search-scraper.md) |

Other ways to use the same tools: MCP server `https://mcp.apify.com?tools=plainrows/<slug>`, n8n, Make and Zapier (Apify integration).
