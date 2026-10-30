# Bulk Backlink Checker & API: Referring Domains & Anchor Text (`plainrows/backlink-checker`)

SEO backlink checker, backlinks API & MCP tool, Ahrefs backlinks alternative. Check backlinks of domains/URLs: backlink profile, one row per backlink (anchor, dofollow, spam score) or referring domain for backlink analysis, backlink audit, competitor backlink gap. $0.035/target, $1.20+/1,000 rows.

Store page and full documentation: https://apify.com/plainrows/backlink-checker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `targets` (required) | array |  | One per line. A domain ("example.com", also covers its subdomains) or a subdomain gives the backlinks of the whole site; a full URL with a path ("https://example.com/blog/post") gives the backlinks of that page only. Up... |
| `mode` | string: `backlinks`, `referringDomains`, `anchors`, `summary` | "backlinks" | Backlinks: each linking page with anchor, dofollow, ranks and dates. Referring domains: each domain that links to the target, with its number of backlinks. Anchor texts: each anchor used in links to the target, with how... |
| `maxResultsPerTarget` | integer | 100 | Each row returned is billed; targets with more backlinks are cut at this number (best-ranked first by default). Above 1,000, each extra block of 1,000 rows adds one lookup fee (see Pricing). |
| `sortBy` | string: `rank`, `newest`, `backlinks` | "rank" | Order of the rows, which also decides which rows you get when a target has more than the maximum. Not used in summary mode. |
| `dofollowOnly` | boolean | false | Skip nofollow links. In referring domains mode, only domains with dofollow links are listed and counts cover dofollow links only. |
| `onePerDomain` | boolean | false | Backlinks mode: keep only the best link from each linking domain (handy to scan a large profile). |
| `includeLostLinks` | boolean | false | Also return links that were found before but are gone now (isLost = true). Off: live links only. |
| `includeSubdomains` | boolean | true | For a domain target, also count links pointing to its subdomains (www, blog, shop...). |

## Example input

```json
{
  "targets": [
    "backlinko.com"
  ],
  "maxResultsPerTarget": 100
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Backlink or referring domain**: $0.003 / $0.002 / $0.0016 / $0.0012. One row returned: a backlink (linking page, anchor, dofollow, ranks, spam score, dates), a referring domain (rank, backlink counts, dates) or an anchor text (backlink and domain counts). Targets with no backlink found get a free row.
- **Domain or URL checked**: $0.035 / $0.035 / $0.035 / $0.035. One lookup in the backlink index: charged once per domain or URL checked, plus once per extra block of 1,000 rows when you ask for more than 1,000 rows per target. Not charged when the lookup fails.
