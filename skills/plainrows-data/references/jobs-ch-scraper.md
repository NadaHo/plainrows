# jobs.ch & jobup.ch Jobs Scraper: Swiss Job Ads (`plainrows/jobs-ch-scraper`)

Paste jobs.ch or jobup.ch search URLs, or keywords + a Swiss place, get each job ad: title, company, place, workload (e.g. 80-100%), contract type, position level, publication date, link. No login. Pay per job ($0.0012 or less) plus a $0.001 start fee per run.

Store page and full documentation: https://apify.com/plainrows/jobs-ch-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Job search pages copied from jobs.ch or jobup.ch (any language), e.g. https://www.jobs.ch/en/vacancies/?term=engineer or https://www.jobup.ch/fr/emplois/?term=vendeur&location=Gen%C3%A8ve (filters in the URL are kept).... |
| `keywords` | array |  | Job titles or skills in any language ("data analyst", "Pflegefachperson", "comptable"). Each keyword is searched in each place below, on the site(s) chosen below. |
| `locations` | array |  | Swiss towns, cantons or regions ("Zürich", "Genève", "Bern"), used with the keywords above. Leave empty to search all of Switzerland. |
| `site` | string: `both`, `jobs.ch`, `jobup.ch` | "both" | Where the keywords are searched. Search URLs always use their own site. |
| `maxResultsPerSearch` | integer | 40 | Both sites show 20 jobs per page; the Actor reads up to 50 pages (1,000 jobs) per search, one after the other. |

## Example input

```json
{
  "searchUrls": [
    "https://www.jobs.ch/en/vacancies/?term=engineer"
  ],
  "keywords": [
    "data analyst"
  ],
  "locations": [
    "Zürich"
  ],
  "maxResultsPerSearch": 40
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0012 / $0.0011 / $0.001 / $0.0009. One jobs.ch or jobup.ch job ad returned with title, company, place and link (plus workload, contract type, position level, publication dates when shown). Searches without jobs, blocked or unreadable pages, ads without a company name, jobs already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
