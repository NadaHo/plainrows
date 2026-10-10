# Broken Link Checker: 404s, Redirect Chains & Sitemaps (`plainrows/broken-link-checker`)

Crawl any website and find broken links (404, 500, dead domains), redirect chains and sitemap problems, with the page and anchor text of each bad link. Checks internal, external, image, script and CSS links. Fast HTTP crawler, no browser. Pay only per page crawled.

Store page and full documentation: https://apify.com/plainrows/broken-link-checker

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `startUrls` (required) | array |  | Home page (or any page) of each website to check, e.g. https://example.com. The crawler follows links on the same domain (www. included). You can also add a sitemap URL ending in .xml. Up to 100 URLs per run. |
| `maxPages` | integer | 200 | Stop after crawling this many HTML pages per website. Each page crawled is billed once, with all its links checked; see Pricing. |
| `reportRedirects` | string: `all`, `internal`, `none` | "all" | Links that answer with a redirect (301, 302, ...) still work but slow pages down and waste crawl budget. Choose which ones to list. |
| `checkExternalLinks` | boolean | true | Also check links pointing to other websites (they are checked, never crawled). |
| `checkResources` | boolean | true | Also check <img>, <script> and stylesheet URLs, not only <a> links. |
| `useSitemaps` | boolean | true | Read the sitemaps listed in robots.txt (or /sitemap.xml), crawl their URLs too, and report sitemap URLs that are broken, redirected, noindex or not linked from any page. |
| `reportAllLinks` | boolean | false | One row per link found on each page, including working ones (issueType "ok"). Useful for a full link inventory. Rows are free either way. |
| `excludeUrlPatterns` | array |  | URLs containing any of these texts are neither crawled nor checked, e.g. "/tag/", "?replytocom=", "/wp-admin". Case-insensitive. |
| `respectRobotsTxt` | boolean | true | Do not crawl pages that robots.txt disallows (links to them are still checked). Turn off only for your own site. |
| `maxConcurrency` | integer | 4 | How many requests the crawler sends at once to the website being checked. Keep it low for small servers. Other websites get at most 3. |
| `requestTimeoutSecs` | integer | 15 | A link that does not answer within this time (twice) is reported as "timeout". |

## Example input

```json
{
  "startUrls": [
    {
      "url": "https://the-internet.herokuapp.com/"
    }
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Page**: $0.0015 / $0.001 / $0.0008 / $0.0006. One HTML page of your website crawled, with every link on it checked (internal, external, images, scripts, stylesheets). Result rows, redirects, non-HTML files, broken internal URLs and the run summary are free.
