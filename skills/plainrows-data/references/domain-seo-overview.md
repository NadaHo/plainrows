# Website Traffic Checker: Organic Traffic & Keywords (`plainrows/domain-seo-overview`)

Estimated Google organic traffic, ranking keyword counts and up to 1,000 ranking keywords per website for competitor keyword research, in 20 countries. A Semrush and Ahrefs alternative without a subscription, no scraping. You only pay for domains and keywords with data.

Store page and full documentation: https://apify.com/plainrows/domain-seo-overview

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | One website per line: example.com, https://www.example.com/page or blog.example.com. Up to 5,000 per run. URLs are reduced to their domain (subdomains other than www are kept). Duplicates are removed for free. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google search data you want. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). Only languages offered by the data source for that country work;... |
| `topKeywords` | integer | 10 | How many of the keywords bringing the most organic traffic to return per domain (position, URL, volume, CPC, difficulty, intent). 0 = traffic metrics only, otherwise 10 to 1,000. Each keyword returned is billed; see... |

## Example input

```json
{
  "domains": [
    "apify.com",
    "moz.com"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Domain**: $0.006 / $0.004 / $0.0035 / $0.003. One domain returned with data: estimated organic and paid Google traffic and keyword counts. Domains without data, duplicates and invalid entries are never charged.
- **Top keyword**: $0.003 / $0.002 / $0.002 / $0.0018. One top traffic keyword returned for a domain (position, URL, estimated traffic, volume, CPC, difficulty, intent). Only charged when you ask for top keywords (topKeywords > 0).
