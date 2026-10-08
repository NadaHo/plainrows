# YouTube Search Scraper: Videos, Views & Channels by Keyword (`plainrows/youtube-search-scraper`)

Get YouTube search results for any keyword: video title, URL, views, upload date, duration, channel, badges and position. Filters for date, length, Shorts and live. Results in seconds, no browser, no API key. Pay only per video found.

Store page and full documentation: https://apify.com/plainrows/youtube-search-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchQueries` (required) | array |  | What you would type in the YouTube search box, one per line: "how to make sourdough bread", "iphone 17 review", "lofi hip hop". Up to 1,000 queries per run. |
| `maxResultsPerQuery` | integer | 50 | YouTube shows up to about 200 videos per search. Each video returned is billed; see Pricing. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose YouTube results you want (YouTube ranks videos differently per country). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `sortBy` | string: `relevance`, `popularity` | "relevance" | Same as YouTube's "Prioritize" filter. |
| `uploadDate` | string: `any`, `today`, `week`, `month`, `year` | "any" | Only videos uploaded in this period (YouTube's upload date filter). Useful to monitor new videos for a keyword. |
| `duration` | string: `any`, `short`, `medium`, `long` | "any" | YouTube's duration filter. |
| `includeShorts` | boolean | true | Turn off to get regular videos only (uses YouTube's "Videos" type filter). Shorts removed are not billed. |
| `includeLive` | boolean | true | Turn off to skip streams that are live right now. Skipped streams are not billed. |
| `onlyNewVideos` | boolean | false | Return only videos this tool has never delivered to you for the same query, country and language. The first run returns every video and remembers them; later runs (for example a daily schedule) return and bill only new... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered videos (default "plainrows-youtube-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to start over.... |

## Example input

```json
{
  "searchQueries": [
    "how to make sourdough bread"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Video**: $0.002 / $0.0015 / $0.0012 / $0.001. One YouTube video from the search results, with title, URL, views, upload date, duration, channel and badges. Queries with no result, channels, playlists, repeated videos and videos removed by your filters are free.
