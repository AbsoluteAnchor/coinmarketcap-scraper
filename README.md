[Coinmarketcap Scraper](https://apify.com/lulzasaur/coinmarketcap-scraper?fpr=data)

# CoinMarketCap Scraper

Scrape cryptocurrency prices and market data from [CoinMarketCap](https://coinmarketcap.com), the world's largest crypto tracking platform with 8,500+ cryptocurrencies.

## What does CoinMarketCap Scraper do?

This Actor extracts real-time cryptocurrency market data from CoinMarketCap's internal data API. Get current prices, market capitalizations, trading volumes, price changes across multiple time periods, and supply data for thousands of cryptocurrencies.

## Features

- Scrape up to 8,500+ cryptocurrencies in a single run
- Sort by market cap, price, volume, name, or price change
- Filter by crypto type (all, coins only, tokens only)
- Rich data: price, market cap, volume, 1h/24h/7d/30d/60d/90d changes, dominance, YTD change
- Fast HTTP-only scraper (no browser needed)
- Automatic pagination handling

## Output

Each cryptocurrency result includes:

| Field | Description |
| --- | --- |
| `id` | CoinMarketCap internal ID |
| `name` | Cryptocurrency name (e.g., "Bitcoin") |
| `symbol` | Ticker symbol (e.g., "BTC") |
| `slug` | URL slug (e.g., "bitcoin") |
| `cmcRank` | CoinMarketCap ranking |
| `price` | Current price in USD |
| `marketCap` | Market capitalization in USD |
| `volume24h` | 24-hour trading volume in USD |
| `percentChange1h` | Price change in last 1 hour (%) |
| `percentChange24h` | Price change in last 24 hours (%) |
| `percentChange7d` | Price change in last 7 days (%) |
| `percentChange30d` | Price change in last 30 days (%) |
| `percentChange60d` | Price change in last 60 days (%) |
| `percentChange90d` | Price change in last 90 days (%) |
| `fullyDilutedMarketCap` | Fully diluted market cap in USD |
| `circulatingSupply` | Circulating supply |
| `totalSupply` | Total supply |
| `maxSupply` | Maximum supply (null if unlimited) |
| `marketPairCount` | Number of trading pairs |
| `dominance` | Market dominance percentage |
| `turnover` | Volume/market cap ratio |
| `ytdPriceChangePercentage` | Year-to-date price change (%) |
| `percentChange1y` | 1-year price change (%) |
| `dateAdded` | Date first listed on CoinMarketCap |
| `lastUpdated` | Timestamp of last data update |
| `scrapedAt` | Timestamp when data was scraped |

## Example output

```
{
    "id": 1,
    "name": "Bitcoin",
    "symbol": "BTC",
    "slug": "bitcoin",
    "cmcRank": 1,
    "circulatingSupply": 20020787,
    "totalSupply": 20020787,
    "maxSupply": 21000000,
    "marketPairCount": 12615,
    "isActive": true,
    "dateAdded": "2010-07-13T00:00:00.000Z",
    "price": 93249.50,
    "volume24h": 34567890123,
    "marketCap": 1867123456789,
    "percentChange1h": -0.12,
    "percentChange24h": 2.34,
    "percentChange7d": 5.67,
    "percentChange30d": 12.45,
    "percentChange60d": 18.90,
    "percentChange90d": -8.23,
    "fullyDilutedMarketCap": 1958239500000,
    "dominance": 61.23,
    "turnover": 0.0185,
    "ytdPriceChangePercentage": -10.5,
    "percentChange1y": 45.67,
    "lastUpdated": "2026-04-25T12:00:00.000Z",
    "scrapedAt": "2026-04-25T12:01:00.000Z"
}
```

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `sortBy` | select | `market_cap` | Sort field: market_cap, name, price, percent_change_24h, percent_change_7d, volume_24h |
| `sortOrder` | select | `desc` | Sort direction: desc or asc |
| `cryptoType` | select | `all` | Filter: all, coins, or tokens |
| `maxResults` | integer | `500` | Max results (0 = all, max 10,000) |
| `proxyConfiguration` | proxy | none | Optional proxy settings |

## Use cases

- **Portfolio tracking**: Get real-time prices for your crypto holdings
- **Market analysis**: Track market caps, volumes, and dominance shifts
- **Trend detection**: Monitor 1h/24h/7d/30d price changes to spot momentum
- **Research**: Compare supply metrics, FDV, and market pair counts
- **Alerts**: Feed data into monitoring systems for price alerts
- **Data pipelines**: Export to Google Sheets, databases, or BI tools

## Cost of usage

This Actor uses CoinMarketCap's public data API which requires no authentication. Typical usage costs on Apify:

- **500 cryptos**: ~$0.003 (a few seconds)
- **5,000 cryptos**: ~$0.01 (under a minute)
- **All 8,500+**: ~$0.02 (1-2 minutes)

## Tips

- Start with the default 500 results to get top cryptocurrencies by market cap
- Use `cryptoType: "coins"` to filter out tokens and focus on major cryptocurrencies
- Sort by `percent_change_24h` descending to find today's biggest gainers
- The API returns up to 200 results per page; the scraper handles pagination automatically
- No proxy is typically needed, but enable it if you experience rate limiting