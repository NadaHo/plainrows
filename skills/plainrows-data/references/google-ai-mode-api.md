# Google AI Mode API: AI Mode Answers, Citations & Sources (`plainrows/google-ai-mode-api`)

Google AI Mode scraper and MCP tool: send queries, get Google AI Mode's answer as JSON: markdown text and every cited source (URL, domain, title, snippet). No Google account, no browser. $0.008 per answer, plus $0.001 per run; empty or failed answers are free.

Store page and full documentation: https://apify.com/plainrows/google-ai-mode-api

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | One query per line, as you would type it in Google AI Mode. Up to 200 queries per run, 1 to 500 characters each. Each query is one AI Mode answer. Google search operators (site:, intitle:, inurl:, filetype:...) are not... |
| `country` | string (20 codes, see the Store page) | "US" | Country Google AI Mode answers from (two-letter ISO code). |
| `languageCode` | string |  | Two-letter language code, e.g. "en", "de", "fr". Default: the main language of the country. |

## Example input

```json
{
  "queries": [
    "best standing desk for small spaces",
    "Which CRM do small agencies recommend in 2026?"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Google AI Mode answer**: $0.008 / $0.008 / $0.008 / $0.008. One query that got a non-empty Google AI Mode answer: the answer as Markdown and the sources it cites. Empty answers, refused queries, failures and queries not asked are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
