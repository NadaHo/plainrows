# Google Autocomplete & People Also Ask Questions Scraper (`plainrows/google-autocomplete-questions`)

Get Google autocomplete suggestions, People Also Ask questions and related searches for any keyword in 20 countries. Question, comparison and A-Z expansions for content ideas, FAQs and SEO. Fast API results, no browser, no proxies. Pay only per result.

Store page and full documentation: https://apify.com/plainrows/google-autocomplete-questions

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `seedKeywords` (required) | array |  | One topic per line, e.g. "running shoes" or "how to learn python". Up to 500 seeds per run, max 120 characters each. |
| `mode` | string: `both`, `autocomplete`, `questions` | "both" | Autocomplete = what Google suggests while typing (with the expansions below). Questions = the "People also ask" box and the "Related searches" at the bottom of the Google results page for each seed. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google suggestions and questions you want. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxResultsPerSeed` | integer | 300 | Stops looking up more expansions for a seed once it has this many results. Each result is billed; see Pricing. |
| `expandQuestions` | boolean | true | Also look up the seed with question words in the search language: "how / what / why / can / is ... running shoes" (12 words in English, about 10 in other languages). Skipped for a seed that is already a question. Each... |
| `expandComparisons` | boolean | false | Also look up "running shoes vs / or / for / with / without / near / like / to ..." (8 to 9 words, localized). |
| `expandAlphabet` | boolean | false | Also look up "running shoes a" to "running shoes z": 26 more lookups per seed for hundreds of long-tail suggestions. |
| `customExpansions` | array |  | Your own patterns, up to 50. Use {seed} to place the seed ("best {seed}", "{seed} for kids"); text without {seed} is added after it. |
| `onlyWithSeedWords` | boolean | true | Drop autocomplete suggestions that do not contain every word of the seed (Google sometimes fills the list with unrelated queries). Dropped suggestions are not billed. Does not apply to People Also Ask questions. |
| `paaClickDepth` | integer | 4 | Google reveals more questions each time a question is opened. 0 = only the first 4 questions or so, 4 = up to about 15. |
| `includeRelatedSearches` | boolean | true | Also return the "Related searches" shown at the bottom of the results page. |

## Example input

```json
{
  "seedKeywords": [
    "running shoes"
  ],
  "mode": "both",
  "country": "US",
  "maxResultsPerSeed": 300
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Suggestion**: $0.0007 / $0.0005 / $0.0004 / $0.0003. One row returned: a Google autocomplete suggestion, a People Also Ask question or a related search. Duplicates, suggestions without your seed words and seeds with no result are not billed.
- **Google lookup**: $0.0035 / $0.0035 / $0.0035 / $0.0035. Charged once per Google lookup sent to the data source: the seed, each expansion ("how ...", "... vs", "... a") and each results page read for questions. The data source bills every lookup, even one that finds nothing new. Not charged when the lookup fails.
