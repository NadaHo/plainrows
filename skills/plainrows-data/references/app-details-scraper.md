# App Store Scraper & Google Play Scraper: App Details (`plainrows/app-details-scraper`)

App Store scraper, Google Play scraper and MCP tool for app details: paste app URLs or IDs, get one row per app: title, developer, category, rating, rating count, installs, price, version, update date, content rating, icon. No login. Pay per app found plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/app-details-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `apps` (required) | array |  | Google Play app URLs (https://play.google.com/store/apps/details?id=com.spotify.music), App Store app URLs (https://apps.apple.com/us/app/spotify-music-and-podcasts/id324684580), Android package names... |
| `country` | string | "us" | Two-letter store country (us, gb, de, fr, br…). Prices, ratings and availability depend on it. An App Store URL with its own country (/gb/app/…) keeps that country. |
| `language` | string | "en" | Language of the Google Play texts (en, de, fr, pt-BR…). Dates are converted to YYYY-MM-DD for English pages; other languages keep the date as shown. |

## Example input

```json
{
  "apps": [
    "https://play.google.com/store/apps/details?id=com.spotify.music",
    "https://apps.apple.com/us/app/spotify-music-and-podcasts/id324684580"
  ],
  "country": "us",
  "language": "en"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **App**: $0.0015 / $0.0013 / $0.0012 / $0.001. One Google Play or App Store app returned with its ID, title, developer and a rating or rating count (plus category, installs, price, version, dates when the store shows them). Apps not found, blocked or unreadable pages, apps without any rating, duplicates and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
