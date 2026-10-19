# Contact Details Scraper: Emails, Phones & Social Profiles (`plainrows/contact-details-scraper`)

Contact details and email finder MCP tool for any list of websites: e-mails, phone numbers and social media links (LinkedIn, Facebook, Instagram, X, YouTube, TikTok) from the homepage, contact and Impressum pages. robots.txt respected. Pay per website where contacts are found, + a small start fee.

Store page and full documentation: https://apify.com/plainrows/contact-details-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `domains` (required) | array |  | One website per line: a domain (acme.com) or any URL of the site (https://www.acme.com/about). The homepage is read, then up to two contact, imprint or legal pages when it shows no e-mail. Up to 10,000 websites per run;... |
| `onlyWithEmail` | boolean | false | Return and bill only websites where at least one e-mail was found. Websites with only phone numbers or social profiles then come back as free rows (status NO_EMAIL). |

## Example input

```json
{
  "domains": [
    "russanddaughters.com",
    "levainbakery.com",
    "bigsurbakery.com",
    "voodoodoughnut.com"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Website with contacts**: $0.003 / $0.0025 / $0.002 / $0.0015. One website where e-mails, phone links or social profiles were found, with all of them (with "Only websites with an e-mail": only websites with an e-mail). Websites with nothing found, unreachable sites, sites that object to solicitation, duplicates and input mistakes are free.
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
