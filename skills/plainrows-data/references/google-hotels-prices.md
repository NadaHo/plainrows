# Google Hotels Prices Scraper: Price Comparison of Booking Sites (`plainrows/google-hotels-prices`)

Google Hotels prices by city and dates (nightly hotel rates, stars, rating, GPS, link), or every booking site's price for given hotels (Booking.com, Expedia, official site) with a daily price calendar. API-based, no browser or proxies. Pay per hotel.

Store page and full documentation: https://apify.com/plainrows/google-hotels-prices

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `destinations` | array |  | Cities or areas to search, one per line, written as you would in Google Hotels: "Paris, France", "Lisbon, Portugal", "hotels near Times Square". Adding the country avoids ambiguity. Up to 500 per run. Leave empty when... |
| `hotels` | array |  | Optional. Hotel names with their city ("Hyatt Regency Lisbon"), Google hotel IDs (the hotelId column of a search run) or Google Hotels links (google.com/travel/hotels/entity/...), one per line. When filled in, the Actor... |
| `priceCalendarRange` | string: `month`, `three_months`, `six_months`, `year` | "three_months" | Price comparison mode only: how many days of nightly prices to return from the check-in date. Same price whatever the range. |
| `speed` | string: `standard`, `fast` | "standard" | Price comparison mode only. Standard waits in the data provider's queue (about 10-20 seconds per hotel when measured, longer at busy times; a hotel still queued after 12 minutes is answered the fast way at no extra... |
| `checkInDate` | string |  | YYYY-MM-DD. Leave empty for 30 days from today (handy for scheduled price tracking). |
| `nights` | integer | 1 | Length of stay. Check-out = check-in + nights. |
| `adults` | integer | 2 | Guests per room (Google prices change with the number of guests). |
| `currency` | string | "USD" | Three-letter currency code for prices, e.g. USD, EUR, GBP, CHF. |
| `maxHotelsPerDestination` | integer | 20 | Google Hotels returns up to about 140 hotels per search, in pages of about 20. Each hotel returned and each results page are billed; see Pricing. |
| `sortBy` | string: `relevance`, `lowest_price`, `highest_rating`, `most_reviewed` | "relevance" | Order of the results, as in Google Hotels. |
| `country` | string (20 codes, see the Store page) | "US" | Google market the search is made from (Google's country). It changes how prices are shown, e.g. with or without taxes. It does not limit where the hotels are. |
| `languageCode` | string |  | Two-letter language code, e.g. "en" or "fr". Leave empty to use the country's main language (for example German for Switzerland, French for Belgium). |
| `propertyType` | string: `any`, `hotels`, `vacation-rentals` | "any" | Google mixes some vacation rentals into hotel results. Choose "Hotels only" to drop them, or search rentals only. |
| `hotelClass` | array |  | Keep only these star classes. Empty = all. |
| `minRating` | number | 0 | Google's guest-rating filter, e.g. 4 or 4.5 (0 = no filter). |
| `minPrice` | integer |  | In the chosen currency. Empty = no minimum. |
| `maxPrice` | integer |  | In the chosen currency. Empty = no maximum. |
| `freeCancellationOnly` | boolean | false | Google's free-cancellation filter. Rows then have freeCancellation = true. |
| `amenities` | array |  | Keep only hotels that have all of these amenities (Google filter). |

## Example input

```json
{
  "destinations": [
    "Paris, France"
  ],
  "currency": "USD",
  "country": "US"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Hotel**: $0.0012 / $0.001 / $0.0009 / $0.0008. One hotel with its Google Hotels nightly price for your dates, class, rating, reviews count, coordinates, photo and link. Hotels without a price, removed rentals and duplicates are free.
- **Results page**: $0.004 / $0.004 / $0.004 / $0.004. One Google Hotels results page fetched (about 20 hotels), charged before each search at the data provider's cost. A 20-hotel search uses 1 page, 100 hotels use 5.
- **Hotel price check**: $0.02 / $0.017 / $0.015 / $0.013. One hotel checked in price comparison mode: the price of every booking site Google lists for your dates (official site included) and a daily price calendar for the coming months. Charged once per hotel, after the data provider has answered; a hotel Google has no price for is free.
