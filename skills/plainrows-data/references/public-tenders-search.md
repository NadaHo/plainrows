# Public Tenders API & Search: EU TED & UK Procurement API (`plainrows/public-tenders-search`)

Public tenders search and MCP tool: government contracts, notices and award winners from EU TED (Tenders Electronic Daily), UK Find a Tender and Contracts Finder: keywords, CPV, countries, value in EUR, deadlines, winners. Only-new-notices mode. Pay per notice plus a start fee per run.

Store page and full documentation: https://apify.com/plainrows/public-tenders-search

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` | array |  | One search per line, matched in the notice text (title, description, buyer, CPV labels). All words must appear; put a line in double quotes for an exact phrase ("cyber security"). TED also matches translations and words... |
| `noticeTypes` | array | ["contract-notice"] | contract-notice = open calls for tenders (bid opportunities); award = contract awards with winners and values; prior-information = planned procurements and market engagement; other = modifications, direct-award... |
| `countries` | array |  | Two-letter codes of the buyer's country, e.g. FR, DE, IT, ES, PL, NL, GB. Empty = all countries. TED covers EU/EEA buyers (and some neighbours); GB uses the two UK sources. Supported: AT, BE, BG, HR, CY, CZ, DK, EE, FI,... |
| `cpvCodes` | array |  | Common Procurement Vocabulary codes; a code covers its sub-codes (72000000 = all IT services, 79340000 = advertising and marketing). Check digits like "-8" are accepted. A notice matches when any of its CPV codes... |
| `publishedWithinDays` | integer | 7 | Ignored when "Published from" is set. |
| `publishedFrom` | string |  | First publication date (YYYY-MM-DD). UK Find a Tender is searched over the last 31 days of the range at most. |
| `publishedTo` | string |  | Last publication date (YYYY-MM-DD). Default: today. |
| `minValueEur` | integer |  | Keeps notices whose estimated value (or awarded value when there is no estimate) is at least this amount, converted to euros with the ECB reference rates of the day. Notices without a published value are removed when a... |
| `maxValueEur` | integer |  | Upper bound, same rules as the minimum value. |
| `openForBidsOnly` | boolean | false | Keeps contract notices whose submission deadline is in the future. |
| `sources` | array | ["ted", "uk-find-a-tender", "uk-contracts-finder"] | Official platforms to search. Empty = all three. |
| `maxResults` | integer | 100 | Newest first, across all sources. Each notice returned is billed; see Pricing. |
| `includeDescription` | boolean | true | Adds the notice description (up to 2,000 characters, e-mail addresses removed). |
| `onlyNewNotices` | boolean | false | Return only notices this tool has never delivered to you (whatever the keyword). The first run returns the matching notices and remembers them; later runs (for example a daily schedule) return and bill only new notices. |
| `monitorName` | string |  | Name of the key-value store in your Apify account that remembers delivered notices (default "plainrows-tenders-monitor"). Use a different name per alert to keep separate histories, or a new name to start over. Lowercase... |

## Example input

```json
{
  "keywords": [
    "software"
  ],
  "noticeTypes": [
    "contract-notice"
  ],
  "countries": [],
  "publishedWithinDays": 7,
  "maxResults": 50
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Notice**: $0.003 / $0.0025 / $0.002 / $0.0015. One procurement notice returned (contract notice, award, prior information) with buyer, CPV codes, values, deadline, winners and official link. Keywords without results, notices removed by your filters and duplicates found on several platforms are free.
- **Actor Start**: $0.012 / $0.012 / $0.012 / $0.012. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
