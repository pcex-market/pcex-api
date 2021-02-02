# PCEX Member Public Rest API
Here’s our public API handed to you on a silver platter. You can use it to build tickers, price comparison apps, or anything that helps the crypto community. Use it responsibly. ❤️


## General Information
1. Base API Endpoint: https://api.pcex.io
1. All public api will return either JSON or Array object.

### Public API Endpoints

1. #### MARKET ALL TRACKER
   GET `/api/market/allTracker`  [Live link](https://api.pcex.io/api/market/allTracker)

    > "Market All TRACKER" will provide you an overview of markets trackers. This is helpful when you want to track the configuration of our markets, track fees and more. This response is not recommended for price polling because accurate realtime price is not guaranteed as there could be some delays. We recommend using price ticker API for all price tracking activity.
    
    Response object will have 3 keys `code`(response status) `data` (market pair wise data) and `msg`(success or failed). 
    ### Response:
    ```
     {
        "code": "200",
        "data":
        {
            "BCH-C2USD":
            {
                "trading_pairs": "BCH-C2USD",
                "last_price": 219.56,
                "lowest_ask": 219.5,
                "highest_bid": 219.28,
                "base_volume": 63,
                "quote_volume": 13832.28,
                "price_change_percent_24h": -0.22,
                "highest_price_24h": 220.53,
                "lowest_price_24h": 219.56
            },
            "ETH-INR": 
        {
                "trading_pairs": "ETH-INR",
                "last_price": 26556,
                "lowest_ask": 26556,
            "highest_bid": 26519,
                "base_volume": 820,
                "quote_volume": 21775920,
                "price_change_percent_24h": 2.14,
                "highest_price_24h": 26691,
                "lowest_price_24h": 26000
        },
        "msg": "success"
    }

    ```
    
    
    1. **`allTracker` Summary response descriptions:** 
   
        1. `trading_pairs`: Identifier of a ticker with a delimiter to separate base/quote, eg. 
        1. `base_currency`: Symbol/currency code of base currency, eg. BTC
        1. `quote_currency`: Symbol/currency code of quote currency, eg. USD
        1. `last_price`: Last transacted price of base currency based on given quote currency
        1. `lowest_ask`: Lowest Ask price of base currency based on given quote currency
        1. `highest_bid`: The highest bid price of base currency based on given quote currency
        1. `base_volume`: The 24-hr volume of market pair denoted in BASE currency
        1. `quote_volume`: The 24-hr volume of market pair denoted in QUOTE currency
        1. `price_change_percent_24h`: 24-hr % price change of market pair
        1. `highest_price_24h`: The highest price of base currency based on given quote currency in the last 24-hrs
        1. `lowest_price_24h`: The lowest price of base currency based on given quote currency in the last 24-hrs
