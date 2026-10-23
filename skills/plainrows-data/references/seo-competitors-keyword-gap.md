# SEO Competitors & Keyword Gap Finder (`plainrows/seo-competitors-keyword-gap`)

Keyword gap tool and MCP tool: the organic Google competitors of any website and the keywords they rank for that it misses: shared keywords, positions, traffic, volume, CPC, difficulty. 94 countries. Semrush alternative. $0.002 per competitor or keyword, plus a $0.012 fee per domain with results.

Store page and full documentation: https://apify.com/plainrows/seo-competitors-keyword-gap

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | One website per line: example.com, https://www.example.com/page or blog.example.com. Up to 100 per run. URLs are reduced to their domain (subdomains other than www are kept). Duplicates are removed for free. |
| `country` | string (94 codes, see the Store page) | "US" | Country whose Google search data you want. |
| `languageCode` | string |  | Language code, e.g. "en", "fr" or "zh-TW". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). Only languages offered by the data source for that country work; others... |
| `maxCompetitors` | integer | 10 | How many organic competitors to return per domain (sites ranking on the most keywords shared with it), 5 to 100. Each competitor returned is billed; see Pricing. |
| `keywordGap` | boolean | true | Also return the keywords your first competitors rank for in Google's top 100 and the domain does not (best traffic first). Each keyword returned is billed; see Pricing. |
| `gapCompetitors` | integer | 3 | Keyword gap from the first 1 to 5 competitors. Competitors with fewer than 20 keywords outside the shared ones are skipped (nothing paid). A keyword found at several competitors is returned once. |
| `maxGapKeywords` | integer | 100 | Most gap keywords returned per domain, 20 to 1,000, split between the competitors used for the gap. |
| `excludeTopDomains` | boolean | true | Leave out sites that rank for everything (Wikipedia, Amazon, YouTube, Google...) so the list shows real competitors. |

## Example input

```json
{
  "domains": [
    "plausible.io"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Competitor or gap keyword**: $0.002 / $0.002 / $0.0018 / $0.0016. One organic competitor (shared keywords, average position, traffic) or one gap keyword (a keyword a competitor ranks for and your domain does not, with volume, CPC, difficulty and the competitor's URL). Domains without data are never charged.
- **Domain analysed**: $0.012 / $0.012 / $0.012 / $0.012. One domain for which competitors were found, charged once per domain at about what the data source charges us for the lookup. Domains without data are free.
