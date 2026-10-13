# YouTube Comments Scraper: Video Comments Export (`plainrows/youtube-comments-scraper`)

Export YouTube comments of any video: text, likes, reply count, date and the video's title and comment count. Paste video links, Shorts links or IDs. Top and recent comments, up to 700 per video. No author names. Only-new-comments mode for daily checks. Pay per comment.

Store page and full documentation: https://apify.com/plainrows/youtube-comments-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `videos` (required) | array |  | One per line: a YouTube video link (youtube.com/watch?v=…, youtu.be/…, /shorts/…, /live/…) or an 11-character video ID. The url and videoId columns of PlainRows YouTube Search Scraper work as they are. Channel and... |
| `maxCommentsPerVideo` | integer | 100 | 20 to 700. Comments are fetched in blocks of 20 (rounded up: 50 asks for 60): each block requested and each comment returned is billed; see Pricing. |
| `onlyNewComments` | boolean | false | Return only comments this tool has never delivered to you for the same video. The first run returns the comments and remembers them; later runs (for example a daily schedule) return and bill only new comments. Each run... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered comments (default "plainrows-youtube-comments-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to... |

## Example input

```json
{
  "videos": [
    "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
  ],
  "maxCommentsPerVideo": 100
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Comment**: $0.0003 / $0.0003 / $0.0002 / $0.0002. One YouTube comment returned with its text, likes, reply count and date, plus the video's title and comment count. Videos with no comment, duplicates and input mistakes are free.
- **Block of 20 comments requested**: $0.001 / $0.001 / $0.001 / $0.001. YouTube comments are fetched in blocks of 20 per video (100 comments = 5 blocks). Charged for each block requested once YouTube has answered, even when the video has fewer comments than requested or is not found, at about what the data source charges us. Not charged when YouTube does not answer.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
