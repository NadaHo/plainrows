# Google Images Scraper API: Image URLs, Sources & Filters (`plainrows/google-images-scraper`)

Get Google Images results as clean data: original image URL, thumbnail, title, source page and domain, position. Filter by size, color, type, file type, date and usage rights, 20 countries. Fast API, no browser. Pay only per image found.

Store page and full documentation: https://apify.com/plainrows/google-images-scraper

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `searchQueries` (required) | array |  | What you would type in Google Images, one per line: "red bicycle", "modern living room", "golden retriever puppy". Up to 1,000 queries per run. |
| `country` | string (20 codes, see the Store page) | "US" | Country whose Google Images results you want. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `maxImagesPerQuery` | integer | 100 | Up to 200 images per query. Each image returned is billed; see Pricing. |
| `imageSize` | string: `any`, `large`, `medium`, `icon` | "any" | Google's image size filter. Filtering is done by Google; results are not checked image by image. |
| `imageColor` | string (15 codes, see the Store page) | "any" | Google's color filter: black and white, transparent background, or a dominant color. Filtering is done by Google; results are not checked image by image. |
| `imageType` | string: `any`, `photo`, `face`, `clipart`, `lineart`, `animated` | "any" | Google's image type filter. Filtering is done by Google; results are not checked image by image. |
| `fileType` | string: `any`, `jpg`, `png`, `gif`, `svg`, `webp` | "any" | Google's file type filter. Filtering is done by Google; results are not checked image by image. |
| `timePeriod` | string: `any`, `pastDay`, `pastWeek`, `pastMonth`, `pastYear` | "any" | Only images Google found recently. Filtering is done by Google; results are not checked image by image. |
| `usageRights` | string: `any`, `creativeCommons`, `commercial` | "any" | Google's usage rights filter (Creative Commons licenses, or commercial and other licenses). Always check the license on the source page before reusing an image. |

## Example input

```json
{
  "searchQueries": [
    "red bicycle"
  ],
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Image**: $0.0012 / $0.001 / $0.0008 / $0.0006. One Google Images result returned: original image URL, thumbnail, title, source page and domain, position. Queries with no result and duplicate images are free.
- **Search with images**: $0.0022 / $0.0022 / $0.0022 / $0.0022. Charged once per search that returns at least one image (the data source charges a whole results page, even for one image). Searches with no image are free.
