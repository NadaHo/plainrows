# YouTube Video Details Scraper & API: Views, Likes, Tags (`plainrows/youtube-video-details-scraper`)

YouTube video details scraper, API and MCP tool: views, likes, comment count, publish date, duration, tags, category, description, channel and subscribers, caption languages for any video or Short. Paste links or IDs. Pay per video found, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/youtube-video-details-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `videos` (required) | array |  | One per line: a YouTube video link (youtube.com/watch?v=…, youtu.be/…, /shorts/…, /live/…) or an 11-character video ID, e.g. https://www.youtube.com/watch?v=jNQXAC9IVRw or jNQXAC9IVRw. The url and videoId columns of... |

## Example input

```json
{
  "videos": [
    "https://www.youtube.com/watch?v=jNQXAC9IVRw"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Video details**: $0.0065 / $0.0065 / $0.0065 / $0.0065. Details of one YouTube video returned: views, likes, comments, publish date, duration, tags, category, description, channel and subscribers. Videos not found, failures and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
