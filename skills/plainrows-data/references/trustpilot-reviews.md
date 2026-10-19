# Trustpilot Reviews Scraper: New Reviews & Replies (`plainrows/trustpilot-reviews`)

Trustpilot reviews scraper and unofficial Trustpilot API and MCP tool: reviews of any company with stars, title, text, date, language, verified flag and company reply, plus TrustScore and review count. No reviewer names. Only-new mode for alerts. Pay per review plus small fetch and start fees.

Store page and full documentation: https://apify.com/plainrows/trustpilot-reviews

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `companies` (required) | array |  | One per line: the company's website domain as Trustpilot shows it (www.booking.com) or its Trustpilot page (https://www.trustpilot.com/review/www.booking.com, uk.trustpilot.com, de.trustpilot.com…). Other values are... |
| `maxReviewsPerCompany` | integer | 100 | Up to 200 (the most Trustpilot returns per company). Reviews are fetched in blocks of 20: each block requested and each review returned is billed; see Pricing. |
| `sortBy` | string: `recency`, `relevance` | "recency" | Most recent first suits monitoring. |
| `ratings` | array |  | Keep only reviews with these stars. Applied after Trustpilot answers: the blocks requested are billed either way, only kept reviews are billed. Empty = all. |
| `languages` | array |  | Keep only reviews in these languages, as two-letter codes (en, de, fr…). Applied after Trustpilot answers: the blocks requested are billed either way, only kept reviews are billed. Empty = all. |
| `onlyNewReviews` | boolean | false | Return only reviews this tool has never delivered to you for the same company. The first run returns the reviews and remembers them; later runs (for example a daily schedule) return and bill only new reviews. Each run... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered reviews (default "plainrows-trustpilot-reviews-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to... |

## Example input

```json
{
  "companies": [
    "www.booking.com"
  ],
  "maxReviewsPerCompany": 20,
  "sortBy": "recency"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Review**: $0.0003 / $0.00027 / $0.00024 / $0.0002. One Trustpilot review returned with its stars, title, text, date, language, verified flag and company reply. Duplicates and input mistakes are never charged.
- **Block of 20 reviews requested**: $0.0022 / $0.0022 / $0.0022 / $0.0022. Trustpilot reviews are fetched in blocks of 20 per company (100 reviews = 5 blocks), at high priority so runs finish in about a minute. Charged for each block requested once Trustpilot has answered, even when the company has fewer reviews than requested, none matching your filters, no new review, or is not found: the data source bills them. Not charged when Trustpilot does not answer.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
