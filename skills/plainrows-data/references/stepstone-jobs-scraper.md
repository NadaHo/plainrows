# StepStone Jobs Scraper: Germany Job Offers, Salaries & API (`plainrows/stepstone-jobs-scraper`)

StepStone jobs scraper and MCP tool: give job titles or stepstone.de search URLs, get the job offers (up to 1,000 per search): title, company, location, date posted, salary range (estimated or not), home office, snippet, labels, link. No login. Pay per job offer, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/stepstone-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a job title searched on stepstone.de ("software entwickler", "pflegefachkraft", "data analyst") or a search URL copied from stepstone.de with your filters, e.g.... |
| `location` | string |  | City for the job title searches (not for URLs), e.g. "Berlin" or "München". Empty = all of Germany. |
| `maxResultsPerSearch` | integer | 100 | StepStone shows 25 offers per page; up to 40 pages (1,000 offers) are read per search, e.g. 100. Pages are read one after the other. |

## Example input

```json
{
  "searches": [
    "software entwickler"
  ],
  "location": "Berlin",
  "maxResultsPerSearch": 25
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job offer**: $0.00055 / $0.0005 / $0.00045 / $0.0004. One StepStone job offer returned with its details (title, company, location, date posted, salary range, home office, snippet, labels, link). Searches without offers, blocked or unreadable pages, offers already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.003 / $0.003 / $0.003 / $0.003. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
