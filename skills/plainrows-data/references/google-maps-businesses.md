# Google Maps Scraper: Business Leads, Emails & Phones (`plainrows/google-maps-businesses`)

An Outscraper alternative, no subscription: B2B leads from Google Maps (Google Places) with name, category, address, phone, website, rating, reviews, hours, coordinates, plus optional e-mails and social profiles from each website. Fast API, no browser. Pay per place, plus per website with contacts.

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
| `contactDetails` | boolean | false | Also visit each place's website (homepage, and its contact or legal page when the homepage shows no e-mail) and return the e-mails, phone links and social profiles (Facebook, Instagram, LinkedIn, X, YouTube, TikTok)... |

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
- **Contact details found**: $0.002 / $0.0015 / $0.0012 / $0.001. Optional (contactDetails): e-mails, phone links and social profiles found on the website of one place. Places without a website, sites that cannot be loaded and sites with nothing found are free.
