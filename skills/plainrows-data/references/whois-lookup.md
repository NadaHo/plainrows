# WHOIS Lookup: Bulk Domain Age, Expiry & Availability Checker (`plainrows/whois-lookup`)

WHOIS lookup and MCP tool for any list of domains: registrar, creation and expiry dates, domain age, days until expiry, status, name servers, DNSSEC, and whether the domain is registered. RDAP first, WHOIS for .de, .io, .co, .it. Pay per domain plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/whois-lookup

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | Domains or URLs, one per line: "apify.com", "https://blog.example.co.uk/page". Subdomains, "www." and paths are reduced to the registered domain (example.co.uk). Up to 10,000 per run; duplicates are removed. |

## Example input

```json
{
  "domains": [
    "apify.com",
    "wikipedia.org",
    "bbc.co.uk",
    "spiegel.de",
    "example-domain-not-registered-123.com"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Domain**: $0.002 / $0.0018 / $0.0015 / $0.0012. One domain the registry answered for: registered (registrar, dates, status, name servers) or not registered. Domains without an answer (rate limit, timeout, extension without a public service) are free.
- **Actor Start**: $0.0005 / $0.0005 / $0.0005 / $0.0005. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
