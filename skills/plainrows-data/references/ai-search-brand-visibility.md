# AI Visibility Tracker: ChatGPT Visibility & Google AI Mode (`plainrows/ai-search-brand-visibility`)

AI search & brand visibility tracker for ChatGPT, LLM visibility and GEO MCP tool: ask ChatGPT, Gemini, Perplexity, Google AI Mode customer questions, see if your brand is named, your site cited, which rivals appear. Answers, sources, fan-out queries. Pay per answer + a fee per question answered.

Store page and full documentation: https://apify.com/plainrows/ai-search-brand-visibility

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `prompts` (required) | array |  | Questions your customers would ask an AI assistant, one per line, as they would type them ("best CRM for a small agency", "is Acme reliable?"). Each question is asked once to each engine. Up to 200 per run. |
| `brandNames` | array |  | Your brand name and its variants ("Acme", "Acme CRM"). Matched as whole words, any case. Leave empty to only collect the answers and their sources. |
| `brandDomain` | string |  | Your domain (acme.com): tells whether the answer cites or links your site, and at which position. Subdomains count; a path is ignored. Gemini mostly cites Google pages, so it rarely shows your site as cited. |
| `competitors` | array |  | Competitor names to look for in the answers (up to 10). |
| `competitorDomains` | array |  | Competitor domains to look for in the cited sources (up to 10). |
| `engines` | array | ["chatgpt", "gemini", "google_ai_mode"] | Which engines to ask. Each answer is billed once. Perplexity is optional: add it to also ask Perplexity (Sonar API with web search). |
| `country` | string (20 codes, see the Store page) | "US" | Where the question is asked from. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `includeAnswerText` | boolean | true | Adds the answer as Markdown (answerText). Turn off for lighter rows. |

## Example input

```json
{
  "prompts": [
    "best standing desk for small spaces"
  ],
  "brandNames": [
    "FlexiSpot"
  ],
  "brandDomain": "flexispot.com",
  "competitors": [
    "Uplift",
    "Desky",
    "IKEA"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **AI answer**: $0.02 / $0.015 / $0.012 / $0.01. One answer from one AI engine to one of your questions, analysed for your brand, your site and your competitors. Failed engines and empty answers are not billed.
- **Question answered**: $0.007 / $0.007 / $0.007 / $0.007. Flat fee per question that got at least one AI answer, whatever the number of engines asked (it covers engines that came back empty). Questions with no answer at all are free.
