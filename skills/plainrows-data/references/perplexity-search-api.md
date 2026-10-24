# Perplexity Scraper & Perplexity Search API: Answers, Citations (`plainrows/perplexity-search-api`)

Perplexity Search API and MCP tool: ask Perplexity Sonar (live web search) your questions, get each answer as JSON with citations, cited domains and an optional brand and domain check. A Perplexity scraper alternative. Pay per answer, plus a small start fee.

Store page and full documentation: https://apify.com/plainrows/perplexity-search-api

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | One question per line, as you would type it in Perplexity. Up to 200 questions per run, 1 to 500 characters each. Each question is one Perplexity Sonar answer with web search. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose web results Perplexity searches (two-letter ISO code). |
| `maxOutputTokens` | integer | 800 | Upper bound on the length of each answer, in tokens (about 0.75 words each). 800 fits a detailed answer; the price per answer does not change. |
| `brand` | string |  | Your brand, e.g. "Asana". Adds brandMentioned: the name appears as a whole word in the answer (case-insensitive). |
| `domain` | string |  | Your website, e.g. "asana.com". Adds domainCited and domainCitationRank (position among the cited domains, 1 = first). Subdomains count; "https://", "www." and paths are ignored. |

## Example input

```json
{
  "queries": [
    "What is the best CRM for small businesses?",
    "Which project management tools do agencies recommend?"
  ],
  "country": "US",
  "maxOutputTokens": 800
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Answer returned**: $0.015 / $0.013 / $0.012 / $0.012. One question that got a non-empty Perplexity Sonar answer: the answer, its citations, cited domains and the brand and domain checks. Empty answers, refused questions, failures and questions not asked are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
