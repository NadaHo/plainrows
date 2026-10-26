# Google Reviews Scraper & API: Ratings, Text & Owner Replies (`plainrows/google-reviews-scraper`)

Google reviews scraper, API and MCP tool for any business: stars, text, date, translation, photos, owner reply and the business's rating. Paste Google Maps links, place IDs, CIDs or "business name, city". No reviewer names. Only-new-reviews mode. Pay per review plus small fetch and start fees.

Store page and full documentation: https://apify.com/plainrows/google-reviews-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `places` (required) | array |  | One per line: a Google Maps link to the place, a place ID ("ChIJ…"), a CID ("4280570365733019477", the number in maps.google.com/?cid=…) or "business name, city". The placeId, cid and googleMapsUrl columns of PlainRows... |
| `maxReviewsPerPlace` | integer | 100 | Up to 500. Reviews are fetched in blocks of 10: each block requested and each review returned is billed; see Pricing. |
| `sortBy` | string: `newest`, `most_relevant`, `highest_rating`, `lowest_rating` | "newest" | Newest first suits monitoring. Lowest rating first finds complaints fast. |
| `country` | string (20 codes, see the Store page) | "US" | Google country used for the lookup (and for finding a place by name). Reviews are not limited to this country: the place's reviews are the same everywhere. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "de". Google shows reviews in other languages translated into this one (the original text is kept in originalText). Leave empty to use the country's main language. |
| `onlyNewReviews` | boolean | false | Return only reviews this tool has never delivered to you for the same place, country and language. The first run returns the reviews and remembers them; later runs (for example a daily schedule) return and bill only new... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered reviews (default "plainrows-maps-reviews-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to start... |

## Example input

```json
{
  "places": [
    "The Plaza Hotel, New York"
  ],
  "maxReviewsPerPlace": 100,
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Review**: $0.0003 / $0.00027 / $0.00024 / $0.0002. One Google review returned with its stars, text, date, translation, photos and owner reply. Places with no review, duplicates and input mistakes are free.
- **Block of 10 reviews requested**: $0.0011 / $0.0011 / $0.0011 / $0.0011. Google reviews are fetched in blocks of 10 per place (100 reviews = 10 blocks). Charged for each block requested once Google has answered, even when the place has fewer reviews than requested or is not found, at about what the data source charges us. Not charged when Google does not answer.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
