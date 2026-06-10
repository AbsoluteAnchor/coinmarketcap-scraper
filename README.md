[Coinmarketcap Scraper](https://apify.com/muhammetakkurtt/coinmarketcap-scraper?fpr=data)

![CoinMarketCap Scraper](https://images.apifyusercontent.com/fOvI4AYecBkvuKkjNSvSJc_wSIYpFRkGj0rcHdskcOQ/w:1800/cb:1/aHR0cHM6Ly9pLnBvc3RpbWcuY2MvYnJLeTA5ZGsvY29pbm1hcmtldGNhcC1sb2dvLnBuZw.webp)

# CoinMarketCap Scraper

This project is an Apify actor designed to scrape cryptocurrency information from CoinMarketCap. It collects details such as cryptocurrency name, symbol, market cap rank, and more based on the specified start and limit parameters.

## Features

- Fetches cryptocurrency data from CoinMarketCap according to specified start and limit parameters.
- Provides the ability to filter cryptocurrencies by category, algorithm, platform and industry.
- Collects detailed information (metadata, market data, audit information, etc.) for each cryptocurrency.
- Provides price display in different currencies (USD, EUR, ETH, BTC, etc.).
- It can sort according to various criteria (market capitalisation, trading volume, price change, etc.).
- Stores the collected data in the Apify data store.

## Usage

1. Run this actor in the Apify console.
2. Provide the desired inputs:

- **start**: Starting position according to the specified characteristics
- **limit**: How many cryptocurrencies to bring (default: 100)
- **sortBy**: Sort criteria (market_cap, volume_24h, etc.)
- **sortType**: Sort direction (asc or desc)
- **convert**: The currency in which the prices will be displayed (USD, EUR, TRY, etc.)
- **cryptoType**: Cryptocurrency type (all, coins, tokens)
- **category**: Category filter (defi, gaming, privacy, etc.)
- **algorithm**: Consensus algorithm (pos, pow, dpos, etc.)
- **platform**: Blockchain platform (ethereum, binance-smart-chain, solana, etc.)
- **industry**: Industry area (gaming, metaverse, artificial-intelligence, etc.)

### Example Input

```
{
  "start": 1,
  "limit": 100,
  "sortBy": "market_cap",
  "sortType": "desc",
  "convert": "USD",
  "cryptoType": "all",
  "category": "defi",
  "algorithm": "pos",
  "platform": "ethereum",
  "industry": "gaming"
}
```

## Output

The collected data is saved to the Apify dataset. The output data includes the following fields:

- `id`: Unique identifier of the cryptocurrency
- `logoUrl`: Logo URL of the cryptocurrency
- `name`: Name of the cryptocurrency
- `symbol`: Symbol of the cryptocurrency
- `cmcRank`: Market cap rank
- `marketPairCount`: Number of market pairs
- `circulatingSupply`: Circulating supply
- `selfReportedCirculatingSupply`: Self-reported circulating supply
- `totalSupply`: Total supply
- `ath`: All-time high price
- `atl`: All-time low price
- `high24h`: 24-hour high price
- `low24h`: 24-hour low price
- `isActive`: Whether the cryptocurrency is active
- `lastUpdated`: Last updated timestamp
- `dateAdded`: Date added to CoinMarketCap
- `price`: Current price in USD
- `volume24h`: 24-hour trading volume
- `volume7d`: 7-day trading volume
- `volume30d`: 30-day trading volume
- `marketCap`: Market capitalization
- `selfReportedMarketCap`: Self-reported market capitalization
- `percentChange1h`: 1-hour price change percentage
- `percentChange24h`: 24-hour price change percentage
- `percentChange7d`: 7-day price change percentage
- `percentChange30d`: 30-day price change percentage
- `percentChange60d`: 60-day price change percentage
- `percentChange90d`: 90-day price change percentage
- `fullyDilluttedMarketCap`: Fully diluted market capitalization
- `marketCapByTotalSupply`: Market cap by total supply
- `dominance`: Market dominance
- `turnover`: Turnover rate
- `ytdPriceChangePercentage`: Year-to-date price change percentage
- `percentChange1y`: 1-year price change percentage
- `usdQuoteLastUpdated`: Last updated timestamp for USD quote
- `isAudited`: Whether the cryptocurrency is audited
- `auditInfo`: Audit information, including:

- `auditor`: Name of the auditor
- `auditStatus`: Status of the audit
- `score`: Audit score
- `auditTime`: Time of the audit
- `reportUrl`: URL to the audit report

## Example Output

```
{
    "id": 52,
    "logoUrl": "https://s2.coinmarketcap.com/static/img/coins/128x128/52.png",
    "name": "XRP",
    "symbol": "XRP",
    "cmcRank": 7,
    "marketPairCount": 1400,
    "circulatingSupply": 56564039920,
    "selfReportedCirculatingSupply": 0,
    "totalSupply": 99987161962,
    "maxSupply": 100000000000,
    "ath": 3.841939926147461,
    "atl": 0.002802350092679262,
    "high24h": 0.536341616635965,
    "low24h": 0.5268968405994953,
    "isActive": 1,
    "lastUpdated": "2024-10-05T19:41:00.000Z",
    "dateAdded": "2013-08-04T00:00:00.000Z",
    "price": 0.5330829865180338,
    "volume24h": 727310239.4412147,
    "volume7d": 6700700847.023869,
    "volume30d": 26597553702.163055,
    "marketCap": 30153327330.078884,
    "selfReportedMarketCap": 0,
    "percentChange1h": 0.21780229,
    "percentChange24h": -0.60403417,
    "percentChange7d": -14.35731985,
    "percentChange30d": -2.01017541,
    "percentChange60d": 3.26531819,
    "percentChange90d": 24.37414876,
    "fullyDilluttedMarketCap": 53308298651.8,
    "marketCapByTotalSupply": 53301454912.165306,
    "dominance": 1.4039,
    "turnover": 0.0241204,
    "ytdPriceChangePercentage": -15.3947,
    "percentChange1y": 2.22706974,
    "usdQuoteLastUpdated": "2024-10-05T19:41:00.000Z",
    "isAudited": true,
    "auditInfo": [
      {
        "auditor": "CertiK",
        "auditStatus": 2,
        "score": null,
        "auditTime": "2023-08-15T21:12:27.861Z",
        "reportUrl": "https://cmc.certik-skynet.com/redirect?project=xrp-ledger"
      }
    ]
  }
```

This example output shows the structured data of a single cryptocurrency. The actual output will be a list of similar objects for all processed cryptocurrencies.

## Notes

- The collected data is stored in Apify’s default data store.