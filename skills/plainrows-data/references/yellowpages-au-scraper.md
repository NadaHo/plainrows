# Yellow Pages Australia Scraper: Business Leads & Phones (`plainrows/yellowpages-au-scraper`)

Australia business directory scraper and MCP tool: paste yellowpages.com.au search URLs or a category and a city, get every business: name, phone, website, categories, address, suburb, state, postcode, rating, years in business. No login. Pay per business plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/yellowpages-au-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchUrls` | array |  | Search pages copied from yellowpages.com.au, of the form https://www.yellowpages.com.au/<city-state>/<category> (e.g. /sydney-nsw/plumbers). The page number is ignored: the Actor reads the pages itself. Up to 100... |
| `categories` | array |  | Business categories as on Yellow Pages ("plumbers", "electricians", "dentists", "cafes"). Each category is searched in each location below. |
| `locations` | array |  | A city or suburb with its state, optionally a postcode: "Melbourne VIC", "Parramatta NSW 2150", "Gold Coast QLD". Used with the categories above. |
| `maxResultsPerSearch` | integer | 60 | Yellow Pages shows 30 businesses per page; the Actor reads up to 20 pages (600 businesses) per search, one after the other. |

## Example input

```json
{
  "searchUrls": [
    "https://www.yellowpages.com.au/sydney-nsw/plumbers"
  ],
  "categories": [
    "electricians"
  ],
  "locations": [
    "Melbourne VIC"
  ],
  "maxResultsPerSearch": 60
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Business**: $0.0025 / $0.0022 / $0.002 / $0.0018. One yellowpages.com.au business returned with name, phone and profile link (plus website, categories, address, rating when shown). Searches without businesses, blocked or unreadable pages, businesses without phone, businesses already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
