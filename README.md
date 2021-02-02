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
        ...
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
    

1. #### MARKET ASSETS
   GET `/api/market/assets` [Live link](https://api.pcex.io/api/market/assets)
    > The assets endpoint is to provide a detailed summary of each currency available on the exchange.
    
    Returns JSON response which has active assets data.
    ### Response:
    ```
     {
        "FCC": {
            "can_deposit": "true",
            "can_withdraw": "true",
            "maker_fee": "0.354",
            "max_withdraw": "",
            "min_withdraw": "",
            "name": "",
            "taker_fee": "0.354",
            "unified_cryptoasset_id": "90"
        }
        ...
    }

    ```
    Response has multiple key which denotes market data, this is in JSON. Find all the fields below:
    
    1. `unified_cryptoasset_id`: Unique ID of cryptocurrency assigned by Unified Cryptoasset ID.
    1. `can_withdraw`: Identifies whether withdrawals are enabled or disabled.
    1. `can_deposit`: Identifies whether deposits are enabled or disabled.
    1. `min_withdraw`: Identifies the single minimum withdrawal amount of a cryptocurrency.
    1. `max_withdraw`: Identifies the single maximum withdrawal amount of a cryptocurrency.
    1. `maker_fee`: Fees applied when liquidity is added to the order book. 
    1. `taker_fee`: Fees applied when liquidity is removed from the order book.

1. #### MARKET TICKER
   GET `/api/market/ticker` [Live link](https://api.pcex.io/api/market/ticker)
    > The ticker endpoint is to provide 24-hour pricing and volume summary for each market pair available on the exchange.
    
    Returns JSON response which has active ticker data.
    ### Response:
    ```
      {
        "FCC-USD": {
            "base_id": "0",
            "quote_id": "0",
            "last_price": "2.27",
            "base_volume": "1760.9",
            "quote_volume": "3997",
            "isFrozen": "0"
        }
        ...
    }


    ```
    Response has multiple key which denotes ticker data, this is in JSON. Find all the fields below:
    
    1. `base_id`: The quote pair Unified Cryptoasset ID.
    1. `quote_id`: The base pair Unified Cryptoasset ID.
    1. `last_price`: Last transacted price of base currency based on given quote currency
    1. `base_volume`: 24-hour trading volume denoted in BASE currency
    1. `quote_volume`: 24-hour trading volume denoted in QUOTE currency
    1. `isFrozen`: Indicates if the market is currently enabled (0) or disabled (1).
        

1. #### MARKET DEPTH
   GET `/api/market/orderbook/:market_pair` [Live link](https://api.pcex.io/api/orderbook/:market_pair)
    > The order book endpoint is to provide a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair.
    
    Returns JSON response which has order book of a perticular market
    ### Response:
    ```
    {
    
        "asks":[
                ["8540.0","1.5"],
                ["8541.0","0.0042"]
            ],
        "bids":[
                ["8530.0","0.8814"],
                ["8524.0","1.4"]
            ]
        "timestamp":1559561187,
    }
    ```
    1. `["8540.0","1.5"]` : [ PRICE, VOLUME ]
    1. URL param `market_pair` : Replace this with any market to get the desired order book.
    
1. #### MARKET TRADE HISTORY
   GET `/market/trades/:market_pair` [Live link](https://api.pcex.io/api/market/trades/market_pair)
    > Get data on all recently completed trades for a given market pair.

    
    Returns JSON response which has trade history of a perticular market
    ### Response:
    ```
    [
        {
            "base_volume": "0.231",
            "price": "807531",
            "quote_volume": "186539.661",
            "timestamp": "1601727861539",
            "trade_id": -170358,
            "type": "SELL"
        },
        {
            "base_volume": "0.231",
            "price": "807531",
            "quote_volume": "186539.661",
            "timestamp": "1601727861539",
            "trade_id": -172338,
            "type": "BUY"
        }
        ...
    ]

    ```
    1. URL param `market_pair=BTC_INR` : Replace this with any market to get the desired order book.

    ```
    Response has multiple key which denotes ticker data, this is in JSON. Find all the fields below:
    
    1. `trade_id`: A unique ID associated with the trade for the currency pair transaction (Unix timestamp does not qualify as a trade_id).
    1. `price`: Last transacted price of base currency based on given quote currency
    1. `base_volume`: Transaction amount in BASE currency.
    1. `quote_volume`: Transaction amount in QUOTE currency.
    1. `timestamp`: Unix timestamp in milliseconds for when the transaction occurred.
    1. `type`: Used to determine whether or not the transaction originated as a buy or sell. (Buy – Identifies an ask that was removed from the order book. Sell – Identifies a bid that was removed from the order book.)

    
    
If you have any questions regarding APIs, please reach out to us at http://support.pcexmember.in
