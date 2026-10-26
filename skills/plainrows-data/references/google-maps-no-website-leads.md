# Google Maps No Website Leads: Businesses Without Website (`plainrows/google-maps-no-website-leads`)

Businesses without website on Google Maps: no website leads scraper and MCP tool. Name, phone, address, rating, reviews count, category and opening hours of local businesses with no website, web design leads for agencies. Any city or country. Pay per business found plus a small start fee.

Store page and full documentation: https://apify.com/plainrows/google-maps-no-website-leads

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchQueries` (required) | array |  | What you would type in Google Maps, one per line: "plumber in Austin", "coffee shop Berlin Mitte", "dentist 75011 Paris". Put the city or area in the query, or use Coordinates below. Up to 1,000 queries per run. Free... |
| `country` | string (20 codes, see the Store page) | "US" | Country used for the Google Maps search (ignored when Coordinates are set, except for the default language). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxPlacesPerQuery` | integer | 100 | Google Maps returns up to about 700 places per search. Each place returned is billed (about $0.0015 on the Starter plan); places removed by filters are free. Free Apify plan: at most 20 places per query. |
| `coordinates` | string |  | Center the search on "latitude,longitude", e.g. "40.7128,-74.0060". Useful to search a neighbourhood or a place without a city name in the query. |
| `zoom` | integer | 13 | Map zoom level around the coordinates: 11 = whole city, 13 = district, 15 = a few streets. |
| `minRating` | number | 0 | Keep only places rated at least this (0 = no filter). Filtered places are not billed. |
| `website` | string: `any`, `with`, `without`, `noOwnSite` | "without" | Filter on whether the business lists a website. Default: only businesses with no website (web design leads). "noOwnSite" also keeps businesses whose only link is a Facebook, Instagram, Yelp or delivery page (more leads... |
| `requirePhone` | boolean | false | Skip places that list no phone number. Filtered places are not billed. |

## Example input

```json
{
  "searchQueries": [
    "hair salon in Odessa, TX"
  ],
  "country": "US",
  "maxPlacesPerQuery": 20,
  "website": "without"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Place**: $0.002 / $0.0015 / $0.0012 / $0.001. One Google Maps business returned with its details (address, phone, website, rating, hours, coordinates). Queries with no result and places removed by your filters are free.
- **Contact details found**: $0.002 / $0.0015 / $0.0012 / $0.001. Optional (contactDetails): e-mails, phone links and social profiles found on the website of one place. Places without a website, sites that cannot be loaded, sites with nothing found and sites that object to solicitation are free.
- **Actor Start**: $0.003 / $0.003 / $0.003 / $0.003. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
