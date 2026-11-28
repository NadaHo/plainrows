# Twitch Scraper: Channels, Live Streams, Clips & Videos (`plainrows/twitch-scraper`)

Twitch scraper and MCP tool: channel profiles with followers and live status, top live streams by category and language, top clips and past broadcasts (VODs) of any channel, and top categories by viewers. No login or API key. Pay per result + start fee.

Store page and full documentation: https://apify.com/plainrows/twitch-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `mode` (required) | string: `channels`, `streams`, `clips`, `videos`, `games` | "channels" | channels = one row per channel; streams = live streams sorted by viewers; clips = most viewed clips of each channel; videos = past broadcasts, highlights or uploads of each channel; games = top categories by viewers.... |
| `channels` | array |  | Channel names ("shroud") or channel URLs ("https://www.twitch.tv/pokimane"). Up to 500 per run; duplicates are removed. |
| `categories` | array |  | Category or game names as shown on Twitch ("Just Chatting", "Counter-Strike") or twitch.tv/directory/category URLs. Leave empty for the top live streams of all of Twitch. |
| `language` | string |  | 2-letter language code to keep only streams in that language, e.g. "en", "es", "fr". Empty = all languages. |
| `clipPeriod` | string: `LAST_DAY`, `LAST_WEEK`, `LAST_MONTH`, `ALL_TIME` | "LAST_WEEK" | Most viewed clips created in this period. Example: LAST_WEEK. |
| `videoType` | string: `ARCHIVE`, `HIGHLIGHT`, `UPLOAD` | "ARCHIVE" | ARCHIVE = past broadcasts (VODs). Example: ARCHIVE. |
| `videoSort` | string: `TIME`, `VIEWS` | "TIME" | Example: TIME. |
| `maxResults` | integer | 50 | Streams, clips, videos or categories returned per input, 1 to 100 (Twitch gives one page of up to 100 to an anonymous reader; 30 for the live streams of all of Twitch). Not used for channel profiles. Each result is... |

## Example input

```json
{
  "mode": "channels",
  "channels": [
    "shroud",
    "pokimane"
  ],
  "maxResults": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Result**: $0.001 / $0.0009 / $0.0008 / $0.0007. One Twitch channel, live stream, clip, video or category with its data. Unknown channels, empty lists and refused requests are free rows.
- **Actor Start**: $0.0005 / $0.0005 / $0.0005 / $0.0005. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
