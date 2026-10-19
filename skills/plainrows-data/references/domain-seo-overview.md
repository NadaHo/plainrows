# Competitor Keywords & Organic Traffic: Semrush Alternative (`plainrows/domain-seo-overview`)

Domain overview, SEO competitor analysis, bulk website traffic checker and Semrush MCP tool: organic traffic, keyword counts and 1,000 competitor keywords per site, 94 countries. A Semrush, Ahrefs, SpyFu, Similarweb alternative. Pay per domain and keyword found, + $0.012/run from October 25, 2026.

Store page and full documentation: https://apify.com/plainrows/domain-seo-overview

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | One website per line: example.com, https://www.example.com/page or blog.example.com. Up to 5,000 per run. URLs are reduced to their domain (subdomains other than www are kept). Duplicates are removed for free. |
| `country` | string (94 codes, see the Store page) | "US" | Country whose Google search data you want. |
| `languageCode` | string |  | Language code, e.g. "en", "fr" or "zh-TW". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). Only languages offered by the data source for that country work; others... |
| `topKeywords` | integer | 10 | How many of the keywords bringing the most organic traffic to return per domain (position, URL, volume, CPC, difficulty, intent). 0 = traffic metrics only, otherwise 10 to 1,000. Each keyword returned is billed; see... |
| `keywordType` | string: `organic`, `paid` | "organic" | Organic = the keywords bringing the most Google search traffic to the domain. Paid = the keywords the domain shows Google Ads for (PPC competitor research, a SpyFu-style view), with the ad position, landing page, ad... |
| `minSearchVolume` | integer |  | Only return top keywords searched at least this many times a month. Filtered by the data source: keywords left out are not returned and not billed. 0 = no filter. |
| `maxPosition` | integer |  | Only return top keywords where the domain ranks (or its ad shows) at this position or better, e.g. 10 = first page. Keywords left out are not billed. 100 = no filter. |
| `excludeKeywords` | array |  | Up to 6 words: top keywords containing any of them are left out (not billed), e.g. the brand name to see non-branded keywords only. With any filter set, organicPositions, organicTrafficValueUsd and paidTrafficCostUsd... |

## Example input

```json
{
  "domains": [
    "apify.com"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Domain**: $0.006 / $0.004 / $0.0035 / $0.003. One domain returned with data: estimated organic and paid Google traffic and keyword counts. Domains without data, duplicates and invalid entries are never charged.
- **Top keyword**: $0.003 / $0.002 / $0.002 / $0.0018. One top traffic keyword returned for a domain (position, URL, estimated traffic, volume, CPC, difficulty, intent). Only charged when you ask for top keywords (topKeywords > 0).
