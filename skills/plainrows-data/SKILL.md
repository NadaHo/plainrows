---
name: plainrows-data
description: Get structured web data as JSON rows by calling PlainRows Actors on Apify - Keyword Search Volume, CPC & Difficulty; Keyword Planner Alternative (Bulk Search Volume & CPC); Bing Keyword Search Volume & CPC; Keyword Ideas Generator; Google Autocomplete & People Also Ask; Google Trends Explorer; Website Organic Traffic & Top Keywords; SEO Competitors & Keyword Gap Finder; Bulk Domain Authority Checker; Backlink Checker; Broken Link Checker; AI Search Visibility Tracker (ChatGPT, Gemini, AI Mode); Google Maps Rank Tracker (Geo-Grid Local SEO); Google Maps Scraper; Google Maps Email Extractor; Google Maps Businesses Without Website; Yellow Pages Australia Scraper; Website Technology Checker; Website Email Extractor; Contact Details Scraper (Emails, Phones, Socials); ATS Jobs Scraper (Workday, Greenhouse, Lever, Ashby); Workday Jobs Scraper; Greenhouse Jobs Scraper; Lever Jobs Scraper; Ashby Jobs Scraper; Google Jobs Scraper; Reed.co.uk Jobs Scraper (UK); jobs.ch & jobup.ch Jobs Scraper (Switzerland);...
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
| `plainrows/2dehands-scraper` | 2dehands Scraper: Belgian Listings & Prices | from $0.0005 per listing | [references/2dehands-scraper.md](references/2dehands-scraper.md) |
| `plainrows/ai-search-brand-visibility` | AI Visibility Tracker: ChatGPT Visibility & LLM Visibility | from $0.01 per ai answer | [references/ai-search-brand-visibility.md](references/ai-search-brand-visibility.md) |
| `plainrows/aliexpress-scraper` | AliExpress Scraper: Products, Prices, Orders & Ratings | from $0.001 per product | [references/aliexpress-scraper.md](references/aliexpress-scraper.md) |
| `plainrows/amazon-product-search` | Amazon Product Scraper: Search, Prices, ASINs & Ratings | from $0.001 per product | [references/amazon-product-search.md](references/amazon-product-search.md) |
| `plainrows/app-details-scraper` | App Store Scraper & Google Play Scraper: App Details | from $0.001 per app | [references/app-details-scraper.md](references/app-details-scraper.md) |
| `plainrows/app-reviews-scraper` | App Store Reviews & Google Play Reviews Scraper | from $0.00005 per review | [references/app-reviews-scraper.md](references/app-reviews-scraper.md) |
| `plainrows/app-store-reviews-scraper` | App Store Reviews Scraper: iOS Ratings, Titles & Text | from $0.00005 per review | [references/app-store-reviews-scraper.md](references/app-store-reviews-scraper.md) |
| `plainrows/arbeitsagentur-jobs-scraper` | Germany Jobs Scraper: Arbeitsagentur API, Bundesagentur Jobs | from $0.0006 per job | [references/arbeitsagentur-jobs-scraper.md](references/arbeitsagentur-jobs-scraper.md) |
| `plainrows/ashby-jobs-scraper` | Ashby Jobs Scraper: Any Ashby Job Board | from $0.0008 per job | [references/ashby-jobs-scraper.md](references/ashby-jobs-scraper.md) |
| `plainrows/ats-job-postings` | ATS Jobs Scraper: Workday, Greenhouse, Lever & Ashby | from $0.0008 per job | [references/ats-job-postings.md](references/ats-job-postings.md) |
| `plainrows/autoscout24-scraper` | AutoScout24 Scraper: Car Listings, Prices & Mileage | from $0.0004 per listing | [references/autoscout24-scraper.md](references/autoscout24-scraper.md) |
| `plainrows/autovit-scraper` | Autovit Scraper: Romania Car Listings & Prices | from $0.0004 per listing | [references/autovit-scraper.md](references/autovit-scraper.md) |
| `plainrows/backlink-checker` | Bulk Backlink Checker: Referring Domains & Anchor Text API | from $0.0012 per backlink or referring domain | [references/backlink-checker.md](references/backlink-checker.md) |
| `plainrows/bing-keyword-search-volume` | Bing Keyword Search Volume: Bulk Bing Ads Volume & CPC | from $0.0001 per keyword | [references/bing-keyword-search-volume.md](references/bing-keyword-search-volume.md) |
| `plainrows/blocket-scraper` | Blocket Scraper: Sweden Marketplace Listings | from $0.0004 per listing | [references/blocket-scraper.md](references/blocket-scraper.md) |
| `plainrows/broken-link-checker` | Broken Link Checker: 404s, Redirect Chains & Sitemaps | from $0.0006 per page | [references/broken-link-checker.md](references/broken-link-checker.md) |
| `plainrows/catho-jobs-scraper` | Catho Jobs Scraper: Brazil Job Ads from catho.com.br | from $0.0009 per job | [references/catho-jobs-scraper.md](references/catho-jobs-scraper.md) |
| `plainrows/coches-net-scraper` | coches.net Scraper: Spain Car Listings, Prices & Mileage | from $0.0004 per listing | [references/coches-net-scraper.md](references/coches-net-scraper.md) |
| `plainrows/company-registry-lookup` | Company Registry Lookup: SIRENE, LEI, Brreg & KYB Data | from $0.0012 per company | [references/company-registry-lookup.md](references/company-registry-lookup.md) |
| `plainrows/contact-details-scraper` | Contact Details Scraper: Emails, Phones & Social Profiles | from $0.0015 per website with contacts | [references/contact-details-scraper.md](references/contact-details-scraper.md) |
| `plainrows/dba-scraper` | DBA Scraper: Denmark Marketplace Listings | from $0.0004 per listing | [references/dba-scraper.md](references/dba-scraper.md) |
| `plainrows/domain-authority-checker` | Domain Authority Checker: Bulk Rank, Backlinks & Spam Score | from $0.001 per domain | [references/domain-authority-checker.md](references/domain-authority-checker.md) |
| `plainrows/domain-seo-overview` | Competitor Keywords & Organic Traffic: Semrush Alternative | from $0.003 per domain | [references/domain-seo-overview.md](references/domain-seo-overview.md) |
| `plainrows/finn-cars-scraper` | FINN.no Car Scraper: Norway Used Car Listings | from $0.0006 per car listing | [references/finn-cars-scraper.md](references/finn-cars-scraper.md) |
| `plainrows/finn-scraper` | FINN.no Scraper: Norway Marketplace Listings | from $0.0004 per listing | [references/finn-scraper.md](references/finn-scraper.md) |
| `plainrows/google-ads-transparency` | Google Ads Scraper: Google Ads Transparency Center | from $0.0006 per ad | [references/google-ads-transparency.md](references/google-ads-transparency.md) |
| `plainrows/google-autocomplete-questions` | Google Autocomplete & People Also Ask Questions Scraper | from $0.0003 per suggestion | [references/google-autocomplete-questions.md](references/google-autocomplete-questions.md) |
| `plainrows/google-hotels-prices` | Google Hotels Prices Scraper: Price Comparison of Booking Sites | from $0.0008 per hotel | [references/google-hotels-prices.md](references/google-hotels-prices.md) |
| `plainrows/google-hotels-scraper` | Google Hotels Scraper: Prices, Ratings & Booking Sites | from $0.0008 per hotel | [references/google-hotels-scraper.md](references/google-hotels-scraper.md) |
| `plainrows/google-images-scraper` | Google Images Scraper API: Image URLs, Sources & Filters | from $0.0006 per image | [references/google-images-scraper.md](references/google-images-scraper.md) |
| `plainrows/google-jobs-scraper` | Google Jobs Scraper: Listings, Salaries & Apply Links | from $0.0008 per job listing | [references/google-jobs-scraper.md](references/google-jobs-scraper.md) |
| `plainrows/google-maps-businesses` | Google Maps Scraper: Business Leads, Emails & Phones | from $0.001 per place | [references/google-maps-businesses.md](references/google-maps-businesses.md) |
| `plainrows/google-maps-email-extractor` | Google Maps Email Extractor: Business Leads with Emails | from $0.001 per place | [references/google-maps-email-extractor.md](references/google-maps-email-extractor.md) |
| `plainrows/google-maps-no-website-leads` | Google Maps Businesses Without Website: Web Design Leads | from $0.001 per place | [references/google-maps-no-website-leads.md](references/google-maps-no-website-leads.md) |
| `plainrows/google-maps-rank-tracker` | Google Maps Rank Tracker: Geo-Grid Local SEO | from $0.006 per grid point checked | [references/google-maps-rank-tracker.md](references/google-maps-rank-tracker.md) |
| `plainrows/google-maps-reviews` | Google Maps Reviews Scraper | from $0.0002 per review | [references/google-maps-reviews.md](references/google-maps-reviews.md) |
| `plainrows/google-news-scraper` | Google News Scraper API: Articles, Sources & Dates | from $0.0009 per article | [references/google-news-scraper.md](references/google-news-scraper.md) |
| `plainrows/google-play-reviews-scraper` | Google Play Reviews Scraper: Ratings, Text & Replies | from $0.00005 per review | [references/google-play-reviews-scraper.md](references/google-play-reviews-scraper.md) |
| `plainrows/google-reviews-scraper` | Google Reviews Scraper: Ratings, Text & Owner Replies | from $0.0002 per review | [references/google-reviews-scraper.md](references/google-reviews-scraper.md) |
| `plainrows/google-shopping-prices` | Google Shopping Prices Scraper: Products, Stores & Deals | from $0.001 per product offer | [references/google-shopping-prices.md](references/google-shopping-prices.md) |
| `plainrows/google-trends-explorer` | Google Trends Scraper & Google Trends API: Regions & Queries | from $0.004 per google trends search | [references/google-trends-explorer.md](references/google-trends-explorer.md) |
| `plainrows/greenhouse-jobs-scraper` | Greenhouse Jobs Scraper: Any Greenhouse Job Board | from $0.0008 per job | [references/greenhouse-jobs-scraper.md](references/greenhouse-jobs-scraper.md) |
| `plainrows/gupy-jobs-scraper` | Gupy Jobs Scraper: Brazil Job Ads from portal.gupy.io | from $0.0009 per job | [references/gupy-jobs-scraper.md](references/gupy-jobs-scraper.md) |
| `plainrows/immoweb-scraper` | Immoweb Scraper: Belgium Property Listings & Prices | from $0.0004 per listing | [references/immoweb-scraper.md](references/immoweb-scraper.md) |
| `plainrows/imovirtual-scraper` | Imovirtual Scraper: Portugal Property Listings & Prices | from $0.0004 per listing | [references/imovirtual-scraper.md](references/imovirtual-scraper.md) |
| `plainrows/jobs-ch-scraper` | Switzerland Jobs Scraper: jobs.ch & jobup.ch Swiss Job Ads | from $0.0009 per job | [references/jobs-ch-scraper.md](references/jobs-ch-scraper.md) |
| `plainrows/jobs-cz-scraper` | Czech Jobs Scraper: Jobs.cz Job Listings & Salaries | from $0.0009 per job | [references/jobs-cz-scraper.md](references/jobs-cz-scraper.md) |
| `plainrows/keyword-ideas-generator` | Keyword Research Tool: Keyword Ideas & Related Keywords | from $0.002 per keyword | [references/keyword-ideas-generator.md](references/keyword-ideas-generator.md) |
| `plainrows/keyword-planner-alternative` | Keyword Planner Alternative: Bulk Search Volume & CPC | from $0.0007 per keyword | [references/keyword-planner-alternative.md](references/keyword-planner-alternative.md) |
| `plainrows/keyword-search-volume` | Keyword Search Volume API & Difficulty: Ahrefs Alternative | from $0.006 per keyword | [references/keyword-search-volume.md](references/keyword-search-volume.md) |
| `plainrows/kijiji-scraper` | Kijiji Scraper: Canada Listings, Prices & Cars | from $0.0005 per listing | [references/kijiji-scraper.md](references/kijiji-scraper.md) |
| `plainrows/kleinanzeigen-scraper` | Kleinanzeigen Scraper: Listings, Prices & Locations | from $0.0007 per listing | [references/kleinanzeigen-scraper.md](references/kleinanzeigen-scraper.md) |
| `plainrows/lever-jobs-scraper` | Lever Jobs Scraper: Any Lever Job Board | from $0.0008 per job | [references/lever-jobs-scraper.md](references/lever-jobs-scraper.md) |
| `plainrows/marktplaats-scraper` | Marktplaats Scraper: Dutch Listings & Prices | from $0.0005 per listing | [references/marktplaats-scraper.md](references/marktplaats-scraper.md) |
| `plainrows/otodom-scraper` | Otodom Scraper: Poland Property Listings & Prices | from $0.0007 per listing | [references/otodom-scraper.md](references/otodom-scraper.md) |
| `plainrows/otomoto-scraper` | Otomoto Scraper: Polish Car Listings & Prices | from $0.0004 per listing | [references/otomoto-scraper.md](references/otomoto-scraper.md) |
| `plainrows/propertyfinder-scraper` | Property Finder Scraper: UAE Property Listings | from $0.0005 per listing | [references/propertyfinder-scraper.md](references/propertyfinder-scraper.md) |
| `plainrows/public-tenders-search` | Public Tenders Search: EU TED & UK Procurement API | from $0.0015 per notice | [references/public-tenders-search.md](references/public-tenders-search.md) |
| `plainrows/redfin-scraper` | Redfin Scraper: US Homes for Sale, Prices & Details | from $0.00035 per listing | [references/redfin-scraper.md](references/redfin-scraper.md) |
| `plainrows/reed-jobs-scraper` | UK Jobs Scraper: Reed.co.uk Job Ads & Salaries | from $0.0005 per job | [references/reed-jobs-scraper.md](references/reed-jobs-scraper.md) |
| `plainrows/seo-competitors-keyword-gap` | SEO Competitors & Keyword Gap Finder | from $0.0016 per competitor or gap keyword | [references/seo-competitors-keyword-gap.md](references/seo-competitors-keyword-gap.md) |
| `plainrows/standvirtual-scraper` | Standvirtual Scraper: Portugal Car Listings & Prices | from $0.0004 per listing | [references/standvirtual-scraper.md](references/standvirtual-scraper.md) |
| `plainrows/storia-scraper` | Storia Scraper: Romania Property Listings & Prices | from $0.0004 per listing | [references/storia-scraper.md](references/storia-scraper.md) |
| `plainrows/tori-scraper` | Tori.fi Scraper: Finland Marketplace Listings | from $0.0004 per listing | [references/tori-scraper.md](references/tori-scraper.md) |
| `plainrows/tripadvisor-reviews` | Tripadvisor Reviews Scraper API: Hotels & Restaurants | from $0.0002 per review | [references/tripadvisor-reviews.md](references/tripadvisor-reviews.md) |
| `plainrows/trustpilot-reviews` | Trustpilot Reviews Scraper: New Reviews & Replies | from $0.0002 per review | [references/trustpilot-reviews.md](references/trustpilot-reviews.md) |
| `plainrows/vagas-jobs-scraper` | Brazil Jobs Scraper: Vagas.com.br Job Ads | from $0.0009 per job | [references/vagas-jobs-scraper.md](references/vagas-jobs-scraper.md) |
| `plainrows/website-email-extractor` | Website Email Extractor: Emails, Phones & Socials from URLs | from $0.0015 per website with contacts | [references/website-email-extractor.md](references/website-email-extractor.md) |
| `plainrows/website-screenshot` | Website Screenshot API: Full Page, Mobile & Bulk Capture | from $0.0018 per screenshot | [references/website-screenshot.md](references/website-screenshot.md) |
| `plainrows/website-tech-stack` | Website Technology Checker: Tech Stack & CMS Detector | from $0.0006 per website | [references/website-tech-stack.md](references/website-tech-stack.md) |
| `plainrows/workday-jobs-scraper` | Workday Jobs Scraper: Any myworkdayjobs Careers Site | from $0.0008 per job | [references/workday-jobs-scraper.md](references/workday-jobs-scraper.md) |
| `plainrows/yellowpages-au-scraper` | Yellow Pages Australia Scraper: Business Leads & Phones | from $0.0018 per business | [references/yellowpages-au-scraper.md](references/yellowpages-au-scraper.md) |
| `plainrows/youtube-comments-scraper` | YouTube Comments Scraper: Video Comments Export | from $0.0002 per comment | [references/youtube-comments-scraper.md](references/youtube-comments-scraper.md) |
| `plainrows/youtube-search-api` | YouTube Search API: Videos, Views & Channels as JSON | from $0.001 per video | [references/youtube-search-api.md](references/youtube-search-api.md) |
| `plainrows/youtube-search-scraper` | YouTube Search Scraper: Videos, Views & Channels by Keyword | from $0.001 per video | [references/youtube-search-scraper.md](references/youtube-search-scraper.md) |

Other ways to use the same tools: MCP server `https://mcp.apify.com?tools=plainrows/<slug>`, n8n, Make and Zapier (Apify integration).
