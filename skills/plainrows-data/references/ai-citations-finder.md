# AI Citations Finder: LLM Mentions in ChatGPT & AI Overviews (`plainrows/ai-citations-finder`)

AI citations finder and MCP tool: real LLM mentions of your domain or brand in ChatGPT and Google AI Overviews, no prompts needed. One row per AI question: AI search volume, answer excerpt, cited sources, your source position. Fee per target searched plus per question.

Store page and full documentation: https://apify.com/plainrows/ai-citations-finder

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `targets` (required) | array |  | One target per line: a domain ("pipedrive.com"; https://, www. and paths are ignored, subdomains count) or a brand name / keyword ("pipedrive"). Up to 100 per run. Each target is one search in the AI answers database,... |
| `platform` | string: `google`, `chat_gpt` | "google" | Where the questions and answers come from: Google AI Overviews (any country below) or ChatGPT (United States only). |
| `country` | string (20 codes, see the Store page) | "US" | Country of the AI answers. Google AI Overviews: any country of the list. ChatGPT: United States only (another country is refused before anything is searched; only the $0.002 start fee is charged). |
| `languageCode` | string |  | Two-letter language code, e.g. "en". Leave empty to use the country's main language. |
| `maxQuestionsPerTarget` | integer | 100 | Most questions returned per target, 1 to 1,000 (default 100), most searched first. You pay one fee per target searched (0 questions included) plus one fee per question returned (see Pricing). |

## Example input

```json
{
  "targets": [
    "pipedrive.com"
  ],
  "platform": "google",
  "country": "US",
  "maxQuestionsPerTarget": 10
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **AI question**: $0.003 / $0.003 / $0.003 / $0.003. One real question asked to ChatGPT or answered by Google AI Overviews where your target is mentioned or cited: AI search volume, trend, answer excerpt and cited sources.
- **Target searched**: $0.2 / $0.2 / $0.2 / $0.2. Once per domain or brand name searched in the AI answers database, including searches that find 0 questions (the data source bills every search). Failures, refused targets and targets not reached are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
