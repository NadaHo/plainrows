# Imovirtual Scraper: Portugal Property Listings & Prices (`plainrows/imovirtual-scraper`)

Portugal real estate scraper and MCP tool: paste imovirtual.com search URLs, get every property listing: price, price per m², area, rooms, floor, district, municipality, parish, agency or private owner, date. Flats, houses, land, buy or rent. No login. Pay per listing plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/imovirtual-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searches` (required) | array |  | One imovirtual.com search URL per line, copied from the address bar after choosing the property type, buy or rent (comprar / arrendar), location and filters (price, area, rooms, owner type…). Up to 100 searches per run;... |
| `maxResultsPerSearch` | integer | 108 | Imovirtual shows 36 listings per page; the Actor reads up to 20 pages (720 listings) per search, one after the other. |

## Example input

```json
{
  "searches": [
    "https://www.imovirtual.com/pt/resultados/comprar/apartamento/lisboa",
    "https://www.imovirtual.com/pt/resultados/arrendar/apartamento/porto"
  ],
  "maxResultsPerSearch": 36
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Listing**: $0.00055 / $0.0005 / $0.00045 / $0.0004. One imovirtual.com property listing returned with its details (title, price, price per m², area, rooms, floor, district, municipality, parish, agency or private owner, date). Searches without listings, blocked or unreadable pages, listings already returned by another search of the run and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
