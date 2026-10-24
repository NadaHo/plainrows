# ChatGPT Search Scraper: Answers, Citations & Sources API (`plainrows/chatgpt-search-scraper`)

ChatGPT Search Scraper and MCP tool: send prompts, get ChatGPT's answer with web search as JSON: markdown text, cited sources, search results, fan-out queries, brands and products. No account, no browser. $0.008 per answer, plus $0.001 per run; empty or failed answers are free.

Store page and full documentation: https://apify.com/plainrows/chatgpt-search-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `prompts` (required) | array |  | One prompt per line, as you would type it in ChatGPT. Up to 200 prompts per run, 1 to 500 characters each. Each prompt is one ChatGPT answer with web search. |
| `country` | string (20 codes, see the Store page) | "US" | Country ChatGPT answers and searches the web from (two-letter ISO code). |
| `languageCode` | string |  | Two-letter language code, e.g. "en", "de", "fr". Default: the main language of the country. |
| `includeSearchResults` | boolean | true | Add the web search results ChatGPT read (url, domain, title, description). Off: only their count. The price per answer does not change. |

## Example input

```json
{
  "prompts": [
    "best standing desk for small spaces",
    "Which CRM do small agencies recommend in 2026?"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **ChatGPT answer**: $0.008 / $0.008 / $0.008 / $0.008. One prompt that got a non-empty ChatGPT answer with web search: the answer, its cited sources, search results, fan-out queries, brands and products. Empty answers, refused prompts, failures and prompts not asked are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
