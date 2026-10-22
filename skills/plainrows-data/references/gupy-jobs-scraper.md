# Gupy Jobs Scraper: Brazil Job Ads from portal.gupy.io (`plainrows/gupy-jobs-scraper`)

Gupy scraper and MCP tool for Brazil jobs: paste portal.gupy.io search URLs or keywords + state, get each job: title, company, city, state, remote/hybrid, contract type, dates, description, link. No login. Pay per job ($0.0012 or less) + $0.001 start fee.

Store page and full documentation: https://apify.com/plainrows/gupy-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Job search pages copied from portal.gupy.io, e.g. https://portal.gupy.io/job-search/term=vendas or https://portal.gupy.io/job-search/term=analista&state=Paran%C3%A1&city=Curitiba (filters in the URL are kept). The page... |
| `keywords` | array |  | Job titles or skills, best in Portuguese ("vendas", "analista de dados", "enfermeiro"). Each keyword is searched in each state below. |
| `states` | array |  | State codes or names ("SP", "Rio de Janeiro", "Parana"), used with the keywords above. Leave empty to search all of Brazil. To search one city, paste a portal URL with the city filter. |
| `workModel` | string: `any`, `remote`, `hybrid`, `on-site` | "any" | Filter of the keyword searches. Search URLs keep their own filters. |
| `maxResultsPerSearch` | integer | 48 | Gupy shows 12 jobs per page; the Actor reads up to 84 pages (1,000 jobs) per search, one after the other. Gupy displays "100" for any large search, but its pages go on beyond 100 jobs. |

## Example input

```json
{
  "searchUrls": [
    "https://portal.gupy.io/job-search/term=vendas"
  ],
  "keywords": [
    "analista de dados"
  ],
  "states": [
    "SP"
  ],
  "maxResultsPerSearch": 24
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0012 / $0.0011 / $0.001 / $0.0009. One Gupy job returned with title, company, link and city/state (or remote), plus contract type, work model, dates and description. Searches without jobs, blocked or unreadable pages, jobs without a company, jobs already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
