# Website Email Extractor: Emails, Phones & Socials from URLs (`plainrows/website-email-extractor`)

Paste a list of websites, get the e-mails, phone links and social profiles (Facebook, Instagram, LinkedIn, X, YouTube, TikTok) each one publishes: homepage, then its contact or legal pages. No browser, robots.txt respected. Pay only per website where contacts are found.

Store page and full documentation: https://apify.com/plainrows/website-email-extractor

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | One website per line: a domain (acme.com) or any URL of the site (https://www.acme.com/about). The homepage is read, then up to two contact, imprint or legal pages when it shows no e-mail. Up to 10,000 websites per run;... |

## Example input

```json
{
  "domains": [
    "apify.com",
    "stripe.com"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Website with contacts**: $0.003 / $0.0025 / $0.002 / $0.0015. One website where e-mails, phone links or social profiles were found, with all of them. Websites with nothing found, unreachable sites, sites that object to solicitation, duplicates and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
