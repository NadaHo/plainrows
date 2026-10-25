# Keyword Rank Checker: Google SERP Position Tracker API (`plainrows/keyword-rank-checker`)

Keyword rank checker, SERP rank tracker and MCP tool: for each keyword, your Google organic position and ranking URL, competitor positions, the top 10 results and SERP features (featured snippet, local pack, People Also Ask). Pay per keyword, plus small fees per run and per extra page.

Store page and full documentation: https://apify.com/plainrows/keyword-rank-checker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domain` (required) | string |  | The website whose Google rankings you want, e.g. "hubspot.com". Subdomains count (blog.hubspot.com); a path or "www." is ignored. |
| `keywords` (required) | array |  | One Google search per line. Up to 1,000 keywords per run, max 200 characters each. Each keyword is one Google results page (plus more pages if you raise the depth). |
| `competitorDomains` | array |  | Up to 10 other domains to track on the same results pages: each row gets their position and ranking URL too (no extra charge). |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google results you want to check. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `depth` | integer | 10 | How deep to look for your domain in the organic results: 10 = first page (the normal case). Rounded up to a multiple of 10; each extra 10 results is one more Google page, billed as an extra page (see Pricing). |

## Example input

```json
{
  "domain": "hubspot.com",
  "keywords": [
    "crm software",
    "best crm for small business",
    "free crm"
  ],
  "competitorDomains": [
    "salesforce.com",
    "zoho.com"
  ],
  "country": "US",
  "depth": 10
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword checked**: $0.006 / $0.005 / $0.0045 / $0.004. One keyword whose Google results page was read: your organic position and ranking URL, competitor positions, top 10 results and SERP features. Keywords with no results, failures and keywords not checked are free.
- **Extra results page**: $0.004 / $0.004 / $0.004 / $0.004. Only when you raise "Organic results checked" above 10: one per extra page of 10 organic results that Google returned. Not charged at the default depth of 10.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
