# Google Maps Scraper: Business Leads, Phones & Ratings (`plainrows/google-maps-businesses`)

Extract businesses from Google Maps searches: name, category, address, phone, website, rating, reviews count, opening hours, coordinates and Place ID. Fast API-based results in seconds, no browser. Pay only per place found.

Store page and full documentation: https://apify.com/plainrows/google-maps-businesses

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchQueries` (required) | array |  | What you would type in Google Maps, one per line: "plumber in Austin", "coffee shop Berlin Mitte", "dentist 75011 Paris". Put the city or area in the query, or use Coordinates below. Up to 1,000 queries per run. |
| `country` | string (20 codes, see the Store page) | "US" | Country used for the Google Maps search (ignored when Coordinates are set, except for the default language). |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxPlacesPerQuery` | integer | 100 | Google Maps returns up to about 700 places per search. Each place returned is billed; see Pricing. |
| `coordinates` | string |  | Center the search on "latitude,longitude", e.g. "40.7128,-74.0060". Useful to search a neighbourhood or a place without a city name in the query. |
| `zoom` | integer | 13 | Map zoom level around the coordinates: 11 = whole city, 13 = district, 15 = a few streets. |
| `minRating` | number | 0 | Keep only places rated at least this (0 = no filter). Filtered places are not billed. |
| `website` | string: `any`, `with`, `without` | "any" | Filter on whether the business lists a website. Filtered places are not billed. |
| `requirePhone` | boolean | false | Skip places that list no phone number. Filtered places are not billed. |

## Example input

```json
{
  "searchQueries": [
    "coffee shop in Austin, TX"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Place**: $0.002 / $0.0015 / $0.0012 / $0.001. One Google Maps business returned with its details (address, phone, website, rating, hours, coordinates). Queries with no result and places removed by your filters are free.
