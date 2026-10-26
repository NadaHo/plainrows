# PDF to Markdown Converter: PDF to Text API for AI Agents & RAG (`plainrows/pdf-to-markdown`)

PDF to markdown converter and MCP tool for AI agents and RAG: give PDF URLs, get clean Markdown with headings, page texts, title, author and word count. Text-layer PDFs only, no OCR. Pay $0.003 per PDF converted (up to 30 pages), $0.0001 per extra page, plus a small start fee per run.

Store page and full documentation: https://apify.com/plainrows/pdf-to-markdown

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `urls` (required) | array |  | Public addresses of PDF files, one per line (e.g. "https://arxiv.org/pdf/1706.03762"). Up to 5,000 per run; duplicates are removed. Files up to 50 MB; text-layer PDFs only (no OCR). |
| `maxPagesPerPdf` | integer | 30 | Only the first pages up to this number are converted. Up to 30 pages are included in the price of a PDF; each converted page beyond 30 costs $0.0001. |
| `includePageTexts` | boolean | false | Also return the plain text of each page in "pages" (page number + text), next to the full Markdown. It does not change the price. |

## Example input

```json
{
  "urls": [
    "https://arxiv.org/pdf/1706.03762",
    "https://www.irs.gov/pub/irs-pdf/fw9.pdf"
  ]
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **PDF converted**: $0.003 / $0.003 / $0.003 / $0.003. One PDF downloaded and converted to Markdown from its text layer, up to 30 pages included. Scanned PDFs without text, unreadable or password-protected files, files over 50 MB, non-PDFs and URLs that fail (404, timeout) are free.
- **Extra page**: $0.0001 / $0.0001 / $0.0001 / $0.0001. Each converted page beyond the 30 included in a PDF (only when maxPagesPerPdf is above 30 and the PDF is longer).
- **Actor Start**: $0.002 / $0.002 / $0.002 / $0.002. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
