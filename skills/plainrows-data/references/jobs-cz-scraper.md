# Jobs.cz Scraper: Czech Job Listings & Salaries (`plainrows/jobs-cz-scraper`)

Jobs.cz scraper and MCP tool for Czech jobs: paste jobs.cz search URLs or keywords + a Czech place, get each job ad with title, company, place, salary range in CZK, remote work and link. No login. Pay per job ($0.0012 or less) plus a $0.001 start fee per run.

Store page and full documentation: https://apify.com/plainrows/jobs-cz-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Job search pages copied from jobs.cz, e.g. https://www.jobs.cz/prace/praha/ or https://www.jobs.cz/prace/brno/?q%5B%5D=python (filters in the URL are kept). The page number is ignored: the Actor reads the pages itself.... |
| `keywords` | array |  | Job titles or skills, in Czech or English ("python", "účetní", "data analyst"). Each keyword is searched in each place below. |
| `locations` | array |  | Czech towns or regions ("Praha", "Brno", "Jihomoravský kraj"). With keywords: searched together; alone: all jobs in the place. Leave empty to search the whole Czech Republic. An unknown place returns a free NOT_FOUND... |
| `maxResultsPerSearch` | integer | 30 | jobs.cz shows 30 jobs per page; the Actor reads up to 34 pages (1,000 jobs) per search, one after the other. |

## Example input

```json
{
  "searchUrls": [
    "https://www.jobs.cz/prace/praha/"
  ],
  "maxResultsPerSearch": 30
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0012 / $0.0011 / $0.001 / $0.0009. One jobs.cz job ad returned with title, company and link (plus place, salary range, remote work, posting label when shown). Searches without jobs, blocked or unreadable pages, ads without a company name or link, jobs already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
