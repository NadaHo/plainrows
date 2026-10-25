# AI Overview Scraper & Tracker API: Google AI Overview Citations (`plainrows/ai-overview-tracker`)

AI Overview tracker, AI Overview API and MCP tool: for each keyword, see if Google shows an AI Overview, if it cites your domain (rank, URL), which sites it cites, and your organic rank. Pay per keyword, plus a fee per AI Overview found.

Store page and full documentation: https://apify.com/plainrows/ai-overview-tracker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domain` (required) | string |  | The website to look for in the AI Overview citations and in the organic results, e.g. "hubspot.com". Subdomains count (blog.hubspot.com); a path or "www." is ignored. |
| `keywords` (required) | array |  | One Google search per line. Up to 1,000 keywords per run, max 200 characters each. Each keyword is one Google results page (plus more pages if you raise the depth). |
| `brandNames` | array |  | Your brand and its variants, e.g. "HubSpot". Adds brandMentionedInAiOverview: the name appears as a whole word in the AI Overview text. Up to 10. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google results you want to check (Google's AI Overview is not shown in every country). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `depth` | integer | 10 | How deep to look for your domain in the organic results: 10 = first page. Rounded up to a multiple of 10; each extra 10 results is one more Google page, billed as an extra page (see Pricing). |

## Example input

```json
{
  "domain": "hubspot.com",
  "keywords": [
    "what is a crm",
    "best crm for small business",
    "how to write a sales email"
  ],
  "brandNames": [
    "HubSpot"
  ],
  "country": "US",
  "depth": 10
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword checked**: $0.006 / $0.005 / $0.0045 / $0.004. One keyword whose Google results page was read: AI Overview presence, citations of your domain, cited domains and your organic position. Keywords with no results, failures and keywords not checked are free.
- **AI Overview found**: $0.005 / $0.0045 / $0.004 / $0.004. Charged only when Google shows an AI Overview for the keyword (with text or sources). Keywords without an AI Overview, or whose AI Overview did not load, are not charged this event.
- **Extra results page**: $0.004 / $0.004 / $0.004 / $0.004. Only when you raise "Organic results checked" above 10: one per extra page of 10 organic results that Google returned. Not charged at the default depth of 10.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
