# Company Registry Lookup & API: SIRENE, LEI, Brreg & KYB Data (`plainrows/company-registry-lookup`)

Company registry lookup and MCP tool: find companies in official registers by name, registration number, VAT number or LEI: France SIRENE, Norway Brreg, Finland PRH, Czech ARES and global LEI. Legal form, status, address, industry, employees, LEI. No personal data. Pay only per company found.

Store page and full documentation: https://apify.com/plainrows/company-registry-lookup

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `queries` (required) | array |  | One per line: a registration number (French SIREN or SIRET, Norwegian organisation number, Finnish Business ID, Czech IČO), an EU VAT number of those countries, an LEI, or a company name. Numbers are routed to the right... |
| `country` | string: `auto`, `FR`, `NO`, `FI`, `CZ`, `GLEIF` | "auto" | Where company names are searched (and how numbers are read). National registers list every company of the country; the LEI index covers entities worldwide that have an LEI. A "FR:"-style prefix on a line overrides this. |
| `maxResultsPerQuery` | integer | 3 | For name searches: how many matching companies to return, best match first. A registration number always returns its one company. Each company returned is billed. |
| `activeOnly` | boolean | true | Skip closed, bankrupt or liquidating companies in name searches. Lookups by number always return the company with its status. |
| `addLei` | boolean | true | Find each company's Legal Entity Identifier in the GLEIF index from its registration number. Free; makes runs slightly slower. |

## Example input

```json
{
  "queries": [
    "552032534",
    "923609016",
    "0112038-9",
    "00177041",
    "Danone"
  ],
  "country": "auto"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Company**: $0.0025 / $0.002 / $0.0016 / $0.0012. One company returned with its registry data (name, number, legal form, status, address, industry, LEI). Inputs with no company, invalid numbers and withheld sole proprietorships are free.
