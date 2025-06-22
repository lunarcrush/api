# LunarCrush API v4
Base URL: https://lunarcrush.com/api4

---

### Categories List

https://lunarcrush.com/api4/public/categories/list/v1

Get a list of trending social categories.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/categories/list/v1
```



Example response:

```json
{
  "data": [
    {
      "category": "musicians",
      "title": "Musicians",
      "category_rank": 7,
      "category_rank_1h_previous": 7,
      "category_rank_24h_previous": 6,
      "num_contributors": 143217,
      "social_dominance": 5.508609522018807,
      "num_posts": 257096,
      "interactions_24h": 1853319049
    }
  ]
}
```

Schema:

+ **category**: LunarCrush social category. Can only includes letters, numbers and spaces
+ **title**: The case sensitive title of the topic or category
+ **category_rank**: LunarCrush metric for ranking a social topic relative to all other social topics
+ **category_rank_1h_previous**: The topic rank from 1 hour ago
+ **category_rank_24h_previous**: The topic rank from 24 hours ago
+ **num_contributors**: The number of unique social contributors to the topic
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **num_posts**: Total number of posts with interactions on this topic in the last 24 hours
+ **interactions_24h**: Number of interactions in the last 24 hours




---

### Category Creators

https://lunarcrush.com/api4/public/category/:category/creators/v1

Get the top creators for a social category

input parameters:

+ **category**: _Provide the category to get details for. A category must be all lower case and can only include letters, numbers, and spaces._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/category/musicians/creators/v1
```



Example response:

```json
{
  "data": [
    {
      "creator_id": "youtube::UCVvlTmyH1b4Pyf2LSRUn43w",
      "creator_name": "popupfacts1m",
      "creator_avatar": "https://yt3.ggpht.com/HFqoOSzx6aTYsggcSrI3WY_srDkKV3MDaxz8rT-Tc4bLsxi1Qx8iZ8qWJ4mGeIh5fuJSqwPx0zc=s88-c-k-c0x00ffffff-no-rj",
      "creator_followers": 3850000,
      "creator_rank": 1,
      "interactions_24h": 47802016
    }
  ]
}
```

Schema:

+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_avatar**: The URL to the avatar for the creator
+ **creator_followers**: number of followers the account has
+ **creator_rank**: ranking based on all posts in the last 24 hours that have interactions
+ **interactions_24h**: Number of interactions in the last 24 hours




---

### Category News

https://lunarcrush.com/api4/public/category/:category/news/v1

Get the top news posts for a category. Top news is determined by the metrics related to the social posts that mention the news posts.

input parameters:

+ **category**: _Provide the category to get details for. A category must be all lower case and can only include letters, numbers, and spaces._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/category/cryptocurrencies/news/v1
```



Example response:

```json
{
  "config": {
    "category": "cryptocurrencies",
    "type": "topic",
    "id": "_cryptocurrencies",
    "topic": "_cryptocurrencies",
    "generated": 1749549544
  },
  "data": [
    {
      "id": "thecryptobasic.com-4029930643",
      "post_type": "news",
      "post_title": "Chainlink or XRP? AI Models Reveal Their Top Pick in Direct Comparison",
      "post_link": "https://thecryptobasic.com/2025/06/10/chainlink-or-xrp-ai-models-reveal-their-top-pick-in-direct-comparison/",
      "post_image": "https://thecryptobasic.com/wp-content/uploads/2023/09/Chainlink-and-XRP.png",
      "post_created": 1749546817,
      "post_sentiment": 3.11,
      "creator_id": "twitter::1221786728379404288",
      "creator_name": "thecryptobasic",
      "creator_display_name": "TheCryptoBasic",
      "creator_followers": 67713,
      "creator_avatar": "https://pbs.twimg.com/profile_images/1231872139776667659/RKnqGDt6_200x200.png",
      "interactions_24h": 339,
      "interactions_total": 339
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **category**: LunarCrush social category. Can only includes letters, numbers and spaces
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **id**: LunarCrush internal ID for the asset
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **post_type**: The type of social post
+ **post_title**: The title text of the social post
+ **post_link**: The URL to view the social post on the social network
+ **post_image**: The URL to the primary image for the post if available
+ **post_created**: The unix timestamp of our best indication of when the post was created
+ **post_sentiment**: The sentiment of the post is a score between 1 and 5 with 1 being very negative, 3 being neutral, and 5 being very positive. A score of 3.5 is considered slightly positive.
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_followers**: number of followers the account has
+ **creator_avatar**: The URL to the avatar for the creator
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **interactions_total**: Number of total interactions




---

### Category Posts

https://lunarcrush.com/api4/public/category/:category/posts/v1

Get the top posts for a social topic. If start time is provided the result will be the top posts by interactions for the time range. If start is not provided it will be the most recent top posts by interactions from the last 24 hours.

input parameters:

+ **category**: _Provide the category to get details for. A category must be all lower case and can only include letters, numbers, and spaces._ **required**
+ **start**: _The start time (unix timestamp) to start at. Will be rounded to the beginning of the day. If the end parameter is not provided it will just be the top posts for this day._ 
+ **end**: _(Optional) The end time (unix timestamp) to stop at. Will be rounded to the end of the day._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/category/cryptocurrencies/posts/v1
```



Example response:

```json
{
  "config": {
    "category": "cryptocurrencies",
    "type": "topic",
    "id": "_cryptocurrencies",
    "topic": "_cryptocurrencies",
    "generated": 1749549544
  },
  "data": [
    {
      "id": "1932353239128686686",
      "post_type": "tweet",
      "post_title": "Good morning Friends.\n\n$BTC tapped $110,000.\n$ETH gains 7% in 24h. \n\nAre we back?",
      "post_link": "https://x.com/CryptoFellaTx/status/1932353239128686686",
      "post_image": "https://pbs.twimg.com/media/GtEZB5kWAAAOCjg.jpg",
      "post_created": 1749543888,
      "post_sentiment": 3.64,
      "creator_id": "twitter::1542080630376243202",
      "creator_name": "CryptoFellaTx",
      "creator_display_name": "Crypto Fella",
      "creator_followers": 98810,
      "creator_avatar": "https://pbs.twimg.com/profile_images/1793644989475434505/gOIqPAhP_200x200.jpg",
      "interactions_24h": 25014,
      "interactions_total": 25014
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **category**: LunarCrush social category. Can only includes letters, numbers and spaces
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **id**: Unique id of the social post
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **post_type**: The type of social post
+ **post_title**: The title text of the social post
+ **post_link**: The URL to view the social post on the social network
+ **post_image**: The URL to the primary image for the post if available
+ **post_created**: The unix timestamp of our best indication of when the post was created
+ **post_sentiment**: The sentiment of the post is a score between 1 and 5 with 1 being very negative, 3 being neutral, and 5 being very positive. A score of 3.5 is considered slightly positive.
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_followers**: number of followers the account has
+ **creator_avatar**: The URL to the avatar for the creator
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **interactions_total**: Number of total interactions




---

### Category Time Series

https://lunarcrush.com/api4/public/category/:category/time-series/v1

Get historical time series data for a social category

input parameters:

+ **category**: _Provide the category to get details for. A category must be all lower case and can only include letters, numbers, and spaces._ **required**
+ **bucket**: _bucket time series data into hours or days. default is hours._ 
+ **interval**: _Use interval to specify the start and end time automatically for convenience. If "start" or "end" parameters are provided this parameter is ignored._ 
+ **start**: _The start time (unix timestamp) to go back to._ 
+ **end**: _The end time (unix timestamp) to stop at._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/category/cryptocurrencies/time-series/v1
```



Example response:

```json
{
  "config": {
    "category": "cryptocurrencies",
    "topic": "_cryptocurrencies",
    "type": "topic",
    "id": "_cryptocurrencies",
    "interval": "1w",
    "start": 1748908800,
    "end": 1749556744,
    "bucket": "hour",
    "metrics": [],
    "remote_api": "danode1-13",
    "generated": 1749549544
  },
  "data": [
    {
      "time": 1748908800,
      "contributors_active": 64576,
      "contributors_created": 3843,
      "interactions": 12885957,
      "posts_active": 144851,
      "posts_created": 5334,
      "sentiment": 80,
      "spam": 622
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **category**: LunarCrush social category. Can only includes letters, numbers and spaces
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **id**: LunarCrush internal ID for the asset
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **bucket**: Data is generally bucketed into hours or days
+ **metrics**: Comma separated list of metrics to include or that are included
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **contributors_active**: number of unique social accounts with posts that have interactions
+ **contributors_created**: number of unique social accounts that created new posts
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **posts_active**: number of unique social posts with interactions
+ **posts_created**: number of unique social posts created
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **spam**: The number of posts created that are considered spam




---

### Category Topics

https://lunarcrush.com/api4/public/category/:category/topics/v1

Get the top topics for a social category

input parameters:

+ **category**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/category/musicians/topics/v1
```



Example response:

```json
{
  "data": [
    {
      "topic": 3038,
      "title": "Aerosmith",
      "topic_rank": 1634,
      "topic_rank_1h_previous": 1470,
      "topic_rank_24h_previous": 1517,
      "num_contributors": 882,
      "social_dominance": 0.13005759526026472,
      "num_posts": 1283,
      "interactions_24h": 2698011
    }
  ]
}
```

Schema:

+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **title**: The case sensitive title of the topic or category
+ **topic_rank**: LunarCrush metric for ranking a social topic relative to all other social topics
+ **topic_rank_1h_previous**: The topic rank from 1 hour ago
+ **topic_rank_24h_previous**: The topic rank from 24 hours ago
+ **num_contributors**: The number of unique social contributors to the topic
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **num_posts**: Total number of posts with interactions on this topic in the last 24 hours
+ **interactions_24h**: Number of interactions in the last 24 hours




---

### Category

https://lunarcrush.com/api4/public/category/:category/v1

Get summary information for a social category

input parameters:

+ **category**: _Provide the category to get details for. A category must be all lower case and can only include letters, numbers, and spaces. A category is the aggregation of all posts for all topics within the category._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/category/musicians/v1
```



Example response:

```json
{
  "data": {
    "topic": "_musicians",
    "title": "Musicians",
    "related_topics": [
      "aerosmith"
    ],
    "types_count": {
      "youtube-video": 196837,
      "news": 601,
      "reddit-post": 19943,
      "tweet": 122347,
      "tiktok-video": 46289
    },
    "types_interactions": {
      "youtube-video": 1234779146,
      "news": 769066,
      "reddit-post": 1087209,
      "tweet": 252272102,
      "tiktok-video": 364411526
    },
    "types_sentiment": {
      "youtube-video": 68,
      "news": 84,
      "reddit-post": 73,
      "tweet": 77,
      "tiktok-video": 68
    },
    "types_sentiment_detail": {
      "youtube-video": {
        "positive": 347921043,
        "neutral": 734921510,
        "negative": 151936593
      },
      "news": {
        "positive": 440205,
        "neutral": 276612,
        "negative": 52249
      },
      "reddit-post": {
        "positive": 477614,
        "neutral": 437781,
        "negative": 171814
      },
      "tweet": {
        "positive": 126524479,
        "neutral": 94275077,
        "negative": 31472546
      },
      "tiktok-video": {
        "positive": 99590786,
        "neutral": 217243073,
        "negative": 47577667
      }
    },
    "interactions_24h": 1853319049,
    "num_contributors": 216196,
    "num_posts": 386017,
    "trend": "down"
  }
}
```

Schema:

+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **title**: The case sensitive title of the topic or category
+ **related_topics**: an array of related topics
+ **types_count**: An object with the counts of the total number of unique posts getting interactions from each social network in the last 24 hours
+ **types_interactions**: An object with the counts of the total number of interactions on each post from each social network in the last 24 hours
+ **types_sentiment**: An object with the sentiment score broken down by each supported social network. 0% is all posts negative, 100% is all posts positive. 50% is equal positive and negative posts. Each post is weighted by interactions.
+ **types_sentiment_detail**: An object with the breakdown of positive, neutral, and negative posts by 24h interactions for each social network
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **num_contributors**: The number of unique social contributors to the topic
+ **num_posts**: Total number of posts with interactions on this topic in the last 24 hours
+ **trend**: One of up, down or flat to represent the general trend in interactions




---

### Coins Meta

https://lunarcrush.com/api4/public/coins/:coin/meta/v1

Get meta information for a cryptocurrency project. This includes information such as the website, social media links, and other information.

input parameters:

+ **coin**: _provide the numeric id or symbol of the coin or token._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/coins/2/meta/v1
```



Example response:

```json
{
  "data": {
    "id": 2,
    "name": "Ethereum",
    "symbol": "ETH",
    "market_categories": "layer-1",
    "updated": 1741059248,
    "blockchain": [
      {
        "type": "layer1",
        "network": "ethereum",
        "address": null,
        "decimals": null
      }
    ],
    "short_summary": "Ethereum is open access to digital money and data-friendly services for everyone â€“ no matter your background or location. It's a community-built technology behind the cryptocurrency ether (ETH) and thousands of applications you can use today.",
    "description": "Ethereum is a technology that lets you send cryptocurrency to anyone for a small fee. It also powers applications that everyone can use and no one can take down.\n\nIt's the world's programmable blockchain.\n\nEthereum builds on Bitcoin's innovation, with some big differences.\n\nBoth let you use digital money without payment providers or banks. But Ethereum is programmable, so you can also use it for lots of different digital assets â€“ even Bitcoin!\n\nThis also means Ethereum is for more than payments. It's a marketplace of financial services, games and apps that can't steal your data or censor you.",
    "github_link": "https://github.com/ethereum",
    "website_link": "https://www.ethereum.org/",
    "whitepaper_link": "https://ethereum.org/en/whitepaper",
    "twitter_link": "https://twitter.com/ethereum",
    "reddit_link": "https://www.reddit.com/r/ethereum/",
    "header_image": "headers/ethereum.png",
    "header_text": "The foundation for our digital future",
    "videos": "https://www.youtube.com/watch?v=GQR1xjQn5Pg",
    "coingecko_link": "https://www.coingecko.com/en/coins/ethereum",
    "coinmarketcap_link": "https://coinmarketcap.com/currencies/ethereum/"
  },
  "config": {
    "coin": "2",
    "generated": 1749549544
  }
}
```

Schema:

+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **updated**: Timestamp of when the data was last updated
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **network**: The social network for the post or influencer. We still refer to x as twitter out of developer preference.
+ **description**: Explanation of the change and the potential impact
+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data




---

### Coins Time Series

https://lunarcrush.com/api4/public/coins/:coin/time-series/v2

Get market time series data on a coin or token. Specify the coin to be queried by providing the numeric ID or the symbol of the coin in the input parameter, which can be found by calling the /coins/list endpoint.

input parameters:

+ **coin**: _provide the numeric id or symbol of the coin or token._ **required**
+ **bucket**: _bucket time series data into hours or days. default is hours._ 
+ **interval**: _Use interval to specify the start and end time automatically for convenience. If "start" or "end" parameters are provided this parameter is ignored._ 
+ **start**: _The start time (unix timestamp) to go back to._ 
+ **end**: _The end time (unix timestamp) to stop at._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/coins/2/time-series/v2
```



Example response:

```json
{
  "config": {
    "coin": "2",
    "topic": "ethereum",
    "id": "coins:2",
    "name": "Ethereum",
    "symbol": "ETH",
    "interval": "1w",
    "start": 1748908800,
    "end": 1749556744,
    "bucket": "hour",
    "metrics": [],
    "generated": 1749549544
  },
  "data": [
    {
      "time": 1748908800,
      "contributors_active": 8121,
      "contributors_created": 411,
      "interactions": 1482881,
      "posts_active": 14547,
      "posts_created": 491,
      "sentiment": 82,
      "spam": 121,
      "alt_rank": 67,
      "circulating_supply": 120723694,
      "close": 2621.79,
      "galaxy_score": 64,
      "high": 2621.79,
      "low": 2603.46,
      "market_cap": 316460047769,
      "market_dominance": 9.5251,
      "open": 2607.2,
      "social_dominance": 10.0427,
      "volume_24h": 18453700544
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **bucket**: Data is generally bucketed into hours or days
+ **metrics**: Comma separated list of metrics to include or that are included
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **contributors_active**: number of unique social accounts with posts that have interactions
+ **contributors_created**: number of unique social accounts that created new posts
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **posts_active**: number of unique social posts with interactions
+ **posts_created**: number of unique social posts created
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **spam**: The number of posts created that are considered spam
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **circulating_supply**: Circulating Supply is the total number of coins or tokens that are actively available for trade and are being used in the market and in general public
+ **close**: Close price for the time period
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **high**: Higest price fo rthe time period
+ **low**: Lowest price for the time period
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **open**: Open price for the time period
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **volume_24h**: Volume in USD for 24 hours up to this data point




---

### Coins

https://lunarcrush.com/api4/public/coins/:coin/v1

Get market data on a coin or token. Specify the coin to be queried by providing the numeric ID or the symbol of the coin in the input parameter, which can be found by calling the /coins/list endpoint.

input parameters:

+ **coin**: _provide the numeric id or symbol of the coin or token._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/coins/2/v1
```



Example response:

```json
{
  "config": {
    "id": "coins:2",
    "name": "Ethereum",
    "symbol": "ETH",
    "topic": "ethereum",
    "generated": 1749549544
  },
  "data": {
    "id": 2,
    "name": "Ethereum",
    "symbol": "ETH",
    "price": 2692.042882347701,
    "price_btc": 0.02457838172344049,
    "market_cap": 324990530857.09,
    "percent_change_24h": 7.036343244704,
    "percent_change_7d": 2.882054247732,
    "percent_change_30d": 7.024290007132,
    "volume_24h": 27252807840.1,
    "max_supply": null,
    "circulating_supply": 120722642.64,
    "close": 2692.042882347701,
    "galaxy_score": 74.3,
    "alt_rank": 19,
    "volatility": 0.0289,
    "market_cap_rank": 2
  }
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **price**: Current price in USD
+ **price_btc**: Current price in BTC
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **percent_change_7d**: Percent change in price since 7 days ago
+ **percent_change_30d**: Percent change in price since 30 days ago
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **max_supply**: The maximum supply of the asset if available
+ **circulating_supply**: Circulating Supply is the total number of coins or tokens that are actively available for trade and are being used in the market and in general public
+ **close**: Close price for the time period
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **volatility**: Volatility is calculated as the standard deviation of the price.
+ **market_cap_rank**: The rank of the asset by market cap with additional filtering to remove outliers and bad market data.




---

### Coins List

https://lunarcrush.com/api4/public/coins/list/v1

Get a general snapshot of LunarCrush metrics on the entire list of tracked coins. This version is heavily cached and up to 1 hour behind. It is designed as a lightweight mechanism for monitoring the universe of available assets, either in aggregate or relative to each other. Metrics include Galaxy Scoreâ„¢, AltRankâ„¢, price, volatility, 24h percent change, market cap, social mentions, social interactions, social contributors, social dominance, and categories. Use the coins/list/v2 endpoint for data updated every few seconds.

input parameters:

+ **sort**: _sort the output by metric_ 
+ **filter**: _filter by sub categories / sector from the "categories" key. Separate by commas for multiple matches. Available sectors can be found on the sector filters at https://lunarcrush.com/categories/cryptocurrencies_ 
+ **limit**: _limit the number of results. Default is 10 maximum is 1000 per page._ 
+ **desc**: _Pass any value as desc and the output will be reversed (descending)_ 
+ **page**: _When using limit, set the page of results to display, pages start at 0_ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/coins/list/v1
```



Example response:

```json
{
  "config": {
    "sort": "market_cap_rank",
    "desc": true,
    "limit": 0,
    "page": 0,
    "total_rows": 6628,
    "generated": 1749549545
  },
  "data": [
    {
      "id": 1,
      "symbol": "BTC",
      "name": "Bitcoin",
      "price": 109528.89057705089,
      "price_btc": 1,
      "volume_24h": 59770903936.57,
      "volatility": 0.0156,
      "circulating_supply": 19876850,
      "max_supply": 21000000,
      "percent_change_1h": 0.382878535386,
      "percent_change_24h": 2.602493206182,
      "percent_change_7d": 4.06181058705,
      "market_cap": 2177089328666.45,
      "market_cap_rank": 1,
      "interactions_24h": 96447578,
      "social_volume_24h": 97995,
      "social_dominance": 17.64343675675481,
      "market_dominance": 63.87888526301957,
      "market_dominance_prev": 65.91964180701686,
      "galaxy_score": 67.6,
      "galaxy_score_previous": 64,
      "alt_rank": 380,
      "alt_rank_previous": 119,
      "sentiment": 79,
      "categories": "layer-1,bitcoin-ecosystem,pow",
      "blockchains": [
        {
          "type": "layer1",
          "network": "bitcoin",
          "address": null,
          "decimals": null
        }
      ],
      "percent_change_30d": 4.94690523836,
      "last_updated_price": 1749549537,
      "last_updated_price_by": "cmc_stream",
      "topic": "btc bitcoin",
      "logo": "https://cdn.lunarcrush.com/bitcoin.png"
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **symbol**: The symbol for the asset
+ **name**: The full name of the asset
+ **price**: Current price in USD
+ **price_btc**: Current price in BTC
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **volatility**: Volatility is calculated as the standard deviation of the price.
+ **circulating_supply**: Circulating Supply is the total number of coins or tokens that are actively available for trade and are being used in the market and in general public
+ **max_supply**: The maximum supply of the asset if available
+ **percent_change_1h**: Percent change in price since 1 hour ago
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **percent_change_7d**: Percent change in price since 7 days ago
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_cap_rank**: The rank of the asset by market cap with additional filtering to remove outliers and bad market data.
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **social_volume_24h**: Total number of posts with interactions on this topic in the last 24 hours
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **galaxy_score_previous**: The galaxy score from the previous 24 hours
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **alt_rank_previous**: The alt rank from the previous 24 hours
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **categories**: A comma delimited string of sub categories/sectors this asset belongs to
+ **blockchains**: An array of blockchains that the asset is part of including the contract address and decimals if applicable
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **network**: The name of the blockchain or network
+ **address**: The contract address, zero or null means it is a layer 1
+ **percent_change_30d**: Percent change in price since 30 days ago
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **logo**: The URL to the logo for the asset, topic, or category




---

### Coins List v2

https://lunarcrush.com/api4/public/coins/list/v2

Get a general snapshot of LunarCrush metrics on the entire list of tracked coins. It is designed as a lightweight mechanism for monitoring the universe of available assets, either in aggregate or relative to each other. Metrics include Galaxy Scoreâ„¢, AltRankâ„¢, price, volatility, 24h percent change, market cap, social mentions, social interactions, social contributors, social dominance, and categories.

input parameters:

+ **sort**: _sort the output by metric_ 
+ **filter**: _filter by sub categories / sector from the "categories" key. Separate by commas for multiple matches. Available sectors can be found on the sector filters at https://lunarcrush.com/categories/cryptocurrencies_ 
+ **limit**: _limit the number of results. Default is 10 maximum is 1000 per page._ 
+ **desc**: _Pass any value as desc and the output will be reversed (descending)_ 
+ **page**: _When using limit, set the page of results to display, pages start at 0_ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/coins/list/v2
```



Example response:

```json
{
  "config": {
    "sort": "market_cap_rank",
    "desc": true,
    "limit": 0,
    "page": 0,
    "total_rows": 6628,
    "generated": 1749549545
  },
  "data": [
    {
      "id": 1,
      "symbol": "BTC",
      "name": "Bitcoin",
      "price": 109528.89057705089,
      "price_btc": 1,
      "volume_24h": 59770903936.57,
      "volatility": 0.0156,
      "circulating_supply": 19876850,
      "max_supply": 21000000,
      "percent_change_1h": 0.382878535386,
      "percent_change_24h": 2.602493206182,
      "percent_change_7d": 4.06181058705,
      "market_cap": 2177089328666.45,
      "market_cap_rank": 1,
      "interactions_24h": 96447578,
      "social_volume_24h": 97995,
      "social_dominance": 17.64343675675481,
      "market_dominance": 63.87888526301957,
      "market_dominance_prev": 65.91964180701686,
      "galaxy_score": 67.6,
      "galaxy_score_previous": 64,
      "alt_rank": 380,
      "alt_rank_previous": 119,
      "sentiment": 79,
      "categories": "layer-1,bitcoin-ecosystem,pow",
      "blockchains": [
        {
          "type": "layer1",
          "network": "bitcoin",
          "address": null,
          "decimals": null
        }
      ],
      "percent_change_30d": 4.94690523836,
      "last_updated_price": 1749549537,
      "last_updated_price_by": "cmc_stream",
      "topic": "btc bitcoin",
      "logo": "https://cdn.lunarcrush.com/bitcoin.png"
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **symbol**: The symbol for the asset
+ **name**: The full name of the asset
+ **price**: Current price in USD
+ **price_btc**: Current price in BTC
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **volatility**: Volatility is calculated as the standard deviation of the price.
+ **circulating_supply**: Circulating Supply is the total number of coins or tokens that are actively available for trade and are being used in the market and in general public
+ **max_supply**: The maximum supply of the asset if available
+ **percent_change_1h**: Percent change in price since 1 hour ago
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **percent_change_7d**: Percent change in price since 7 days ago
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_cap_rank**: The rank of the asset by market cap with additional filtering to remove outliers and bad market data.
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **social_volume_24h**: Total number of posts with interactions on this topic in the last 24 hours
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **galaxy_score_previous**: The galaxy score from the previous 24 hours
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **alt_rank_previous**: The alt rank from the previous 24 hours
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **categories**: A comma delimited string of sub categories/sectors this asset belongs to
+ **blockchains**: An array of blockchains that the asset is part of including the contract address and decimals if applicable
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **network**: The name of the blockchain or network
+ **address**: The contract address, zero or null means it is a layer 1
+ **percent_change_30d**: Percent change in price since 30 days ago
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **logo**: The URL to the logo for the asset, topic, or category




---

### Creator Posts

https://lunarcrush.com/api4/public/creator/:network/:id/posts/v1

Get the top posts for a specific creator.

input parameters:

+ **network**: _Network for the creator. One of twitter, youtube, instagram, reddit, or tiktok_ **required**
+ **id**: _Unique ID or screen name of the creator_ **required**
+ **start**: _The start time (unix timestamp) to start at. Will be rounded to the beginning of the day. If the end parameter is not provided it will just be the top posts for this day._ 
+ **end**: _(Optional) The end time (unix timestamp) to stop at. Will be rounded to the end of the day._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/creator/twitter/elonmusk/posts/v1
```



Example response:

```json
{
  "data": [
    {
      "id": "1924174964673884540",
      "post_type": "tweet",
      "post_title": "Impressive range",
      "post_created": 1747594035,
      "post_sentiment": 3.04,
      "post_link": "https://x.com/elonmusk/status/1924174964673884540",
      "post_image": null,
      "creator_id": "twitter::44196397",
      "creator_name": "elonmusk",
      "creator_display_name": "Elon Musk",
      "creator_followers": 221008497,
      "creator_avatar": "https://pbs.twimg.com/profile_images/1926284313365979137/o2cF3MeJ_200x200.jpg",
      "interactions_24h": 0,
      "interactions_total": 49783798
    }
  ]
}
```

Schema:

+ **id**: Unique id of the social post
+ **post_type**: The type of social post
+ **post_title**: The title text of the social post
+ **post_created**: The unix timestamp of our best indication of when the post was created
+ **post_sentiment**: The sentiment of the post is a score between 1 and 5 with 1 being very negative, 3 being neutral, and 5 being very positive. A score of 3.5 is considered slightly positive.
+ **post_link**: The URL to view the social post on the social network
+ **post_image**: The URL to the primary image for the post if available
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_followers**: number of followers the account has
+ **creator_avatar**: The URL to the avatar for the creator
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **interactions_total**: Number of total interactions




---

### Creator Time Series

https://lunarcrush.com/api4/public/creator/:network/:id/time-series/v1

Get time series data on a creator.

input parameters:

+ **network**: _Influencer social network_ **required**
+ **id**: _The unique id or screen name of the creator_ **required**
+ **bucket**: _bucket time series data into hours or days. default is hours._ 
+ **interval**: _Use interval to specify the start and end time automatically for convenience. If "start" or "end" parameters are provided this parameter is ignored._ 
+ **start**: _The start time (unix timestamp) to go back to._ 
+ **end**: _The end time (unix timestamp) to stop at._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/creator/twitter/lunarcrush/time-series/v1
```



Example response:

```json
{
  "config": {
    "network": "twitter",
    "influencer_id": "twitter::988992203568562176",
    "interval": "1w",
    "start": 1748908800,
    "end": 1749600000,
    "bucket": "hour",
    "name": "lunarcrush",
    "remote_api": "danode2-13",
    "generated": 1749549545
  },
  "data": [
    {
      "time": 1748908800,
      "followers": 313274,
      "interactions": 1125,
      "posts_active": 34
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **network**: The social network for the post or influencer. We still refer to x as twitter out of developer preference.
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **bucket**: Data is generally bucketed into hours or days
+ **name**: The full name of the asset
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **followers**: The number of publicly displayed followers the creator has
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **posts_active**: number of unique social posts with interactions




---

### Creator

https://lunarcrush.com/api4/public/creator/:network/:id/v1

Get detail information on a specific creator

input parameters:

+ **network**: _Provide the network for the creator. One of twitter, youtube, instagram, reddit, or tiktok_ **required**
+ **id**: _Provide the unique ID or screen name of the creator_ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/creator/twitter/elonmusk/v1
```



Example response:

```json
{
  "data": {
    "creator_id": "twitter::44196397",
    "creator_name": "elonmusk",
    "creator_display_name": "Elon Musk",
    "creator_avatar": "https://pbs.twimg.com/profile_images/1926284313365979137/o2cF3MeJ_200x200.jpg",
    "creator_followers": 221009538,
    "creator_rank": "1",
    "interactions_24h": 848920228,
    "topic_influence": [
      {
        "topic": "elon musk",
        "count": 87,
        "percent": 4.02,
        "rank": 1
      }
    ]
  }
}
```

Schema:

+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_avatar**: The URL to the avatar for the creator
+ **creator_followers**: number of followers the account has
+ **creator_rank**: ranking based on all posts in the last 24 hours that have interactions
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **topic_influence**: an array of social topics and the creators ranking on each topic
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $




---

### Creators List

https://lunarcrush.com/api4/public/creators/list/v1

Get a list of trending social creators over all of social based on interactions. To get lists of creators by category or topic see the topics and categories endpoints.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/creators/list/v1
```



Example response:

```json
{
  "data": [
    {
      "creator_name": "elonmusk",
      "creator_display_name": "Elon Musk",
      "creator_id": "44196397",
      "creator_network": "twitter",
      "creator_avatar": "https://pbs.twimg.com/profile_images/1926284313365979137/o2cF3MeJ_200x200.jpg",
      "creator_followers": 221009538,
      "creator_posts": 1286,
      "creator_rank": 1,
      "interactions_24h": 848920228
    }
  ]
}
```

Schema:

+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_network**: The social network for the post or influencer. We still refer to x as twitter out of developer preference.
+ **creator_avatar**: The URL to the avatar for the creator
+ **creator_followers**: number of followers the account has
+ **creator_posts**: total number of posts with interactions in the last 24 hours
+ **creator_rank**: ranking based on all posts in the last 24 hours that have interactions
+ **interactions_24h**: Number of interactions in the last 24 hours




---

### Nfts Time Series

https://lunarcrush.com/api4/public/nfts/:nft/time-series/v1

Get market time series data on an nft collection. Specify the nft to be queried by providing the numeric ID or slug of the nft collection in the input parameter, which can be found by calling the /public/nfts/list endpoint.

input parameters:

+ **nft**: _provide the numeric id or symbol of the nft collection._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/nfts/2/time-series/v1
```



Example response:

```json
{
  "config": {
    "nft": "2",
    "interval": "1w",
    "bucket": "hour",
    "start": 1748908800,
    "end": 1749549546,
    "generated": 1749549545
  },
  "data": {
    "id": 2,
    "name": "CryptoPunks",
    "symbol": "cryptopunks"
  },
  "timeSeries": [
    {
      "time": 1748908800,
      "market_cap": 457500,
      "alt_rank": 222
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **bucket**: Data is generally bucketed into hours or days
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **time**: A unix timestamp (in seconds)
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported




---

### Nfts Time Series v2

https://lunarcrush.com/api4/public/nfts/:nft/time-series/v2

Get market time series data on a nft. Specify the nft to be queried by providing the numeric ID or the symbol of the nft in the input parameter, which can be found by calling the /nfts/list endpoint.

input parameters:

+ **nft**: _provide the numeric id or symbol of the nft or token._ **required**
+ **bucket**: _bucket time series data into hours or days. default is hours._ 
+ **interval**: _Use interval to specify the start and end time automatically for convenience. If "start" or "end" parameters are provided this parameter is ignored._ 
+ **start**: _The start time (unix timestamp) to go back to._ 
+ **end**: _The end time (unix timestamp) to stop at._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/nfts/2/time-series/v2
```



Example response:

```json
{
  "config": {
    "nft": 2,
    "topic": "cryptopunks",
    "interval": "1w",
    "bucket": "hour",
    "start": 1748908800,
    "end": 1749549546,
    "generated": 1749549545
  },
  "data": [
    {
      "time": 1748908800,
      "market_cap": 457500,
      "alt_rank": 222,
      "contributors_active": 61,
      "contributors_created": 1,
      "posts_active": 83,
      "posts_created": 1,
      "interactions": 1693,
      "social_dominance": 1.4648782209671725,
      "sentiment": 78
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **bucket**: Data is generally bucketed into hours or days
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **contributors_active**: number of unique social accounts with posts that have interactions
+ **contributors_created**: number of unique social accounts that created new posts
+ **posts_active**: number of unique social posts with interactions
+ **posts_created**: number of unique social posts created
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.




---

### Nfts

https://lunarcrush.com/api4/public/nfts/:nft/v1

Get market data on an nft collection. Specify the nft to be queried by providing the numeric ID or the slug of the nft in the input parameter, which can be found by calling the /public/nfts/list endpoint.

input parameters:

+ **nft**: _provide the numeric id or slug of the nft._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/nfts/2/v1
```



Example response:

```json
{
  "config": {
    "nft": "2",
    "generated": 1749549545
  },
  "data": {
    "id": 2,
    "name": "CryptoPunks",
    "floor_price": 44,
    "market_cap": 440000,
    "percent_change_24h": 0,
    "volume_24h": 0
  }
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **volume_24h**: Volume in USD for 24 hours up to this data point




---

### Nfts List

https://lunarcrush.com/api4/public/nfts/list/v1

Lists all nft collections supported by LunarCrush. Includes the "topic" endpoint to use to get social data from this nft collection as a social topic.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/nfts/list/v1
```



Example response:

```json
{
  "config": {
    "sort": "market_cap_rank",
    "desc": true,
    "limit": 0,
    "page": 0,
    "total_rows": 461,
    "generated": 1749549545
  },
  "data": [
    {
      "id": 2876,
      "lunar_id": "Nouns-Fork-0",
      "base_crypto": "ETH",
      "name": "Nouns - Fork 0",
      "floor_price": 1.08498,
      "volume_24h": 0,
      "percent_change_24h": 0,
      "market_cap": 11360.82558,
      "interactions_24h": 0,
      "social_volume_24h": 0,
      "social_contributors": 0,
      "social_dominance": 0,
      "galaxy_score": 0,
      "alt_rank": 418,
      "logo": "https://cdn.lunarcrush.com/nfts/nouns-fork-0.png"
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **lunar_id**: LunarCrush human readable slug/ID for the asset
+ **base_crypto**: The base crypto used to calculate the crypto_usd value
+ **name**: The full name of the asset
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **social_volume_24h**: Total number of posts with interactions on this topic in the last 24 hours
+ **social_contributors**: The number of unique social contributors in the last 24 hours
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **logo**: The URL to the logo for the asset, topic, or category




---

### Nfts List v2

https://lunarcrush.com/api4/public/nfts/list/v2

Get a general snapshot of LunarCrush metrics on the entire list of tracked NFTS. It is designed as a lightweight mechanism for monitoring the universe of available assets, either in aggregate or relative to each other. Metrics include Galaxy Scoreâ„¢, AltRankâ„¢, floor price, 24h percent change, market cap, social mentions, social interactions, social contributors, social dominance, and categories.

input parameters:

+ **sort**: _sort the output by metric_ 
+ **limit**: _limit the number of results. Default is 10 maximum is 100 per page._ 
+ **desc**: _Pass any value as desc and the output will be reversed (descending)_ 
+ **page**: _When using limit, set the page of results to display, pages start at 0_ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/nfts/list/v2
```



Example response:

```json
{
  "config": {
    "limit": 0,
    "sort": "market_cap_rank",
    "desc": true,
    "page": 0,
    "total_rows": 461,
    "generated": 1749549545
  },
  "data": [
    {
      "id": 2876,
      "lunar_id": "Nouns-Fork-0",
      "base_crypto": "ETH",
      "name": "Nouns - Fork 0",
      "floor_price": 1.08498,
      "volume_24h": 0,
      "percent_change_24h": 0,
      "market_cap": 11360.82558,
      "interactions_24h": 0,
      "social_volume_24h": 0,
      "social_contributors": 0,
      "social_dominance": 0,
      "galaxy_score": 0,
      "alt_rank": 418,
      "logo": "https://cdn.lunarcrush.com/nfts/nouns-fork-0.png"
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **lunar_id**: LunarCrush human readable slug/ID for the asset
+ **base_crypto**: The base crypto used to calculate the crypto_usd value
+ **name**: The full name of the asset
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **social_volume_24h**: Total number of posts with interactions on this topic in the last 24 hours
+ **social_contributors**: The number of unique social contributors in the last 24 hours
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **logo**: The URL to the logo for the asset, topic, or category




---

### Posts Time Series

https://lunarcrush.com/api4/public/posts/:post_type/:post_id/time-series/v1

Get interactions over time for a post. If a post is older than 365 days the time series will be returned as daily interactions, otherwise it hourly interactions

input parameters:

+ **post_type**: _The post type e.g. tweet, youtube-video, tiktok-video, reddit-post, instagram-post_ **required**
+ **post_id**: _The unique id of a post, for twitter it is a number, youtube it is the id in the url after watch?v=, look in the url for the unique id_ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/posts/tweet/1756378079893782591/time-series/v1
```



Example response:

```json
{
  "data": [
    {
      "time": "1707523200",
      "interactions": 24
    }
  ]
}
```

Schema:

+ **time**: A unix timestamp (in seconds)
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)




---

### Posts

https://lunarcrush.com/api4/public/posts/:post_type/:post_id/v1

Get details of a post

input parameters:

+ **post_type**: _The post type e.g. tweet, youtube-video, tiktok-video, reddit-post, instagram-post_ **required**
+ **post_id**: _The unique id of a post, for twitter it is a number, youtube it is the id in the url after watch?v=, look in the url for the unique id_ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/posts/tweet/1756378079893782591/v1
```



Example response:

```json
{
  "type": "tweet",
  "id": "1756378079893782591",
  "title": "Social activity is ðŸ‘† across the board today. \n\nðŸ¤” What are y'all talking about? \nðŸ«¡ We've got you covered.\n\nðŸ‘©â€ðŸ’» Technology\nðŸ’¬ Social Networks\nðŸ‘¨â€ðŸŽ¤ Musicians\nðŸ•º Celebrities\nðŸŒ Countries\nðŸŽ® Gaming\nðŸ–ï¸ Travel\nðŸš— Automotive\nðŸ¥· Cryptocurrencies\nðŸ‡ºðŸ‡¸ US Election\n\nðŸš€ https://t.co/AI5yuZEyi7 https://t.co/T0mqJBiyx0",
  "description": null,
  "extraText": "https://lunarcrush.com/categories?rpp=300&page=1&cols=topic_rank%2Ccontributors_active%2Cposts_active%2Caverage_sentiment%2Cinteractions_24h%2Cinteractions_trend",
  "metrics": {
    "bookmarks": 2,
    "favorites": 20,
    "retweets": 3,
    "replies": 13,
    "views": 13004
  },
  "image": {
    "src": "https://pbs.twimg.com/media/GF_n3GQaoAA23sT.jpg",
    "width": 2048,
    "height": 989
  },
  "video": null,
  "images": null,
  "creator_id": "twitter::988992203568562176",
  "creator_name": "LunarCrush",
  "creator_display_name": "LunarCrush Analytics",
  "creator_avatar": "https://pbs.twimg.com/profile_images/1863747720827244545/xoSWaM53_200x200.png",
  "topics": [
    "analytics"
  ],
  "categories": []
}
```

Schema:

+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **id**: Unique id of the social post
+ **title**: Title of the social post
+ **description**: Explanation of the change and the potential impact
+ **extraText**: Extra text for the post for search matching like the retweet text or text included in the video
+ **metrics**: Comma separated list of metrics to include or that are included
+ **image**: Provides the url/src width and height of a the image in the post if available
+ **video**: Provides the url/src width and height of a the video in the post if available
+ **images**: Provides the url/src width and height of a the images in the post if available
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_avatar**: The URL to the avatar for the creator
+ **categories**: an array of categories this topic aggregates into




---

### Searches

https://lunarcrush.com/api4/public/searches/:slug

See the summary output of a custom search aggregation.

input parameters:

+ **slug**: _The ID of the custom search aggregation to view._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/searches/:slug
```



Example response:

```json
{
  "error": "Use the topics endpoints to get the latest data like /public/topic/:slug/v1"
}
```

Schema:





---

### Searches Delete

https://lunarcrush.com/api4/public/searches/:slug/delete

Delete a custom search aggregation.

input parameters:

+ **slug**: _The ID of the custom search aggregation to delete._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/searches/:slug/delete
```



Example response:

```json
{
  "error": "Error: That item does not exist"
}
```

Schema:





---

### Searches Update

https://lunarcrush.com/api4/public/searches/:slug/update

Update a custom search aggregation name or priority. Search terms and configuration cannot be changed once created.

input parameters:

+ **slug**: _The ID of the custom search aggregation to update._ **required**
+ **name**: _The name of the custom search aggregation._ 
+ **search_json**: _A JSON object (stringified) that defines the search criteria for the custom search aggregation. Search terms and configuration cannot be changed once created. Posts that match any of the search term will be included. For each search term there are optional inclusion and exclusion terms to help fine tune the results._ **required**
+ **priority**: _Define if this is a high priority search aggregation. Pro accounts get up to 10 high priority search aggregations at a time._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/searches/:slug/update
```



Example response:

```json
{
  "error": "Error: search_json is required"
}
```

Schema:





---

### Searches Create

https://lunarcrush.com/api4/public/searches/create

Create a custom search aggregation of topics and search terms. Fine tune the posts that get included or excluded. Search terms and configuration cannot be changed once created. If successful returns the new id/slug and the processed search config. Note that search terms will be adjusted and simplified for optimized search and matching.

input parameters:

+ **name**: _The name of the custom search aggregation._ **required**
+ **search_json**: _A JSON object (stringified) that defines the search criteria for the custom search aggregation. Search terms and configuration cannot be changed once created. Posts that match any of the search term will be included. For each search term there are optional inclusion and exclusion terms to help fine tune the results._ **required**
+ **priority**: _Flag as a high priority search aggregation. Pro accounts get up to 10 high priority search aggregations at a time._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/searches/create
```



Example response:

```json
{
  "error": "Error: name is required"
}
```

Schema:





---

### Searches List

https://lunarcrush.com/api4/public/searches/list

List all custom search aggregations.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/searches/list
```



Example response:

```json
{
  "data": [
    {
      "id": "lc1s5M27Jq",
      "name": "Pump.fun Leaderboard",
      "search_json": {
        "terms": [],
        "rollups": [
          "7hb4agnzp7rithvtftgmedkru3g8x34fwhzy1vqjpump"
        ]
      },
      "priority": false,
      "created": 1749064987
    }
  ]
}
```

Schema:

+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset




---

### Searches Search

https://lunarcrush.com/api4/public/searches/search

Get recently popular social posts matching a single search term or phrase. Optionally configure and test a custom search configuration.

input parameters:

+ **term**: _Test a single search term or phrase_ 
+ **search_json**: _A JSON object (stringified) that defines the search criteria for the custom search aggregation. Posts that match any of the search term will be included. For each search term there are optional inclusion and exclusion terms to help fine tune the results._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/searches/search
```



Example response:

```json
{
  "error": "Error: search_json object is not formatted correctly"
}
```

Schema:





---

### Stocks Time Series

https://lunarcrush.com/api4/public/stocks/:stock/time-series/v2

Get market time series data on a stock. Specify the stock to be queried by providing the numeric ID or the symbol of the stock in the input parameter, which can be found by calling the /stocks/list endpoint.

input parameters:

+ **stock**: _provide the numeric id or symbol of the stock or token._ **required**
+ **bucket**: _bucket time series data into hours or days. default is hours._ 
+ **interval**: _Use interval to specify the start and end time automatically for convenience. If "start" or "end" parameters are provided this parameter is ignored._ 
+ **start**: _The start time (unix timestamp) to go back to._ 
+ **end**: _The end time (unix timestamp) to stop at._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/stocks/7056/time-series/v2
```



Example response:

```json
{
  "config": {
    "stock": "7056",
    "topic": "$nvda",
    "id": "stocks:7056",
    "name": "NVIDIA Corp.",
    "symbol": "NVDA",
    "interval": "1w",
    "start": 1748908800,
    "end": 1749556745,
    "bucket": "hour",
    "metrics": [],
    "generated": 1749549545
  },
  "data": [
    {
      "time": 1748908800,
      "contributors_active": 3578,
      "contributors_created": 157,
      "interactions": 966989,
      "posts_active": 6262,
      "posts_created": 233,
      "sentiment": 77,
      "spam": 87,
      "alt_rank": 202,
      "close": 137.37,
      "galaxy_score": 66,
      "high": 137.37,
      "low": 137.37,
      "market_cap": 3352801345296,
      "market_dominance": 4.6146,
      "open": 137.37,
      "social_dominance": 15.3424
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **bucket**: Data is generally bucketed into hours or days
+ **metrics**: Comma separated list of metrics to include or that are included
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **contributors_active**: number of unique social accounts with posts that have interactions
+ **contributors_created**: number of unique social accounts that created new posts
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **posts_active**: number of unique social posts with interactions
+ **posts_created**: number of unique social posts created
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **spam**: The number of posts created that are considered spam
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **close**: Close price for the time period
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **high**: Higest price fo rthe time period
+ **low**: Lowest price for the time period
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **open**: Open price for the time period
+ **social_dominance**: The percent of the total social volume that this topic represents




---

### Stocks

https://lunarcrush.com/api4/public/stocks/:stock/v1

Get market data on a stock. Specify the coin to be queried by providing the numeric ID or the symbol of the coin in the input parameter, which can be found by calling the /coins/list endpoint.

input parameters:

+ **stock**: _provide the numeric id or symbol of the stock._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/stocks/7056/v1
```



Example response:

```json
{
  "config": {
    "id": "stocks:7056",
    "name": "NVIDIA Corp.",
    "symbol": "NVDA",
    "topic": "$nvda",
    "generated": 1749549545
  },
  "data": {
    "id": 7056,
    "name": "NVIDIA Corp.",
    "symbol": "NVDA",
    "price": 142.55,
    "market_cap": 3506487665000,
    "percent_change_24h": 0.5856618684730542,
    "volume_24h": 26242306134,
    "close": 142.55,
    "market_cap_rank": 1125
  }
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **price**: Current price in USD
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **close**: Close price for the time period
+ **market_cap_rank**: The rank of the asset by market cap with additional filtering to remove outliers and bad market data.




---

### Stocks List

https://lunarcrush.com/api4/public/stocks/list/v1

Lists all stocks supported by LunarCrush. Includes the "topic" endpoint to use to get social data from this asset as a social topic.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/stocks/list/v1
```



Example response:

```json
{
  "config": {
    "sort": "market_cap_rank",
    "desc": true,
    "limit": 0,
    "page": 0,
    "total_rows": 2141,
    "generated": 1749549545
  },
  "data": [
    {
      "id": 4336,
      "symbol": "GOOGL",
      "name": "Alphabet Inc Class A",
      "price": "176.040000",
      "volume_24h": 4626707150,
      "percent_change_24h": 1.3588208198986558,
      "market_cap": "2143106481063.18",
      "market_cap_rank": 1,
      "interactions_24h": 2050193,
      "social_volume_24h": 3703,
      "social_dominance": 2.60862826871055,
      "market_dominance": 2.799230453859361,
      "market_dominance_prev": 4.726797053924779,
      "galaxy_score": 62.3,
      "galaxy_score_previous": 59,
      "alt_rank": 135,
      "alt_rank_previous": 53,
      "sentiment": 79,
      "categories": "communication-services",
      "last_updated_price": 1749549537,
      "last_updated_price_by": "robinhood",
      "topic": "googl alphabet inc class a",
      "logo": "https://cdn.lunarcrush.com/stocks/googl.png"
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **symbol**: The symbol for the asset
+ **name**: The full name of the asset
+ **price**: Current price in USD
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_cap_rank**: The rank of the asset by market cap with additional filtering to remove outliers and bad market data.
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **social_volume_24h**: Total number of posts with interactions on this topic in the last 24 hours
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **galaxy_score_previous**: The galaxy score from the previous 24 hours
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **alt_rank_previous**: The alt rank from the previous 24 hours
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **categories**: an array of categories this topic aggregates into
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **logo**: The URL to the logo for the asset, topic, or category




---

### Stocks List v2

https://lunarcrush.com/api4/public/stocks/list/v2

Get a general snapshot of LunarCrush metrics on the entire list of tracked stocks. It is designed as a lightweight mechanism for monitoring the universe of available assets, either in aggregate or relative to each other. Metrics include Galaxy Scoreâ„¢, AltRankâ„¢, floor price, 24h percent change, market cap, social mentions, social interactions, social contributors, social dominance, and categories.

input parameters:

+ **sort**: _sort the output by metric_ 
+ **limit**: _limit the number of results. Default is 10 maximum is 100 per page._ 
+ **desc**: _Pass any value as desc and the output will be reversed (descending)_ 
+ **page**: _When using limit, set the page of results to display, pages start at 0_ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/stocks/list/v2
```



Example response:

```json
{
  "config": {
    "limit": 0,
    "sort": "market_cap_rank",
    "desc": true,
    "page": 0,
    "total_rows": 2141,
    "generated": 1749549545
  },
  "data": [
    {
      "id": 4336,
      "symbol": "GOOGL",
      "name": "Alphabet Inc Class A",
      "price": "176.040000",
      "volume_24h": 4626707150,
      "percent_change_24h": 1.3588208198986558,
      "market_cap": "2143106481063.18",
      "market_cap_rank": 1,
      "interactions_24h": 2050193,
      "social_volume_24h": 3703,
      "social_dominance": 2.60862826871055,
      "market_dominance": 2.799230453859361,
      "market_dominance_prev": 4.726797053924779,
      "galaxy_score": 62.3,
      "galaxy_score_previous": 59,
      "alt_rank": 135,
      "alt_rank_previous": 53,
      "sentiment": 79,
      "categories": "communication-services",
      "last_updated_price": 1749549537,
      "last_updated_price_by": "robinhood",
      "topic": "googl alphabet inc class a",
      "logo": "https://cdn.lunarcrush.com/stocks/googl.png"
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **id**: LunarCrush internal ID for the asset
+ **symbol**: The symbol for the asset
+ **name**: The full name of the asset
+ **price**: Current price in USD
+ **volume_24h**: Volume in USD for 24 hours up to this data point
+ **percent_change_24h**: Percent change in price since 24 hours ago
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_cap_rank**: The rank of the asset by market cap with additional filtering to remove outliers and bad market data.
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **social_volume_24h**: Total number of posts with interactions on this topic in the last 24 hours
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **galaxy_score_previous**: The galaxy score from the previous 24 hours
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **alt_rank_previous**: The alt rank from the previous 24 hours
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **categories**: an array of categories this topic aggregates into
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **logo**: The URL to the logo for the asset, topic, or category




---

### System Changes

https://lunarcrush.com/api4/public/system/changes

Updates to potential changes to historical time series data. Search term changes only impact the most recent 72 hours (hourly) or 3 days (daily) data. "full historical" is a change that may impact the full history of data. Each change provides a description of what is impacted and why.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/system/changes
```



Example response:

```json
{
  "data": [
    {
      "asset_type": "coins",
      "asset_id": 160888,
      "asset_name": "BUCKET (BUCKET)",
      "change": "search terms established",
      "description": "search criteria initially set for this asset for the purposes of tracking changes over time",
      "time": 1749547738
    }
  ]
}
```

Schema:

+ **asset_type**: One of coins, nfts, stocks, topic or category
+ **asset_id**: The id of the asset (coin, nft, stock, topic, or category)
+ **asset_name**: The descriptive name of the asset to help identify it
+ **change**: The type of change that occurred
+ **description**: Explanation of the change and the potential impact
+ **time**: A unix timestamp (in seconds)




---

### Topic Creators

https://lunarcrush.com/api4/public/topic/:topic/creators/v1

Get the top creators for a social topic

input parameters:

+ **topic**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/creators/v1
```



Example response:

```json
{
  "data": [
    {
      "creator_id": "twitter::1387497871751196672",
      "creator_name": "WatcherGuru",
      "creator_avatar": "https://pbs.twimg.com/profile_images/1641221212578754562/DfiC0KW2_200x200.png",
      "creator_followers": 3187424,
      "creator_rank": 1,
      "interactions_24h": 2996195
    }
  ]
}
```

Schema:

+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_avatar**: The URL to the avatar for the creator
+ **creator_followers**: number of followers the account has
+ **creator_rank**: ranking based on all posts in the last 24 hours that have interactions
+ **interactions_24h**: Number of interactions in the last 24 hours




---

### Topic News

https://lunarcrush.com/api4/public/topic/:topic/news/v1

Get the top news posts for a social topic. Top news is determined by the metrics related to the social posts that mention the news posts.

input parameters:

+ **topic**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/news/v1
```



Example response:

```json
{
  "config": {
    "topic": "bitcoin",
    "type": "topic",
    "id": "bitcoin",
    "name": "Bitcoin",
    "symbol": "BTC",
    "generated": 1749549546
  },
  "data": [
    {
      "id": "cointelegraph.com-2901968711",
      "post_type": "news",
      "post_title": "Bitcoin Lacks Catalyst to Beat ATH",
      "post_link": "https://cointelegraph.com/news/bitcoin-price-lacks-fuel-surpass-all-time-high",
      "post_image": "https://images.cointelegraph.com/cdn-cgi/image/format=auto,onerror=redirect,quality=90,width=1200/https://s3.cointelegraph.com/uploads/2025-03/0195d29a-2eba-7295-9acc-9502e4daf4a4",
      "post_created": 1749541786,
      "post_sentiment": 2.84,
      "creator_id": "twitter::2207129125",
      "creator_name": "Cointelegraph",
      "creator_display_name": "Cointelegraph",
      "creator_followers": 2744300,
      "creator_avatar": "https://pbs.twimg.com/profile_images/1755983593925378048/kYutau0B_200x200.jpg",
      "interactions_24h": 3,
      "interactions_total": 3
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **post_type**: The type of social post
+ **post_title**: The title text of the social post
+ **post_link**: The URL to view the social post on the social network
+ **post_image**: The URL to the primary image for the post if available
+ **post_created**: The unix timestamp of our best indication of when the post was created
+ **post_sentiment**: The sentiment of the post is a score between 1 and 5 with 1 being very negative, 3 being neutral, and 5 being very positive. A score of 3.5 is considered slightly positive.
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_followers**: number of followers the account has
+ **creator_avatar**: The URL to the avatar for the creator
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **interactions_total**: Number of total interactions




---

### Topic Posts

https://lunarcrush.com/api4/public/topic/:topic/posts/v1

Get the top posts for a social topic. If start time is provided the result will be the top posts by interactions for the time range. If start is not provided it will be the most recent top posts by interactions from the last 24 hours.

input parameters:

+ **topic**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**
+ **start**: _The start time (unix timestamp) to start at. Will be rounded to the beginning of the day. If the end parameter is not provided it will just be the top posts for this day._ 
+ **end**: _(Optional) The end time (unix timestamp) to stop at. Will be rounded to the end of the day._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/posts/v1
```



Example response:

```json
{
  "config": {
    "topic": "bitcoin",
    "type": "topic",
    "id": "bitcoin",
    "name": "Bitcoin",
    "symbol": "BTC",
    "generated": 1749549546
  },
  "data": [
    {
      "id": "1932361541258723504",
      "post_type": "tweet",
      "post_title": "ðŸ’¥BREAKING:\n\nBITCOIN SETS A NEW ALL-TIME HIGH IN ARGENTINA. \n\nFIAT IS COLLAPSING.",
      "post_link": "https://x.com/rovercrc/status/1932361541258723504",
      "post_image": "https://pbs.twimg.com/media/GtEgg1MXIAA8EWa.jpg",
      "post_created": 1749545867,
      "post_sentiment": 2.76,
      "creator_id": "twitter::1353384573435056128",
      "creator_name": "rovercrc",
      "creator_display_name": "Crypto Rover",
      "creator_followers": 1248515,
      "creator_avatar": "https://pbs.twimg.com/profile_images/1891433835675475969/J-TloTb6_200x200.png",
      "interactions_24h": 19752,
      "interactions_total": 19752
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **type**: Type of item or social network of item e.g. tweet, youtube-video, tiktok, x, youtube, category, topic, creator/influencer
+ **id**: Unique id of the social post
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **post_type**: The type of social post
+ **post_title**: The title text of the social post
+ **post_link**: The URL to view the social post on the social network
+ **post_image**: The URL to the primary image for the post if available
+ **post_created**: The unix timestamp of our best indication of when the post was created
+ **post_sentiment**: The sentiment of the post is a score between 1 and 5 with 1 being very negative, 3 being neutral, and 5 being very positive. A score of 3.5 is considered slightly positive.
+ **creator_id**: The [network]::[unique_id] for the influencer
+ **creator_name**: The unique screen name for the influencer
+ **creator_display_name**: The chosen display name for the influencer if available
+ **creator_followers**: number of followers the account has
+ **creator_avatar**: The URL to the avatar for the creator
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **interactions_total**: Number of total interactions




---

### Topic Time Series

https://lunarcrush.com/api4/public/topic/:topic/time-series/v1

Get historical time series data for a social topic

input parameters:

+ **topic**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**
+ **bucket**: _bucket time series data into hours or days. default is hours._ 
+ **interval**: _Use interval to specify the start and end time automatically for convenience. If "start" or "end" parameters are provided this parameter is ignored._ 
+ **start**: _The start time (unix timestamp) to go back to._ 
+ **end**: _The end time (unix timestamp) to stop at._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/time-series/v1
```



Example response:

```json
{
  "config": {
    "topic": "bitcoin",
    "id": "bitcoin",
    "name": "Bitcoin",
    "symbol": "BTC",
    "interval": "1w",
    "start": 1748908800,
    "end": 1749556746,
    "bucket": "hour",
    "metrics": [],
    "generated": 1749549546
  },
  "data": [
    {
      "time": 1748908800,
      "contributors_active": 16137,
      "contributors_created": 817,
      "interactions": 4624855,
      "posts_active": 31376,
      "posts_created": 1012,
      "sentiment": 79,
      "spam": 189,
      "alt_rank": 280,
      "circulating_supply": 19873625,
      "close": 106296,
      "galaxy_score": 73,
      "high": 106296,
      "low": 105798.67,
      "market_cap": 2112336724550,
      "market_dominance": 63.5842,
      "open": 105888.47,
      "social_dominance": 21.6609,
      "volume_24h": 47303569104
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **bucket**: Data is generally bucketed into hours or days
+ **metrics**: Comma separated list of metrics to include or that are included
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **contributors_active**: number of unique social accounts with posts that have interactions
+ **contributors_created**: number of unique social accounts that created new posts
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **posts_active**: number of unique social posts with interactions
+ **posts_created**: number of unique social posts created
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **spam**: The number of posts created that are considered spam
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **circulating_supply**: Circulating Supply is the total number of coins or tokens that are actively available for trade and are being used in the market and in general public
+ **close**: Close price for the time period
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **high**: Higest price fo rthe time period
+ **low**: Lowest price for the time period
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **open**: Open price for the time period
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **volume_24h**: Volume in USD for 24 hours up to this data point




---

### Topic Time Series v2

https://lunarcrush.com/api4/public/topic/:topic/time-series/v2

Get historical time series data for a social topic

input parameters:

+ **topic**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**
+ **bucket**: _Leave blank (default) for the most week aggregated by hour, specify hour for full historical data available in hourly aggregation, specify day for full historical data available in daily aggregation._ 

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/time-series/v2
```



Example response:

```json
{
  "config": {
    "topic": "bitcoin",
    "id": "bitcoin",
    "name": "Bitcoin",
    "symbol": "BTC",
    "interval": "1w",
    "start": 1748908800,
    "end": 1749556746,
    "bucket": "hour",
    "metrics": [],
    "generated": 1749549546
  },
  "data": [
    {
      "time": 1748908800,
      "contributors_active": 16137,
      "contributors_created": 817,
      "interactions": 4624855,
      "posts_active": 31376,
      "posts_created": 1012,
      "sentiment": 79,
      "spam": 189,
      "alt_rank": 280,
      "circulating_supply": 19873625,
      "close": 106296,
      "galaxy_score": 73,
      "high": 106296,
      "low": 105798.67,
      "market_cap": 2112336724550,
      "market_dominance": 63.5842,
      "open": 105888.47,
      "social_dominance": 21.6609,
      "volume_24h": 47303569104
    }
  ]
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **interval**: Typically used for specifying time intervals like 1w = 1 week, 1m = 1 month etc
+ **start**: Start/from unix timestamp (in seconds)
+ **end**: End/to unix timestamp (in seconds)
+ **bucket**: Data is generally bucketed into hours or days
+ **metrics**: Comma separated list of metrics to include or that are included
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **time**: A unix timestamp (in seconds)
+ **contributors_active**: number of unique social accounts with posts that have interactions
+ **contributors_created**: number of unique social accounts that created new posts
+ **interactions**: number of all publicly measurable interactions on a social post (views, likes, comments, thumbs up, upvote, share etc)
+ **posts_active**: number of unique social posts with interactions
+ **posts_created**: number of unique social posts created
+ **sentiment**: % of posts (weighted by interactions) that are positive. 100% means all posts are positive, 50% is half positive and half negative, and 0% is all negative posts.
+ **spam**: The number of posts created that are considered spam
+ **alt_rank**: A proprietary score based on how an asset is performing relative to all other assets supported
+ **circulating_supply**: Circulating Supply is the total number of coins or tokens that are actively available for trade and are being used in the market and in general public
+ **close**: Close price for the time period
+ **galaxy_score**: A proprietary score based on technical indicators of price, average social sentiment, relative social activity, and a factor of how closely social indicators correlate with price and volume
+ **high**: Higest price fo rthe time period
+ **low**: Lowest price for the time period
+ **market_cap**: Total dollar market value of all circulating supply or outstanding shares
+ **market_dominance**: The percent of the total market cap that this asset represents
+ **open**: Open price for the time period
+ **social_dominance**: The percent of the total social volume that this topic represents
+ **volume_24h**: Volume in USD for 24 hours up to this data point




---

### Topic

https://lunarcrush.com/api4/public/topic/:topic/v1

Get summary information for a social topic. The output is a 24 hour aggregation social activity with metrics comparing the latest 24 hours to the previous 24 hours.

input parameters:

+ **topic**: _Provide the topic to get details for. A topic must be all lower case and can only include letters, numbers, spaces, # and $. You can also look up a topic by the coin/nft/stock numeric id like coins:1 for bitcoin or stocks:7056 for nVidia._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/v1
```



Example response:

```json
{
  "config": {
    "id": "bitcoin",
    "name": "Bitcoin",
    "symbol": "BTC",
    "topic": "bitcoin",
    "generated": 1749549546
  },
  "data": {
    "topic": "bitcoin",
    "title": "Bitcoin",
    "topic_rank": 44,
    "related_topics": [
      "coins layer 1"
    ],
    "types_count": {
      "youtube-video": 29407,
      "tweet": 102143,
      "reddit-post": 8356,
      "tiktok-video": 12022,
      "news": 585
    },
    "types_interactions": {
      "youtube-video": 11429561,
      "tweet": 75842866,
      "reddit-post": 190100,
      "tiktok-video": 9108052,
      "news": 172778
    },
    "types_sentiment": {
      "youtube-video": 80,
      "tweet": 82,
      "reddit-post": 77,
      "tiktok-video": 55,
      "news": 73
    },
    "types_sentiment_detail": {
      "youtube-video": {
        "positive": 4652662,
        "neutral": 5825469,
        "negative": 951430
      },
      "tweet": {
        "positive": 36206191,
        "neutral": 32199766,
        "negative": 7436909
      },
      "reddit-post": {
        "positive": 58176,
        "neutral": 116993,
        "negative": 14931
      },
      "tiktok-video": {
        "positive": 1420061,
        "neutral": 5402674,
        "negative": 2285317
      },
      "news": {
        "positive": 61732,
        "neutral": 96178,
        "negative": 14868
      }
    },
    "interactions_24h": 96743357,
    "num_contributors": 58144,
    "num_posts": 152513,
    "categories": [
      "Cryptocurrencies"
    ],
    "trend": "flat"
  }
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **id**: LunarCrush internal ID for the asset
+ **name**: The full name of the asset
+ **symbol**: The symbol for the asset
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data
+ **title**: The case sensitive title of the topic or category
+ **topic_rank**: LunarCrush metric for ranking a social topic relative to all other social topics
+ **related_topics**: an array of related topics
+ **types_count**: An object with the counts of the total number of unique posts getting interactions from each social network in the last 24 hours
+ **types_interactions**: An object with the counts of the total number of interactions on each post from each social network in the last 24 hours
+ **types_sentiment**: An object with the sentiment score broken down by each supported social network. 0% is all posts negative, 100% is all posts positive. 50% is equal positive and negative posts. Each post is weighted by interactions.
+ **types_sentiment_detail**: An object with the breakdown of positive, neutral, and negative posts by 24h interactions for each social network
+ **interactions_24h**: Number of interactions in the last 24 hours
+ **num_contributors**: The number of unique social contributors to the topic
+ **num_posts**: Total number of posts with interactions on this topic in the last 24 hours
+ **categories**: an array of categories this topic aggregates into
+ **trend**: One of up, down or flat to represent the general trend in interactions




---

### Topic Whatsup

https://lunarcrush.com/api4/public/topic/:topic/whatsup/v1

Generate an AI summary of the hottest news and social posts for a specific topic

input parameters:

+ **topic**: _Provide the topic to get a summary for. A topic must be all lower case and can only include letters, numbers, spaces, # and $._ **required**

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topic/bitcoin/whatsup/v1
```



Example response:

```json
{
  "config": {
    "topic": "bitcoin",
    "generated": 1749549381
  },
  "summary": "Several major companies, including BlackRock, Strategy, and Kurl Technology, are increasing their Bitcoin holdings, with BlackRock's iShares Bitcoin Trust reaching $70 billion in assets under management in just 341 days. Additionally, SEC Chair Gary Gensler is championing self-custody rights, which could fuel a crypto boom. Meanwhile, institutional adoption is growing, with companies like Metaplanet and Anap Holdings announcing plans to invest in Bitcoin."
}
```

Schema:

+ **config**: This includes the inputs for the request processed by the server and may include additional hints about the request and response information.
+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **generated**: A unix timestamp (in seconds) when the data was generated to understand possibly stale data




---

### Topics List

https://lunarcrush.com/api4/public/topics/list/v1

Get a list of trending social topics.

Example request:

```bash
curl -H "Authorization: Bearer <API_KEY>" https://lunarcrush.com/api4/public/topics/list/v1
```



Example response:

```json
{
  "data": [
    {
      "topic": "youtube",
      "title": "YouTube",
      "topic_rank": 1,
      "topic_rank_1h_previous": 1,
      "topic_rank_24h_previous": 1,
      "num_contributors": 309855,
      "num_posts": 615752,
      "interactions_24h": 2889316572
    }
  ]
}
```

Schema:

+ **topic**: LunarCrush social topic. Can only includes letters, numbers, spaces, #, and $
+ **title**: The case sensitive title of the topic or category
+ **topic_rank**: LunarCrush metric for ranking a social topic relative to all other social topics
+ **topic_rank_1h_previous**: The topic rank from 1 hour ago
+ **topic_rank_24h_previous**: The topic rank from 24 hours ago
+ **num_contributors**: The number of unique social contributors to the topic
+ **num_posts**: Total number of posts with interactions on this topic in the last 24 hours
+ **interactions_24h**: Number of interactions in the last 24 hours

