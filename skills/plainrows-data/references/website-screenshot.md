# Website Screenshot API: Full Page, Mobile & Bulk Capture (`plainrows/website-screenshot`)

Take website screenshots in bulk: full page or viewport, desktop, tablet or mobile size, PNG, JPEG, WebP or PDF, dark mode, cookie banners hidden. Get a public image link, HTTP status and page title for each URL. Pay only per successful screenshot.

Store page and full documentation: https://apify.com/plainrows/website-screenshot

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `urls` (required) | array |  | Web pages to capture, one per line. "example.com" is read as "https://example.com". Up to 5,000 URLs per run; duplicates are removed. |
| `device` | string: `desktop`, `laptop`, `tablet`, `mobile`, `custom` | "desktop" | Screen size used to render the page. Tablet and mobile use a mobile browser user agent and touch, so sites serve their mobile layout. |
| `fullPage` | boolean | false | Capture the whole scrollable page instead of only the visible screen. The page is scrolled first so lazy-loaded images appear. |
| `format` | string: `png`, `jpeg`, `webp` | "png" | PNG is pixel-perfect; JPEG and WebP files are several times smaller. |
| `quality` | integer | 80 | Compression quality for JPEG and WebP (ignored for PNG). |
| `blockCookieBanners` | boolean | true | Hide consent pop-ups of the common consent platforms (OneTrust, Cookiebot, Didomi, Quantcast, Usercentrics, TrustArc and others). Banners are hidden, not accepted. |
| `blockAds` | boolean | true | Block requests to the main ad and analytics networks: faster pages, cleaner screenshots. Ad slots may show as empty boxes. |
| `darkMode` | boolean | false | Render with prefers-color-scheme: dark, for sites that offer a dark theme. |
| `delayMs` | integer | 500 | Additional wait after the page has loaded (fonts and visible images are already awaited), for animations, sliders and late content. |
| `waitUntil` | string: `load`, `networkidle`, `domcontentloaded` | "load" | When the page counts as loaded. The page load event is awaited at most 10 s and network idle at most 15 s; after that the screenshot is taken anyway and waitTimedOut is true. |
| `waitForSelector` | string |  | Optional. Wait until this element is visible, e.g. "#main" or ".product-grid". If it never appears, the URL fails and is not charged. |
| `hideSelectors` | array |  | Optional. Elements to hide before the capture: chat widgets, ads, popups, e.g. "#intercom-container", ".newsletter-popup". |
| `timeoutSecs` | integer | 30 | Maximum time to load a page. Slow or unreachable pages fail (free) after this. |
| `width` | integer | 1440 | Viewport width when Device is "Custom size". |
| `height` | integer | 900 | Viewport height when Device is "Custom size". |
| `isMobile` | boolean | false | With "Custom size": use a mobile user agent and touch. |
| `deviceScaleFactor` | integer | 1 | 1 = standard, 2 = retina, 3 = high-end phones. 2 doubles width and height of the image (4 times the pixels) for sharp retina screenshots. |
| `maxHeight` | integer | 10000 | Longer pages are cut at this height (truncated is true). Images are also capped at 25 megapixels, so retina full-page captures are cut earlier. |
| `scrollToBottom` | boolean | true | Scroll through the page before a full-page capture so lazy-loaded images and sections render. |
| `savePdf` | boolean | false | Also save an A4 PDF of each page (screen styles, backgrounds included), linked in pdfUrl. Included in the price. |
| `ignoreHttpsErrors` | boolean | false | Capture sites with expired or self-signed certificates (staging servers). |

## Example input

```json
{
  "urls": [
    "https://example.com",
    "https://www.wikipedia.org"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Screenshot**: $0.003 / $0.0025 / $0.002 / $0.0018. One page captured and saved (viewport or full page, image plus PDF if requested), with HTTP status, title and final URL. Failed URLs, HTTP error pages, blank pages and invalid URLs are free.
