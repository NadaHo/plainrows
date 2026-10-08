# Google News Scraper API: Articles, Sources & Dates (`plainrows/google-news-scraper`)

Monitor brands and topics in Google News: title, URL, publisher, snippet, publication time and position for every article, in 20 countries. Time filter, sort by date, only-new-articles mode for scheduled alerts (no duplicates). Pay only per article found.

Store page and full documentation: https://apify.com/plainrows/google-news-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | What you would type in Google News, one per line: a brand, a company, a person in the news, a topic. "Exact phrases", -excluded words and OR work. Operators such as site: or intitle: are not supported (those queries are... |
| `country` | string (20 codes, see the Store page) | "US" | Country edition of Google News (results Google shows to readers in that country). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxArticlesPerQuery` | integer | 50 | Google News returns up to about 200 articles per search. Each article returned is billed; see Pricing. Large values take longer (about 6 seconds per 10 articles). |
| `timeRange` | string: `any`, `hour`, `day`, `week`, `month`, `year` | "any" | Google's time filter. For scheduled monitoring, match it to your schedule ("Past 24 hours" for a daily run) and remove duplicates by URL. |
| `sortBy` | string: `relevance`, `date` | "relevance" | Order of the results. "Most recent first" is best for monitoring. |
| `includeTopStories` | boolean | true | Also return the articles of Google's "Top stories" carousels (they carry the publisher name). Turn off to get only the main news list. |
| `onlyNewArticles` | boolean | false | Return only articles this tool has never delivered to you for the same query, country and language. The first run returns every article and remembers them; later runs (for example a daily schedule) return and bill only... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered articles (default "plainrows-news-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to start over.... |

## Example input

```json
{
  "queries": [
    "Tesla",
    "\"electric vehicles\" Europe"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Article**: $0.002 / $0.0016 / $0.0013 / $0.0009. One Google News article returned with its title, URL, publisher, snippet, publication time and position. Queries with no result, duplicates and input mistakes are free.
