# Gemini Search Scraper: Gemini Answers, Citations & Sources (`plainrows/gemini-search-scraper`)

Gemini scraper and MCP tool: send prompts, get Google Gemini's answers as JSON: markdown text, the sources Gemini cites (URL, domain, title), cited domains, model. No account, no browser. $0.008 per answer, plus $0.001 per run; empty or failed answers are free.

Store page and full documentation: https://apify.com/plainrows/gemini-search-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `prompts` (required) | array |  | One prompt per line, as you would type it in Gemini. Up to 200 prompts per run, 1 to 500 characters each. Each prompt is one Gemini answer. |
| `country` | string (20 codes, see the Store page) | "US" | Country Gemini answers from (two-letter ISO code). |
| `languageCode` | string |  | Two-letter language code, e.g. "en", "de", "fr". Default: the main language of the country. |

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

- **Gemini answer**: $0.008 / $0.008 / $0.008 / $0.008. One prompt that got a non-empty Gemini answer: the answer and the sources it cites. Empty answers, refused prompts, failures and prompts not asked are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
