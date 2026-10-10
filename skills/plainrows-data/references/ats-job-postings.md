# ATS Jobs Scraper: Greenhouse, Lever, Ashby & SmartRecruiters (`plainrows/ats-job-postings`)

Get every open job posting from company career pages on Greenhouse, Lever, Ashby, Recruitee, Workable and SmartRecruiters: title, team, location, remote, salary when published, apply link, clean description. Only-new-jobs mode for daily feeds. Official job-board APIs, pay per job.

Store page and full documentation: https://apify.com/plainrows/ats-job-postings

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `companies` (required) | array |  | One company per line. Paste the job board URL (https://boards.greenhouse.io/airbnb, https://jobs.lever.co/spotify, https://jobs.ashbyhq.com/ramp, https://acme.recruitee.com, https://apply.workable.com/acme,... |
| `ats` | string: `auto`, `greenhouse`, `lever`, `ashby`, `recruitee`, `workable`, `smartrecruiters` | "auto" | Where to look up plain company names. URLs always use their own ATS. Workable is never auto-detected: paste its URL or pick it here. |
| `maxJobsPerCompany` | integer | 500 | Most recent jobs first. Each job returned is billed; see Pricing. |
| `titleKeywords` | array |  | Keep jobs whose title has one of these words, e.g. "engineer", "product manager". Matches word starts, ignores case and accents. Filtered jobs are free. |
| `excludeTitleKeywords` | array |  | Drop jobs whose title has one of these words, e.g. "intern", "senior". |
| `locations` | array |  | Keep jobs listing one of these places, e.g. "London", "Germany", "US", "Remote". Whole words, ignores case and accents. |
| `departments` | array |  | Keep jobs whose department or team starts with one of these words, e.g. "Engineering", "Sales". |
| `remoteOnly` | boolean | false | Keep jobs marked remote by the company or listing a remote location. |
| `postedWithinDays` | integer | 0 | Keep jobs published in the last N days (0 = any date). |
| `includeDescription` | boolean | true | Full description as clean text. Turn off for smaller datasets. |
| `includeHtml` | boolean | false | Adds descriptionHtml with the original formatting. |
| `onlyNewJobs` | boolean | false | Return only jobs this tool has never delivered to you for the same job board. The first run returns every matching job and remembers them; later runs (for example a daily schedule) return and bill only new jobs. |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered jobs (default "plainrows-jobs-monitor"). Use a different name per monitoring task to keep separate histories, or a new name to start over.... |

## Example input

```json
{
  "companies": [
    "stripe",
    "https://jobs.lever.co/spotify",
    "https://jobs.ashbyhq.com/ramp"
  ],
  "maxJobsPerCompany": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0015 / $0.0012 / $0.001 / $0.0008. One open job returned with its details (title, department, locations, remote flag, employment type, salary when published, dates, apply link, description). Companies not found, boards without jobs and jobs removed by your filters are free.
