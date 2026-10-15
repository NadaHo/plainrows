---
name: plainrows-data
description: Get structured web data as JSON rows by calling PlainRows Actors on Apify - Keyword Search Volume, CPC & Difficulty; Keyword Planner Alternative (Bulk Search Volume & CPC); Keyword Ideas Generator; Google Autocomplete & People Also Ask; Google Trends Explorer; Website Organic Traffic & Top Keywords; Bulk Domain Authority Checker; Backlink Checker; Broken Link Checker; AI Search Visibility Tracker (ChatGPT, Gemini, AI Mode); Google Maps Rank Tracker (Geo-Grid Local SEO); Google Maps Scraper; Google Maps Email Extractor; Google Maps Businesses Without Website; Website Technology Checker; Website Email Extractor; Contact Details Scraper (Emails, Phones, Socials); ATS Jobs Scraper (Workday, Greenhouse, Lever, Ashby); Workday Jobs Scraper; Greenhouse Jobs Scraper; Lever Jobs Scraper; Ashby Jobs Scraper; Google Jobs Scraper; Google Ads Scraper (Transparency Center); Company Registry Lookup (SIRENE, LEI, Brreg); Public Tenders Search (EU TED & UK); Amazon Product Search Scraper; Google Shopping Prices Scraper;...
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
| `plainrows/ai-search-brand-visibility` | AI Search Visibility Tracker: ChatGPT, Gemini & Google AI Mode | from $0.01 per ai answer | [references/ai-search-brand-visibility.md](references/ai-search-brand-visibility.md) |
| `plainrows/amazon-product-search` | Amazon Product Scraper: Search, Prices, ASINs & Ratings | from $0.001 per product | [references/amazon-product-search.md](references/amazon-product-search.md) |
| `plainrows/app-reviews-scraper` | App Store Reviews & Google Play Reviews Scraper | from $0.00005 per review | [references/app-reviews-scraper.md](references/app-reviews-scraper.md) |
| `plainrows/app-store-reviews-scraper` | App Store Reviews Scraper: iOS Ratings, Titles & Text | from $0.00005 per review | [references/app-store-reviews-scraper.md](references/app-store-reviews-scraper.md) |
| `plainrows/ashby-jobs-scraper` | Ashby Jobs Scraper: Any Ashby Job Board | from $0.0008 per job | [references/ashby-jobs-scraper.md](references/ashby-jobs-scraper.md) |
| `plainrows/ats-job-postings` | ATS Jobs Scraper: Workday, Greenhouse, Lever & Ashby | from $0.0008 per job | [references/ats-job-postings.md](references/ats-job-postings.md) |
| `plainrows/backlink-checker` | Backlink Checker API: Backlinks, Referring Domains & Anchors | from $0.0012 per backlink | [references/backlink-checker.md](references/backlink-checker.md) |
| `plainrows/broken-link-checker` | Broken Link Checker: 404s, Redirect Chains & Sitemaps | from $0.0006 per page | [references/broken-link-checker.md](references/broken-link-checker.md) |
| `plainrows/company-registry-lookup` | Company Registry Lookup: SIRENE, LEI, Brreg & KYB Data | from $0.0012 per company | [references/company-registry-lookup.md](references/company-registry-lookup.md) |
| `plainrows/contact-details-scraper` | Contact Details Scraper: Emails, Phones & Social Profiles | from $0.0015 per website with contacts | [references/contact-details-scraper.md](references/contact-details-scraper.md) |
| `plainrows/domain-authority-checker` | Domain Authority Checker: Bulk Rank, Backlinks & Spam Score | from $0.001 per domain | [references/domain-authority-checker.md](references/domain-authority-checker.md) |
| `plainrows/domain-seo-overview` | Website Traffic Checker: Organic Traffic, Semrush Alternative | from $0.003 per domain | [references/domain-seo-overview.md](references/domain-seo-overview.md) |
| `plainrows/google-ads-transparency` | Google Ads Scraper: Google Ads Transparency Center | from $0.0006 per ad | [references/google-ads-transparency.md](references/google-ads-transparency.md) |
| `plainrows/google-autocomplete-questions` | Google Autocomplete & People Also Ask Questions Scraper | from $0.0003 per suggestion | [references/google-autocomplete-questions.md](references/google-autocomplete-questions.md) |
| `plainrows/google-hotels-prices` | Google Hotels Prices Scraper: Price Comparison of Booking Sites | from $0.0008 per hotel | [references/google-hotels-prices.md](references/google-hotels-prices.md) |
| `plainrows/google-hotels-scraper` | Google Hotels Scraper: Prices, Ratings & Booking Sites | from $0.0008 per hotel | [references/google-hotels-scraper.md](references/google-hotels-scraper.md) |
| `plainrows/google-images-scraper` | Google Images Scraper API: Image URLs, Sources & Filters | from $0.0006 per image | [references/google-images-scraper.md](references/google-images-scraper.md) |
| `plainrows/google-jobs-scraper` | Google Jobs Scraper: Listings, Salaries & Apply Links | from $0.0008 per job listing | [references/google-jobs-scraper.md](references/google-jobs-scraper.md) |
| `plainrows/google-maps-businesses` | Google Maps Scraper: Business Leads, Phones & Ratings | from $0.001 per place | [references/google-maps-businesses.md](references/google-maps-businesses.md) |
| `plainrows/google-maps-email-extractor` | Google Maps Email Extractor: Business Leads with Emails | from $0.001 per place | [references/google-maps-email-extractor.md](references/google-maps-email-extractor.md) |
| `plainrows/google-maps-no-website-leads` | Google Maps Businesses Without Website: Web Design Leads | from $0.001 per place | [references/google-maps-no-website-leads.md](references/google-maps-no-website-leads.md) |
| `plainrows/google-maps-rank-tracker` | Google Maps Rank Tracker: Geo-Grid Local SEO | from $0.006 per grid point checked | [references/google-maps-rank-tracker.md](references/google-maps-rank-tracker.md) |
| `plainrows/google-maps-reviews` | Google Maps Reviews Scraper | from $0.0002 per review | [references/google-maps-reviews.md](references/google-maps-reviews.md) |
| `plainrows/google-news-scraper` | Google News Scraper API: Articles, Sources & Dates | from $0.0009 per article | [references/google-news-scraper.md](references/google-news-scraper.md) |
| `plainrows/google-play-reviews-scraper` | Google Play Reviews Scraper: Ratings, Text & Replies | from $0.00005 per review | [references/google-play-reviews-scraper.md](references/google-play-reviews-scraper.md) |
| `plainrows/google-reviews-scraper` | Google Reviews Scraper: Ratings, Text & Owner Replies | from $0.0002 per review | [references/google-reviews-scraper.md](references/google-reviews-scraper.md) |
| `plainrows/google-shopping-prices` | Google Shopping Prices Scraper: Products, Stores & Deals | from $0.001 per product offer | [references/google-shopping-prices.md](references/google-shopping-prices.md) |
| `plainrows/google-trends-explorer` | Google Trends Scraper API: Interest, Regions & Queries | from $0.004 per google trends search | [references/google-trends-explorer.md](references/google-trends-explorer.md) |
| `plainrows/greenhouse-jobs-scraper` | Greenhouse Jobs Scraper: Any Greenhouse Job Board | from $0.0008 per job | [references/greenhouse-jobs-scraper.md](references/greenhouse-jobs-scraper.md) |
| `plainrows/keyword-ideas-generator` | Keyword Research Tool: Keyword Ideas, Volume & Difficulty | from $0.002 per keyword | [references/keyword-ideas-generator.md](references/keyword-ideas-generator.md) |
| `plainrows/keyword-planner-alternative` | Keyword Planner Alternative: Bulk Search Volume & CPC | from $0.0007 per keyword | [references/keyword-planner-alternative.md](references/keyword-planner-alternative.md) |
| `plainrows/keyword-search-volume` | Keyword Search Volume & Keyword Difficulty: Ahrefs Alternative | from $0.006 per keyword | [references/keyword-search-volume.md](references/keyword-search-volume.md) |
| `plainrows/lever-jobs-scraper` | Lever Jobs Scraper: Any Lever Job Board | from $0.0008 per job | [references/lever-jobs-scraper.md](references/lever-jobs-scraper.md) |
| `plainrows/public-tenders-search` | Public Tenders Search: EU TED & UK Procurement API | from $0.0015 per notice | [references/public-tenders-search.md](references/public-tenders-search.md) |
| `plainrows/tripadvisor-reviews` | Tripadvisor Reviews Scraper API: Hotels & Restaurants | from $0.0002 per review | [references/tripadvisor-reviews.md](references/tripadvisor-reviews.md) |
| `plainrows/trustpilot-reviews` | Trustpilot Reviews Scraper: New Reviews & Replies | from $0.0002 per review | [references/trustpilot-reviews.md](references/trustpilot-reviews.md) |
| `plainrows/website-email-extractor` | Website Email Extractor: Emails, Phones & Socials from URLs | from $0.0015 per website with contacts | [references/website-email-extractor.md](references/website-email-extractor.md) |
| `plainrows/website-screenshot` | Website Screenshot API: Full Page, Mobile & Bulk Capture | from $0.0018 per screenshot | [references/website-screenshot.md](references/website-screenshot.md) |
| `plainrows/website-tech-stack` | Website Technology Checker: Tech Stack & CMS Detector | from $0.0006 per website | [references/website-tech-stack.md](references/website-tech-stack.md) |
| `plainrows/workday-jobs-scraper` | Workday Jobs Scraper: Any myworkdayjobs Careers Site | from $0.0008 per job | [references/workday-jobs-scraper.md](references/workday-jobs-scraper.md) |
| `plainrows/youtube-comments-scraper` | YouTube Comments Scraper: Video Comments Export | from $0.0002 per comment | [references/youtube-comments-scraper.md](references/youtube-comments-scraper.md) |
| `plainrows/youtube-search-scraper` | YouTube Search Scraper: Videos, Views & Channels by Keyword | from $0.001 per video | [references/youtube-search-scraper.md](references/youtube-search-scraper.md) |

Other ways to use the same tools: MCP server `https://mcp.apify.com?tools=plainrows/<slug>`, n8n, Make and Zapier (Apify integration).
