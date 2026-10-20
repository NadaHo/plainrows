# Reed.co.uk Jobs Scraper: UK Job Ads & Salaries (`plainrows/reed-jobs-scraper`)

Paste reed.co.uk search URLs or keywords + a UK city, get each job ad: title, employer, location, salary (min/max/period), contract type, remote/hybrid, posting date, snippet, link. No login. Pay per job ($0.0008 or less) plus a $0.002 start fee per run.

Store page and full documentation: https://apify.com/plainrows/reed-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Job search pages copied from reed.co.uk, e.g. https://www.reed.co.uk/jobs/nurse-jobs-in-manchester (filters in the URL such as ?perm=true are kept). The page number is ignored: the Actor reads the pages itself. URLs... |
| `keywords` | array |  | Job titles or skills ("software developer", "accountant", "warehouse operative"). Each keyword is searched in each location below, or across the UK when no location is given. |
| `locations` | array |  | UK towns, cities or counties ("London", "Milton Keynes", "Kent"), used with the keywords above. Leave empty to search the whole UK. |
| `maxResultsPerSearch` | integer | 50 | Reed shows 25 jobs per page; the Actor reads up to 40 pages (1,000 jobs) per search, one after the other. |

## Example input

```json
{
  "searchUrls": [
    "https://www.reed.co.uk/jobs/nurse-jobs-in-manchester"
  ],
  "keywords": [
    "data analyst"
  ],
  "locations": [
    "London"
  ],
  "maxResultsPerSearch": 50
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One reed.co.uk job ad returned with title, employer, location and link (plus salary, contract type, workplace, dates, snippet when shown). Searches without jobs, blocked or unreadable pages, incomplete ads, jobs already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
