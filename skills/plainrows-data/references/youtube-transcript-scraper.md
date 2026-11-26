# YouTube Transcript Scraper & API: Video Subtitles to Text (`plainrows/youtube-transcript-scraper`)

YouTube transcript scraper, API and MCP tool: get the transcript of any video or Short as clean text plus timestamped lines, from manual or auto subtitles, in any language, with optional translation. Paste links or IDs. Pay per transcript, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/youtube-transcript-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `videos` (required) | array |  | One per line: a YouTube video link (youtube.com/watch?v=…, youtu.be/…, /shorts/…, /live/…) or an 11-character video ID, e.g. https://www.youtube.com/watch?v=jNQXAC9IVRw or jNQXAC9IVRw. The url and videoId columns of... |
| `language` | string | "en" | Language of the subtitles to read, as a YouTube language code, e.g. "en", "es", "de", "ja", "pt-BR". Use the language spoken in the videos: a video without subtitles in this language returns a free row (nothing... |
| `translateTo` | string |  | Language code to get YouTube's automatic translation of the transcript, e.g. "en" to read a Spanish video in English. Same price. Leave empty for the original. |
| `includeTimestamps` | boolean | true | Adds a "segments" list (start and end time in seconds, text) to each transcript, for captions, chapters or quotes with a time link. Turn off to get the plain text only. |

## Example input

```json
{
  "videos": [
    "https://www.youtube.com/watch?v=jNQXAC9IVRw"
  ],
  "language": "en"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Transcript**: $0.007 / $0.007 / $0.007 / $0.007. One YouTube video transcript returned: full text, word count, language and timestamped lines. Videos without subtitles in the language asked, failures and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
