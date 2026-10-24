# YouTube Search API: Videos, Views & Channels as JSON (`plainrows/youtube-search-api`)

YouTube Search API and MCP tool: search results as JSON for any keyword: video title, URL, views, channel, duration, upload date and position. Date, length, Shorts and live filters. No API key, no quota. Pay per video plus a small start fee; only-new-videos mode adds a fee per 20 results checked.

Store page and full documentation: https://apify.com/plainrows/youtube-search-api

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
  "maxResultsPerQuery": 20,
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Video**: $0.002 / $0.0015 / $0.0012 / $0.001. One YouTube video from the search results, with title, URL, views, upload date, duration, channel and badges. Queries with no result, channels, playlists, repeated videos and videos removed by your filters are free.
- **Page checked (only new results)**: $0.0025 / $0.002 / $0.002 / $0.002. Only with onlyNewVideos: one block of 20 YouTube results checked for new results, charged even when nothing new is found (it pays the data source). Normal runs never pay it.
- **Actor Start**: $0.003 / $0.003 / $0.003 / $0.003. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
