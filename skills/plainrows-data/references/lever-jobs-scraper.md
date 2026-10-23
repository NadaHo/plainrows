# Lever Jobs Scraper: Any Lever Job Board (`plainrows/lever-jobs-scraper`)

Lever jobs scraper and MCP tool: every open job from any Lever board (jobs.lever.co): title, department, team, locations, country, remote/hybrid/onsite, salary when published, posted date, apply link and description. Paste the board URL or its name. Pay per job plus a small start fee.

Store page and full documentation: https://apify.com/plainrows/lever-jobs-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `companies` (required) | array |  | One company per line. Paste the Lever job board URL (https://jobs.lever.co/spotify, a job link from it, or an EU board https://jobs.eu.lever.co/<name>), just the board name (zoox), or the company website: a board named... |
| `ats` | string: `auto`, `greenhouse`, `lever`, `ashby`, `recruitee`, `workable`, `smartrecruiters`, `workday` | "auto" | Where to look up plain company names. URLs always use their own ATS. Workable is never auto-detected: paste its URL or pick it here. Workday is only reached through careers page URLs (names are refused). |
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
    "https://jobs.lever.co/zoox",
    "https://jobs.lever.co/spotify",
    "palantir"
  ],
  "maxJobsPerCompany": 20
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Job**: $0.0015 / $0.0012 / $0.001 / $0.0008. One open job returned with its details (title, department, team, locations, country, workplace type, employment type, salary range when published, posted date, apply link, description). Companies not found, boards without jobs and jobs removed by your filters are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
