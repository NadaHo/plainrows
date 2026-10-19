# 2dehands Scraper: Belgian Listings & Prices (`plainrows/2dehands-scraper`)

Paste 2dehands.be or 2ememain.be search URLs or keywords, get every listing: title, price, price type, city, date, image, condition, delivery, business seller name. No login, no browser. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/2dehands-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One search per line: a keyword ("fiets", "iphone 15", "velo") or a search URL copied from 2dehands.be (/q/… or a category /l/…) or a 2ememain.be keyword search (/q/…). Filters after # in the address bar are applied by... |
| `maxResultsPerSearch` | integer | 100 | 2dehands shows 30 listings per page; the Actor reads up to 20 pages (600 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "fiets",
    "https://www.2dehands.be/l/fietsen-en-brommers/q/fiets/"
  ],
  "maxResultsPerSearch": 30
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.0008 / $0.0007 / $0.0006 / $0.0005. One 2dehands.be listing returned with its details (title, price, price type, city, date, image, condition, delivery, business seller or not). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
