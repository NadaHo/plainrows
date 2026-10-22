# Catho Jobs Scraper: Brazil Job Ads from catho.com.br (`plainrows/catho-jobs-scraper`)

Catho scraper and MCP tool for Brazil jobs: paste catho.com.br search URLs or keywords + city, get each job: title, company, city, openings, salary in BRL, benefits, date, link. No login. Pay per job ($0.0012 or less) + $0.001 start fee.

Store page and full documentation: https://apify.com/plainrows/catho-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Job search pages copied from www.catho.com.br, e.g. https://www.catho.com.br/vagas/vendedor/ or https://www.catho.com.br/vagas/analista-de-dados/sao-paulo-sp/ (filters in the URL are kept). The page number is ignored:... |
| `keywords` | array |  | Job titles or skills, best in Portuguese ("vendedor", "analista de dados", "enfermeiro"). Each keyword is searched in each city below. |
| `locations` | array |  | City and state code ("São Paulo, SP", "Curitiba, PR", "belo-horizonte-mg"), used with the keywords above. Leave empty to search all of Brazil. |
| `maxResultsPerSearch` | integer | 60 | Catho shows 20 jobs per page; the Actor reads up to 50 pages (1,000 jobs) per search, one after the other. |

## Example input

```json
{
  "searchUrls": [
    "https://www.catho.com.br/vagas/vendedor/"
  ],
  "keywords": [
    "analista de dados"
  ],
  "locations": [
    "São Paulo, SP"
  ],
  "maxResultsPerSearch": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0012 / $0.0011 / $0.001 / $0.0009. One Catho job returned with title, company (null when Catho hides it), city and link, plus openings, salary, benefits and date. Searches without jobs, blocked or unreadable pages, jobs without company or city, jobs already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
