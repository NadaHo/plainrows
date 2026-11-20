# Telegram Channel Scraper: Posts, Views & Reactions (`plainrows/telegram-channel-scraper`)

Telegram channel scraper and MCP tool: give public channel names or t.me links, get every post: text, date, views, reactions, photos, video, links, hashtags, forwards, plus channel title and subscribers. Date limit and in-channel search. No login. Pay per post, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/telegram-channel-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `channels` (required) | array |  | One public Telegram channel per line: its name ("durov"), "@durov" or a link ("https://t.me/durov", "https://t.me/s/durov"). Up to 100 channels per run; duplicates are removed. Private groups and invite links (t.me/+…)... |
| `maxPostsPerChannel` | integer | 100 | Newest posts first, 20 per page, older pages one after the other, e.g. 100. |
| `postsNewerThan` | string |  | Optional. Stop at the first post older than this date (UTC), e.g. "2026-11-01". Leave empty for no date limit. |
| `searchQuery` | string |  | Optional. Only posts matching these words, using the channel's own search on t.me, e.g. "update". |

## Example input

```json
{
  "channels": [
    "durov"
  ],
  "maxPostsPerChannel": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Post**: $0.0006 / $0.00055 / $0.0005 / $0.00045. One Telegram channel post returned with its details (text, date, views, reactions, media links, links, hashtags, forward source, channel title and subscribers). Channels without posts, private or unknown names, blocked or unreadable pages and input mistakes are free.
- **Actor Start**: $0.003 / $0.003 / $0.003 / $0.003. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
