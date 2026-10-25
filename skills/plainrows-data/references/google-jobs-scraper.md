# Google Jobs Scraper API: Listings, Salaries & Apply Links (`plainrows/google-jobs-scraper`)

Google Jobs API and jobs MCP tool: listings for any job search and city (LinkedIn, Indeed, career sites): title, company, location, salary, job type, posting date, job board and apply link. 20 countries; a SerpApi Google Jobs alternative. Pay per job; only-new-jobs alerts add a small fee per page.

Store page and full documentation: https://apify.com/plainrows/google-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | What you would type in Google Jobs, one per line: a job title, skill or company, with the city if you want one, e.g. "data engineer in Austin, TX", "nurse Manchester", "remote python developer". Up to 1,000 per run. |
| `country` | string (20 codes, see the Store page) | "US" | Google Jobs market: jobs posted for this country, in its main language by default. Put the city in the search itself ("nurse in Austin, TX"). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxJobsPerQuery` | integer | 50 | Google Jobs lists up to about 200 jobs per search. Each job returned is billed; see Pricing. |
| `onlyNewJobs` | boolean | false | Return only jobs this tool has never delivered to you for the same search, country and language. The first run returns every job and remembers them; later runs (for example a daily schedule) return and bill only new... |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered jobs (default "plainrows-google-jobs-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to start... |

## Example input

```json
{
  "queries": [
    "data engineer in Austin, TX"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job listing**: $0.0015 / $0.0012 / $0.001 / $0.0008. One Google Jobs listing returned with its details. Searches with no job, duplicates and input mistakes are free.
- **Page checked (only new results)**: $0.0016 / $0.0016 / $0.0016 / $0.0016. Only with onlyNewJobs: one page of up to 10 Google Jobs results checked for new results, charged even when nothing new is found (it pays the data source). Normal runs never pay it.
- **Results page**: $0.0016 / $0.0016 / $0.0016 / $0.0016. One page of up to 10 Google Jobs results requested from the data source (50 jobs per search = 5 pages), charged only when the search returns at least one job, at about what the data source charges us. Searches with no job are free. Not charged with Only new jobs, which pays page-checked instead.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
