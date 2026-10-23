# Germany Jobs Scraper: Arbeitsagentur API, Bundesagentur Jobs (`plainrows/arbeitsagentur-jobs-scraper`)

Germany jobs scraper and MCP tool: German jobs from the official Arbeitsagentur Jobbörse API by keyword + place: title, company, address, occupation, full/part-time, remote, salary when given, dates, link. No login. Pay per job ($0.0009 or less) plus a $0.001 start fee per run.

Store page and full documentation: https://apify.com/plainrows/arbeitsagentur-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` | array |  | Job titles, occupations or skills, in German or English ("Data Engineer", "Pflegefachkraft", "Lagerhelfer"). Each keyword is searched in each place below. Leave empty to list all jobs of the places. |
| `locations` | array |  | German towns, postal codes or regions ("Berlin", "80331", "Hamburg"), searched with the radius below. Leave empty to search all of Germany. |
| `radiusKm` | integer | 25 | Distance around each place, as on the Jobbörse (0 = the place only). Used only with places. |
| `offerType` | string: `any`, `job`, `apprenticeship`, `internship`, `self-employment` | "any" | Kind of offer, as the Jobbörse filter Angebotsart. |
| `workingTime` | array |  | Keep only jobs with one of these working times. Leave empty for all. |
| `publishedWithinDays` | integer |  | Only jobs published (or republished) in the last N days, 0 to 100. Leave empty for all. Use 1 for a daily feed of new jobs. |
| `maxJobsPerSearch` | integer | 100 | The API returns 100 jobs per page and at most 10,000 jobs per search; the Actor reads the pages one after the other. |
| `searchUrls` | array |  | Search pages copied from the Jobbörse, e.g. https://www.arbeitsagentur.de/jobsuche/suche?angebotsart=1&was=Koch&wo=Hamburg&umkreis=25. Their filters (was, wo, umkreis, angebotsart, arbeitszeit, veroeffentlichtseit,... |

## Example input

```json
{
  "keywords": [
    "Data Engineer"
  ],
  "locations": [
    "Berlin"
  ],
  "maxJobsPerSearch": 150
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0009 / $0.0008 / $0.0007 / $0.0006. One job ad from the Arbeitsagentur Jobbörse returned with reference number, title, company and link (plus address, occupation, working time, remote, salary and dates when given). Searches without jobs, refused or unreadable answers, ads without a company or reference, jobs already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
