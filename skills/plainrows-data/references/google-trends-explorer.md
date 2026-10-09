# Google Trends Scraper API: Interest, Regions & Queries (`plainrows/google-trends-explorer`)

Google Trends data as clean rows: interest over time for up to 5 compared keywords, interest by region, related queries and topics (top and rising). Any country, region or worldwide; web, YouTube, news, images and shopping search. No proxies, no CAPTCHAs. Pay only per search.

Store page and full documentation: https://apify.com/plainrows/google-trends-explorer

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchTerms` (required) | array |  | One Google Trends search per line. Compare up to 5 keywords by separating them with commas, e.g. "chatgpt, gemini, claude"; values are then on the same 0-100 scale, like on trends.google.com. One keyword alone, e.g.... |
| `country` | string (214 codes, see the Store page) | "US" | Where the searches happen, or Worldwide. |
| `timeRange` | string: `past_hour`, `past_4_hours`, `past_day`, `past_7_days`, `past_30_days`, `past_90_days`, `past_12_months`, `past_5_years`, `all_time` | "past_12_months" | Period of the chart. Google picks the spacing of the points: per minute (past hour), per hour (past day, past 7 days), per day (past 30/90 days), per week (12 months, 5 years) or per month (all time). Ignored when a... |
| `searchType` | string: `web`, `youtube`, `news`, `images`, `shopping` | "web" | Which Google search the interest is measured on, like the "Web search" menu of Google Trends. |
| `includeRegions` | boolean | true | Add one row per region and keyword: states or provinces for a country, countries for Worldwide. Included in the price of the search. |
| `includeRelated` | boolean | true | Add Google's related queries and related topics (top and rising). Google Trends gives them only for a search with a single keyword. Included in the price of the search. |
| `startDate` | string |  | Use your own date range instead of Time range, e.g. 2025-01-01. From 2004-01-01 (web) or 2008-01-01 (other search types). |
| `endDate` | string |  | End of the custom range (default: today). |
| `region` | string |  | A region instead of a whole country: Google Trends region code such as "US-CA" (California), "GB-SCT" (Scotland) or "DE-BY" (Bavaria), as shown in the regionCode column. Overrides Country. |
| `category` | integer | 0 | Google Trends category number to narrow an ambiguous keyword: 0 = all categories (default), 71 = Food & Drink, 18 = Shopping, 20 = Sports, 7 = Finance, 5 = Computers & Electronics, 45 = Health, 67 = Travel, 47 = Autos &... |
| `languageCode` | string |  | Two-letter language of topic names, e.g. "fr" for French topic titles (default "en"). It does not filter searches; Country does. |
| `speed` | string: `standard`, `fast` | "standard" | Standard (lowest price): each search waits in the data provider's queue, so allow a few minutes per run; a search still queued after 12 minutes is answered through the fast route at no extra charge. Fast: about 10-30... |

## Example input

```json
{
  "searchTerms": [
    "chatgpt, gemini, claude",
    "coffee"
  ],
  "country": "US",
  "timeRange": "past_12_months"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Google Trends search**: $0.006 / $0.005 / $0.0045 / $0.004. One Google Trends search (1 to 5 keywords compared) with all its rows: interest over time, interest by region, related queries and topics. Searches with no data are free.
- **Fast mode**: $0.01 / $0.01 / $0.01 / $0.01. Extra fee per Google Trends search with data when you choose Speed = Fast (answer in about 10-30 seconds). Not charged in Standard mode.
