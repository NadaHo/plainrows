# Google Ads Transparency Scraper: Competitor Ads Library (`plainrows/google-ads-transparency`)

Get every Google ad a competitor runs, from a domain, brand name or advertiser ID: creative ID, format, preview image, first and last shown dates, days running, Transparency Center link. Filter by country, platform, format and dates. Fast API, pay only per ad found.

Store page and full documentation: https://apify.com/plainrows/google-ads-transparency

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `targets` (required) | array |  | One per line. A website domain ("nike.com"), an advertiser name as shown in the Google Ads Transparency Center ("Nike, Inc." or "Nike"), an advertiser ID ("AR16735076323512287233") or a Transparency Center advertiser... |
| `maxAdsPerTarget` | integer | 40 | 1 to 120 ads per advertiser or domain, most recently shown first. Each ad returned is billed; see Pricing. |
| `country` | string (21 codes, see the Store page) | "ANY" | Country where the ads were shown. "All regions" matches the Transparency Center default (region: anywhere). |
| `platform` | string: `all`, `google_search`, `youtube`, `google_play`, `google_maps`, `google_shopping` | "all" | Only ads shown on this Google platform. |
| `format` | string: `all`, `text`, `image`, `video` | "all" | Only text, image or video ads. |
| `dateFrom` | string |  | Only ads shown on or after this date (YYYY-MM-DD, earliest 2018-05-31). If you set only one date, the other defaults to the archive start or today. |
| `dateTo` | string |  | Only ads shown on or before this date (YYYY-MM-DD, at most today). |

## Example input

```json
{
  "targets": [
    "nike.com"
  ],
  "country": "ANY"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Ad**: $0.001 / $0.0008 / $0.0007 / $0.0006. One ad creative returned with its details (advertiser, format, preview image, first and last shown dates, days running, Transparency Center link). Advertisers with no ad return a free row.
- **Advertiser search**: $0.003 / $0.003 / $0.003 / $0.003. Charged once per domain, advertiser name or advertiser ID searched in the Google Ads Transparency Center, with or without ads found (covers the lookup, including resolving a name). Invalid inputs and duplicates are free.
