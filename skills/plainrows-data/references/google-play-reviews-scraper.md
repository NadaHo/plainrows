# Google Play Reviews Scraper: Ratings, Text & Replies (`plainrows/google-play-reviews-scraper`)

Scrape Google Play reviews of any Android app: stars, review text, date, app version, thumbs-up count and developer reply, in 20 countries. Paste a package name or Play Store link. No reviewer names. Only-new-reviews mode for daily alerts. Pay per review plus small fetch and start fees.

Store page and full documentation: https://apify.com/plainrows/google-play-reviews-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `apps` (required) | array |  | One per line: a Google Play package name ("com.spotify.music", the id= part of the Play Store link) or the link to the app page. App Store IDs and links work too, in the same list. Up to 500 apps per run. |
| `country` | string (20 codes, see the Store page) | "US" | Store country: reviews written in this country's store (the App Store is separate per country; Google Play filters by country and language). |
| `languageCode` | string |  | Two-letter language code of the reviews, e.g. "en" or "de". Leave empty to use the country's main language. |
| `maxReviewsPerApp` | integer | 100 | Google Play: up to 5,000. App Store: the store gives at most 500 per app and country. Each review returned is billed; see Pricing. |
| `sortBy` | string: `newest`, `most_relevant` | "newest" | Newest first suits monitoring. "Most relevant" uses Google Play's relevance order and the App Store's most helpful order. |
| `onlyNewReviews` | boolean | false | Return only reviews this tool has never delivered to you for the same app, country and language. The first run returns the reviews and remembers them; later runs (for example a daily schedule) return and bill only new... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered reviews (default "plainrows-app-reviews-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to start... |

## Example input

```json
{
  "apps": [
    "com.spotify.music",
    "https://play.google.com/store/apps/details?id=com.duolingo"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Review**: $0.0001 / $0.0001 / $0.0001 / $0.0001. One app review returned with its stars, text, date, version and developer reply. Apps with no review, duplicates and input mistakes are free.
- **Block of reviews requested**: $0.0012 / $0.0012 / $0.0012 / $0.0012. The stores' data is fetched in blocks: up to 150 Google Play reviews or 25 App Store reviews per block, per app and country (100 reviews = 1 block on Google Play, 4 blocks on the App Store). Charged for each block requested once the store has answered, even when the app has fewer reviews than requested or none, at about what the data source charges us. Not charged when the store does not answer.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
