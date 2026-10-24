# Remote Jobs Scraper & API: Himalayas, RemoteOK, Jobicy (`plainrows/remote-jobs-aggregator`)

Remote jobs scraper and MCP tool: remote jobs from the Himalayas, RemoteOK, Jobicy and Arbeitnow public APIs in one table: title, company, salary, location, tags, date, apply link. Same job on 2 sources = 1 row. Pay per job ($0.0009 or less) plus a $0.001 start fee per run.

Store page and full documentation: https://apify.com/plainrows/remote-jobs-aggregator

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` | array |  | Job titles or skills ("python", "product designer", "customer support"). Each keyword is searched on each source. Himalayas and Jobicy search on their side; Remote OK and Arbeitnow give their whole feed, filtered here... |
| `sources` | array | ["himalayas", "remoteok", "jobicy", "arbeitnow"] | Job boards to read. All 4 by default. |
| `location` | string |  | Keep jobs open worldwide or whose allowed countries / location contain this text ("Germany", "United States", "Europe", "UK"). Also sent to the Himalayas search as its country filter. |
| `publishedWithinDays` | integer |  | Only jobs published in the last N days. Leave empty for all. Use 1 for a daily feed of new jobs. |
| `maxResultsPerSource` | integer | 50 | Most jobs read from each source for each keyword. Himalayas search gives at most 20 jobs per keyword (its robots.txt does not allow page 2); Remote OK gives its latest ~100 jobs; Arbeitnow is read up to 3 pages of 300... |

## Example input

```json
{
  "keywords": [
    "python"
  ],
  "maxResultsPerSource": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0009 / $0.0008 / $0.0007 / $0.0006. One remote job from Himalayas, Remote OK, Jobicy or Arbeitnow returned with title, company and link to the job on its source (plus location, salary, tags, date and description when given). The same job found on a second source, jobs without a company, searches without jobs, refused or unreadable answers and input mistakes are free.
- **Actor Start**: $0.001 / $0.001 / $0.001 / $0.001. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
