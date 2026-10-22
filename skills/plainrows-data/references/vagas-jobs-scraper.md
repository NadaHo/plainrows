# Vagas.com.br Scraper: Brazil Jobs from Vagas (`plainrows/vagas-jobs-scraper`)

Vagas scraper and MCP tool for Brazil jobs: paste vagas.com.br search URLs or keywords + city, get each job: title, company, level, openings, city, state, remote, excerpt, date, link. No login. Pay per job ($0.0012 or less) + $0.001 start fee.

Store page and full documentation: https://apify.com/plainrows/vagas-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Job search pages copied from www.vagas.com.br, e.g. https://www.vagas.com.br/vagas-de-vendedor or https://www.vagas.com.br/vagas-de-analista-de-dados-em-sao-paulo (filters such as ?ordenar_por=mais_recentes are kept).... |
| `keywords` | array |  | Job titles or skills, best in Portuguese ("vendedor", "analista de dados", "enfermeiro"). Each keyword is searched in each city below. |
| `locations` | array |  | City names ("São Paulo", "Curitiba", "belo-horizonte"; a state code after a comma is ignored), used with the keywords above. Leave empty to search all of Brazil. |
| `maxResultsPerSearch` | integer | 80 | Vagas.com.br shows 40 jobs per page; the Actor reads up to 25 pages (1,000 jobs) per search, one after the other, and skips jobs the site shows again on a later page. |

## Example input

```json
{
  "searchUrls": [
    "https://www.vagas.com.br/vagas-de-vendedor"
  ],
  "keywords": [
    "analista de dados"
  ],
  "locations": [
    "São Paulo"
  ],
  "maxResultsPerSearch": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0012 / $0.0011 / $0.001 / $0.0009. One Vagas.com.br job returned with title, company (null when the site hides it), location and link, plus level, openings, excerpt and date. Searches without jobs, blocked or unreadable pages, jobs repeated on a later page or by another search of the run and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
