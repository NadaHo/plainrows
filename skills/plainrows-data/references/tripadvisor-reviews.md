# Tripadvisor Reviews Scraper (`plainrows/tripadvisor-reviews`)

Get Tripadvisor reviews of hotels, restaurants and attractions: stars, title, text, visit date, photos, management response and the place rating. Paste Tripadvisor links. No reviewer names. Only-new-reviews mode for alerts. Pay per review.

Store page and full documentation: https://apify.com/plainrows/tripadvisor-reviews

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `startUrls` (required) | array |  | One per line: the Tripadvisor link of a hotel, restaurant or attraction page (tripadvisor.com, .co.uk, .de, .fr and other Tripadvisor domains). Other links are skipped for free. Up to 500 places per run. |
| `maxReviewsPerPlace` | integer | 100 | Up to 500. Reviews are fetched in blocks of 10: each block requested and each review returned is billed; see Pricing. |
| `sortBy` | string: `most_recent`, `detailed_reviews` | "most_recent" | Most recent first suits monitoring. |
| `ratings` | array |  | Keep only reviews with these ratings. Empty = all. |
| `visitTypes` | array |  | Keep only reviews from these traveler types. Empty = all. |
| `months` | array |  | Keep only reviews of visits in these months (any year). Empty = all. |
| `translateReviews` | boolean | false | Off: each review in the language it was written in. On: Tripadvisor's machine translation (target language chosen by Tripadvisor, not guaranteed). |
| `onlyNewReviews` | boolean | false | Return only reviews this tool has never delivered to you for the same place. The first run returns the reviews and remembers them; later runs (for example a daily schedule) return and bill only new reviews. Each run... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered reviews (default "plainrows-tripadvisor-reviews-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to... |

## Example input

```json
{
  "startUrls": [
    "https://www.tripadvisor.com/Hotel_Review-g60763-d23462501-Reviews-Margaritaville_Times_Square-New_York_City_New_York.html"
  ],
  "maxReviewsPerPlace": 100
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Review**: $0.0003 / $0.0003 / $0.0002 / $0.0002. One Tripadvisor review returned with its stars, title, text, dates, photos and management response. Places with no review, duplicates and input mistakes are free.
- **Block of 10 reviews requested**: $0.0011 / $0.0011 / $0.0011 / $0.0011. Tripadvisor reviews are fetched in blocks of 10 per place (100 reviews = 10 blocks). Charged for each block requested once Tripadvisor has answered, even when the place has fewer reviews than requested, none matching your filters, or is not found, at about what the data source charges us. Not charged when Tripadvisor does not answer.
