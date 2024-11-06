# OKX COPY Trading

The **OKX Trading API** offers users comprehensive access to a wide range of trading-related data and functionalities, including trader rankings, performance metrics, position history, and more. This API is ideal for developers building financial applications that require insights into trading behaviors, risk management, or performance tracking.

With intuitive endpoints and real-time data access, the **OKX Trading API** enables users to seamlessly retrieve and analyze up-to-date trading information. The API delivers structured JSON responses, facilitating easy integration into various platforms and data workflows for enhanced automation and streamlined analysis.

# Authentication
The URL you need to use is the following: `https://okx-copy-trading1.p.rapidapi.com/`
The API requires the headers listed below:

 - **`x-rapidapi-host`**: `okx-copy-trading1.p.rapidapi.com`
 - **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/okx-copy-trading1/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

# Endpoints
The API is configured to accept only **GET** requests. Below are the available endpoints with their descriptions and required parameters.

### **Trader**

#### 1. **`GET /trader/unique-name`**
-   **Description**: Retrieves a list of unique trader names.

-   **Parameters**:

| Parameter        | Type     | Default               | Description     | Required |
|------------------|----------|-----------------------|-----------------|----------|
| `page`      | string   | `1`  | The page number for pagination         | No     |
| `perPage`  | string   | `9`| Number of results per page   | No       |
	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/unique-name?perPage=1', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response (JSON object containing a list of unique trader names):
```json
{
  "pages": 8667,
  "total": 8667,
  "data": [
    {
      "uniqueName": "7B17F2000A241F78",
      "nickName": "Stable income",
      "portrait": "https://www.okx.com/cdn/okex/users/headimages/20240329/7ec0ecaa8c1b4bd28197b25a169f3919",
      "followerNum": "50"
    }
  ]
}
```

#### 2. **`GET /trader/search`**
-   **Description**: This endpoint allows users to search for traders based on certain filters such as win ratio, assets under management (AUM), trader's performance period and much more.

- **Parameters**

| Parameter        | Type     | Default               | Description     | Required |
|------------------|----------|-----------------------|-----------------|----------|
| `page`      | string   | `1`  | The page number for pagination.         | Yes      |
| `winRatio`  | string   | `0.5`| Minimum win ratio for filtering traders (range: 0.5 - 0.9).   | No       |
| `aumHigh`        | string   | `358849`            | Maximum assets under management (AUM)  | No       |
| `assetsLow`      | string   | `9762`              | Minimum assets   | No       |
| `assetsHigh`     | string   | `40661`             | Maximum assets   | No       |
| `traderPeriod`   | string   | `30`                | The period in days to filter traders by their activity. Options: 7, 30, 90, 180, null   | No       |
| `type`           | string   | `'1'`                 | The type of filter to apply. Available options: '1' (None), '2' (yieldRatio), '3' (pnl), '4' (winRatio), '5' (aum), '6' (traderFollowerLimit), '7' (followTotalPnl) | No   
| `pnlPercentage`  | integer  | `-`   | The percentage of profit and loss (PnL) for filtering traders.     | Yes      |
| `followerNum`    | integer  | `-`                 | The number of followers for filtering traders.   | Yes      |
| `profitDays`     | integer  | `-`                 | The number of profitable days for filtering traders.   | Yes      |
| `lossDays`       | integer  | `-`                 | The number of loss days for filtering traders.    | Yes      |
| `traderLevel`    | integer  | `-`                 | The level of the trader for filtering.     | Yes      |
| `profitLossRatio`| integer  | `-`                 | The ratio of profit to loss for filtering traders.    | Yes      |

- **Type Option**

| Value | Description                     |
|-------|---------------------------------|
| `1` | No sorting (default)           |
| `2` | Sort by yield ratio            |
| `3` | Sort by PNL                    |
| `4` | Sort by win ratio              |
| `5` | Sort by AUM                    |
| `6` | Sort by trader follower limit   |
| `7` | Sort by follow total PNL       |

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/search?page=1&winRatio=0.5&type=1', {
    method: 'GET',
    headers: {
      'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:
```json
[
  {
    "uniqueName": "7B17F2000A241F78",
    "nickName": "Stable income",
    "portrait": "https://www.okx.com/cdn/okex/users/headimages/20240329/7ec0ecaa8c1b4bd28197b25a169f3919",
    "followerNum": "50",
    "aum": "99009.2948457482470559",
    "channel": 0,
    "copyRelId": "",
    "emptyMinderState": "0",
    "followPnl": "43535.9436973363225799",
    "followType": "0",
    "followerLimit": "50",
    "historyFollowerNum": "167",
    "initialDay": "214",
    "instruments": [
      {
        "instId": "BTC-USDT-SWAP",
        "name": "BTC"
      },
      {
        "instId": "ETH-USDT-SWAP",
        "name": "ETH"
      },
      {
        "instId": "DOGE-USDT-SWAP",
        "name": "DOGE"
      },
      {
        "instId": "SOL-USDT-SWAP",
        "name": "SOL"
      }
    ],
    "pnl": "16039.1542937506229497",
    "rates": [
      {
        "ratio": "0.1624",
        "statTime": "1712160000000"
      },
      ...
    ],
    "symbol": "USDT",
    "targetId": "8",
    "tier": {
      "level": "Lvl 0",
      "name": "Basic",
      "tierKey": "0"
    },
    "totalLeadInstNum": "193",
    "winRatio": "0.5556",
    "yieldRatio": "1.4218"
  },
  ...
]
```

- **Notes**
  - The endpoint uses a single `query` parameter query for the search input.
  - Error handling is implemented for missing required parameter.
  - The actual search functionality is performed by the `getSearchByName` function (implementation not shown).
  - Any errors during the search process will result in a 500 Internal Server Error response.

#### 3. **`GET /trader/week-pnl`**
-   **Description**: Retrieves the weekly profit and loss (PNL) for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/week-pnl?uniqueName=C48033C88C4E8064', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "pnl": "494.7295990681383453",
      "ratio": "0.0645",
      "statTime": "1723392000000"
    },
    {
      "pnl": "1671.9271902217629804",
      "ratio": "0.2052",
      "statTime": "1723996800000"
    },
    {
      "pnl": "-605.1163305594815357",
      "ratio": "-0.0547",
      "statTime": "1724601600000"
    },
    {
      "pnl": "127.0730000000000000",
      "ratio": "0.0116",
      "statTime": "1725206400000"
    },
    {
      "pnl": "1579.2542567302342925",
      "ratio": "0.0835",
      "statTime": "1725811200000"
    },
    {
      "pnl": "3424.0680819142929264",
      "ratio": "0.1464",
      "statTime": "1726416000000"
    },
    {
      "pnl": "-826.7479690898708366",
      "ratio": "-0.0324",
      "statTime": "1727020800000"
    },
    {
      "pnl": "310.2946684755394605",
      "ratio": "0.0126",
      "statTime": "1727625600000"
    },
    {
      "pnl": "393.0511152257395637",
      "ratio": "0.0152",
      "statTime": "1728230400000"
    },
    {
      "pnl": "1891.2391830931401935",
      "ratio": "0.0776",
      "statTime": "1728835200000"
    },
    {
      "pnl": "4925.8675654881266767",
      "ratio": "0.1984",
      "statTime": "1729440000000"
    },
    {
      "pnl": "-579.4893938722066724",
      "ratio": "-0.0183",
      "statTime": "1730044800000"
    }
  ],
  "msg": ""
}
```

#### 4. **`GET /trader/yield-pnl`**
-   **Description**: Retrieves the yield profit and loss (PNL) for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `latestNum` | string | `90` | Number of latest data points to retrieve | No |
	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/yield-pnl?uniqueName=C48033C88C4E8064', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "pnl": "0",
      "ratio": "0.0",
      "statTime": "1722355200000"
    },
    {
      "pnl": "215.3788475337581886",
      "ratio": "0.0127",
      "statTime": "1722441600000"
    },
    {
      "pnl": "-51.3284524662418274",
      "ratio": "-0.003",
      "statTime": "1722528000000"
    },
    {
      "pnl": "774.4711801406565400",
      "ratio": "0.0457",
      "statTime": "1722614400000"
    },
    {
      "pnl": "1176.8929379550750030",
      "ratio": "0.0694",
      "statTime": "1722700800000"
    },
    {
      "pnl": "1062.7380901486691011",
      "ratio": "0.0627",
      "statTime": "1722787200000"
    },
    ...
  ],
  "msg": ""
}
```

#### 5. **`GET /trader/follower-list`**
-   **Description**: Retrieves the list of followers for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/follower-list?uniqueName=C48033C88C4E8064', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "followers": [
        {
          "aum": "16533.687224418605183",
          "coinSymbol": "USDT",
          "followDays": "88",
          "followTime": "1722667268000",
          "investedAmount": "",
          "nickName": "883***@qq.com",
          "pnl": "7629.1651365917691935",
          "portrait": "",
          "profitSharingRatio": "",
          "targetId": "0",
          "uid": "",
          "uniqueName": "3DFD6D97F63A4FE0"
        },
        {
          "aum": "5479.6104499931470855",
          "coinSymbol": "USDT",
          "followDays": "144",
          "followTime": "1717835579000",
          "investedAmount": "",
          "nickName": "cvcv_v50",
          "pnl": "4384.763135260525803",
          "portrait": "",
          "profitSharingRatio": "",
          "targetId": "0",
          "uid": "",
          "uniqueName": "A8F377B51D19874C"
        },
        {
          "aum": "34254.2634389066297445",
          "coinSymbol": "USDT",
          "followDays": "35",
          "followTime": "1727250344000",
          "investedAmount": "",
          "nickName": "138***9900",
          "pnl": "2606.2208322525081018",
          "portrait": "",
          "profitSharingRatio": "",
          "targetId": "0",
          "uid": "",
          "uniqueName": "EC29B627261C9192"
        },
        {
          "aum": "2379.7146788795944303",
          "coinSymbol": "USDT",
          "followDays": "98",
          "followTime": "1721804170000",
          "investedAmount": "",
          "nickName": "7RUNKS",
          "pnl": "1579.6649998642625428",
          "portrait": "https://static.coinall.ltd/cdn/okex/users/headimages/20240209/ff1f659d000a43bf803ff7a9efe9b2b9",
          "profitSharingRatio": "",
          "targetId": "4",
          "uid": "",
          "uniqueName": "621F19A00AF497ED"
        },
        {
          "aum": "800",
          "coinSymbol": "USDT",
          "followDays": "56",
          "followTime": "1725411043000",
          "investedAmount": "",
          "nickName": "梦幻泡影",
          "pnl": "1467.8616644725014217",
          "portrait": "",
          "profitSharingRatio": "",
          "targetId": "6",
          "uid": "",
          "uniqueName": "6A8997E6C3222B92"
        }
      ],
      "pnlCoinSymbol": "USDT",
      "sevenDaysFollowerFlag": "1",
      "sevenDaysFollowerNum": "28",
      "sevenDaysFollowerRatio": "0.0737",
      "sevenDaysFollowerRatioFlag": "1",
      "statTime": "1730131199000",
      "totalFollowerNum": "408",
      "totalFollowerPnl": "29125.4644467966992185"
    }
  ],
  "msg": ""
}
```

#### 6. **`GET /trader/preference-coin`**
-   **Description**: Retrieves the preferred coins for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |


Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/preference-coin?uniqueName=C48033C88C4E8064', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "currency": "other",
      "percent": "0.4839"
    },
    {
      "currency": "OM",
      "percent": "0.1562"
    },
    {
      "currency": "SUI",
      "percent": "0.0971"
    },
    {
      "currency": "SOL",
      "percent": "0.0895"
    },
    {
      "currency": "ETHFI",
      "percent": "0.0895"
    },
    {
      "currency": "ZRO",
      "percent": "0.0838"
    }
  ],
  "msg": ""
}
```

#### 7. **`GET /trader/position-history-scatter`**
-   **Description**: Retrieves the position history scatter plot data for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `period` | string | `30D` | Time period for the data | Yes |
	

Example request:
```javascript
fetch('', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "itemScatterList": [
        {
          "closePnl": "24.6993",
          "holdTimeMS": "3651113"
        },
        {
          "closePnl": "24.7584",
          "holdTimeMS": "3672735"
        },
        {
          "closePnl": "24.6705",
          "holdTimeMS": "3937161"
        },
        {
          "closePnl": "24.9024",
          "holdTimeMS": "5049623"
        },
        {
          "closePnl": "25.9161",
          "holdTimeMS": "9204883"
        },
        {
          "closePnl": "49.1326",
          "holdTimeMS": "31466884"
        },
        {
          "closePnl": "98.7648",
          "holdTimeMS": "35540407"
        },
        ...
      ],
      "symbol": "USDT"
    }
  ],
  "msg": ""
}

```

#### 8. **`GET /trader/position-history`**
-   **Description**: Retrieves the position history for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `size` | string | `10` | Number of history entries to retrieve | No |
	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/position-history?uniqueName=C48033C88C4E8064', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "ccy": "USDT",
      "closeAvgPx": "1.609",
      "closePnl": "24.846",
      "contractVal": "1",
      "dealVolume": "",
      "fee": "-0.687507",
      "fundingFee": "-1.1578333413941465",
      "id": "1830601028514942976",
      "instId": "SUI-USDT-SWAP",
      "instType": "SWAP",
      "lever": "10",
      "liquidationFee": "0",
      "margin": "99.99",
      "mgnMode": "cross",
      "multiplier": "1",
      "openAvgPx": "1.65",
      "openTime": "1727199790173",
      "pnl": "23.0006596586058535",
      "pnlRatio": "0.2300295995460131",
      "posSide": "short",
      "posType": "3",
      "side": "sell",
      "subPos": "606",
      "tradeItemId": "1830601028514942976",
      "type": "2",
      "uTime": "1730135225756",
      "uniqueName": "C48033C88C4E8064"
    },
    {
      "ccy": "USDT",
      "closeAvgPx": "1.6094",
      "closePnl": "12.3018",
      "contractVal": "1",
      "dealVolume": "",
      "fee": "-0.3438141",
      "fundingFee": "-0.5789166706970748",
      "id": "1823331999035232256",
      "instId": "SUI-USDT-SWAP",
      "instType": "SWAP",
      "lever": "10",
      "liquidationFee": "0",
      "margin": "49.995",
      "mgnMode": "cross",
      "multiplier": "1",
      "openAvgPx": "1.65",
      "openTime": "1727199790173",
      "pnl": "11.3790692293029252",
      "pnlRatio": "0.2276041450005586",
      "posSide": "short",
      "posType": "3",
      "side": "sell",
      "subPos": "303",
      "tradeItemId": "1823331999035232256",
      "type": "2",
      "uTime": "1730135225756",
      "uniqueName": "C48033C88C4E8064"
    },
    ...
  ],
  "msg": ""
}

```


#### 9. **`GET /trader/t-performance`**
-   **Description**: Retrieves the trading performance for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `dateRange` | string | `0` | Date range for the performance data (options: '0', '7', '30', '90') | No |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/t-performance?uniqueName=5286E5DD17588061&dateRange=7', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
[
  {
    "nonPeriodicPart": [
      {
        "desc": "Number of days this trader has been a lead trader for.",
        "functionId": "initialDay",
        "learnMoreUrl": "",
        "order": 1,
        "title": "Days leading trades",
        "type": "2",
        "value": "325"
      },
      {
        "desc": "USDT balance in lead trader’s trading account.",
        "functionId": "asset",
        "learnMoreUrl": "",
        "order": 2,
        "title": "Lead trade assets (USDT)",
        "type": "0",
        "value": "155.2670783856349"
      },
      {
        "desc": "Asset under management. Total funds allocated by copy traders.",
        "functionId": "aum",
        "learnMoreUrl": "",
        "order": 3,
        "title": "AUM",
        "type": "0",
        "value": "1344.0363900488801141"
      },
      {
        "desc": "Total copy trade PnL of all traders currently copying this lead trader.",
        "functionId": "currentFollowPnl",
        "learnMoreUrl": "",
        "order": 4,
        "title": "Current copy trader PnL (USDT)",
        "type": "0",
        "value": "-824.9539348510058451"
      },
      {
        "desc": "",
        "functionId": "followerNum",
        "learnMoreUrl": "",
        "order": 5,
        "title": "Copy traders",
        "type": "4",
        "value": "21/50"
      },
      ...
    ],
    "periodicPart": [
      {
        "desc": "",
        "functionId": "profitDays",
        "learnMoreUrl": "",
        "order": 1,
        "title": "Days w/ profit",
        "type": "2",
        "value": "3"
      },
      {
        "desc": "",
        "functionId": "lossDays",
        "learnMoreUrl": "",
        "order": 2,
        "title": "Days w/ loss",
        "type": "2",
        "value": "4"
      },
      {
        "desc": "Number of days with profit / Number of days leading trades × 100%",
        "functionId": "winRatio",
        "learnMoreUrl": "",
        "order": 3,
        "title": "Win rate",
        "type": "1",
        "value": "0.4286"
      },
      {
        "desc": "Cumulative profit of lead trader / Cumulative loss of lead trader",
        "functionId": "pnlProfitLossRatio",
        "learnMoreUrl": "",
        "order": 4,
        "title": "Profit/Loss ratio",
        "type": "3",
        "value": "0.07:1"
      },
      {
        "desc": "The average value of each lead trade position this trader has held.",
        "functionId": "avgPositionValue",
        "learnMoreUrl": "",
        "order": 5,
        "title": "Average position value",
        "type": "0",
        "value": "5286.9589"
      }
    ]
  }
]   
```

#### 10. **`GET /trader/position-summary`**
-   **Description**: Retrieves the position summary for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/position-summary?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "availSubPos": "15.3",
      "ccy": "USDT",
      "closePnl": "0",
      "dealVolume": "",
      "detailIds": "1934734138063523840",
      "fee": "-0.7956",
      "fundingFee": "0.3548753411228404",
      "imr": "199.2548753411228404",
      "instId": "ETH-USDT-SWAP",
      "instType": "SWAP",
      "last": "2633.99",
      "lever": "20",
      "liquidationFee": "0",
      "margin": "198.9",
      "markPx": "2633.97",
      "maxSellableAmount": "15.3",
      "mgnMode": "isolated",
      "notionalUsd": "4027.475516058",
      "openAvgPx": "2600",
      "openTime": "1730161970517",
      "pnl": "-51.9741",
      "pnlRatio": "-0.261307692307692",
      "posSide": "short",
      "posType": "3",
      "side": "sell",
      "subPos": "15.3",
      "tradeItemId": "1934931047677657088_0",
      "uTime": "1730188800503",
      "uniqueName": "5286E5DD17588061"
    }
  ],
  "msg": ""
}
```

#### 11. **`GET /trader/total-pnl`**
-   **Description**: Retrieves the total profit and loss (PNL) for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/total-pnl?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "ratio": "0.0",
      "statTime": "1698595200000"
    },
    {
      "ratio": "0.0",
      "statTime": "1698681600000"
    },
    {
      "ratio": "0.0",
      "statTime": "1698768000000"
    },
    {
      "ratio": "0.0",
      "statTime": "1698854400000"
    },
    {
      "ratio": "0.0",
      "statTime": "1698940800000"
    },
    {
      "ratio": "0.0",
      "statTime": "1699027200000"
    },
    {
      "ratio": "0.0",
      "statTime": "1699113600000"
    },
    {
      "ratio": "0.0",
      "statTime": "1699200000000"
    },
    {
      "ratio": "0.0",
      "statTime": "1699286400000"
    },
    {
      "ratio": "0.0",
      "statTime": "1699372800000"
    },
    {
      "ratio": "0.0105",
      "statTime": "1699459200000"
    },
    {
      "ratio": "0.0595",
      "statTime": "1699545600000"
    },
    {
      "ratio": "0.0595",
      "statTime": "1699632000000"
    },
    {
      "ratio": "0.0616",
      "statTime": "1699718400000"
    },
    {
      "ratio": "0.044",
      "statTime": "1699804800000"
    },
    {
      "ratio": "0.0213",
      "statTime": "1699891200000"
    },
    ...
      ],
  "msg": ""
}
```

#### 12. **`GET /trader/monthly-pnl`**
-   **Description**: Retrieves the monthly profit and loss (PNL) for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "ratio": "-0.016",
      "statTime": "1698768000000"
    },
    {
      "ratio": "0.7462",
      "statTime": "1701360000000"
    },
    {
      "ratio": "0.0886",
      "statTime": "1704038400000"
    },
    {
      "ratio": "1.7388",
      "statTime": "1706716800000"
    },
    {
      "ratio": "-0.2664",
      "statTime": "1709222400000"
    },
    {
      "ratio": "-0.7343",
      "statTime": "1711900800000"
    },
    {
      "ratio": "-0.8492",
      "statTime": "1714492800000"
    },
    {
      "ratio": "-0.3557",
      "statTime": "1717171200000"
    },
    {
      "ratio": "0.5953",
      "statTime": "1719763200000"
    },
    {
      "ratio": "-0.5924",
      "statTime": "1722441600000"
    },
    {
      "ratio": "-0.6252",
      "statTime": "1725120000000"
    },
    {
      "ratio": "-0.7207",
      "statTime": "1727712000000"
    }
  ],
  "msg": ""
}
```

#### 13. **`GET /trader/risk-level`**
-   **Description**: Retrieves the risk level for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/monthly-pnl?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "ratio": "-0.016",
      "statTime": "1698768000000"
    },
    {
      "ratio": "0.7462",
      "statTime": "1701360000000"
    },
    {
      "ratio": "0.0886",
      "statTime": "1704038400000"
    },
    {
      "ratio": "1.7388",
      "statTime": "1706716800000"
    },
    {
      "ratio": "-0.2664",
      "statTime": "1709222400000"
    },
    {
      "ratio": "-0.7343",
      "statTime": "1711900800000"
    },
    {
      "ratio": "-0.8492",
      "statTime": "1714492800000"
    },
    {
      "ratio": "-0.3557",
      "statTime": "1717171200000"
    },
    {
      "ratio": "0.5953",
      "statTime": "1719763200000"
    },
    {
      "ratio": "-0.5924",
      "statTime": "1722441600000"
    },
    {
      "ratio": "-0.6252",
      "statTime": "1725120000000"
    },
    {
      "ratio": "-0.7207",
      "statTime": "1727712000000"
    }
  ],
  "msg": ""
}
```

#### 14. **`GET /trader/max-drawdown`**
-   **Description**: Retrieves the maximum drawdown for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/max-drawdown?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "dayMaxDrawdown": "-1.0",
      "historyMaxDrawdown": "-1.0",
      "weekMaxDrawdown": "-1.0"
    }
  ],
  "msg": ""
}
```

#### 15. **`GET /trader/asset`**
-   **Description**: Retrieves the asset information for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/asset?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "currency": "USDT",
      "percent": "0.9997"
    },
    {
      "currency": "EOS",
      "percent": "0.0003"
    }
  ],
  "msg": ""
}
```

#### 16. **`GET /trader/trade-records`**
-   **Description**: Retrieves the trade records for a specific trader within a given time range.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `limit` | string | `5` | Number of records to retrieve | No |
| `startTime` | string | `-` |Start time for the records (format: 'DD/MM/YYYY') | No |
| `endTime` | string | `-` | End time for the records (format: 'DD/MM/YYYY') | No |

	
Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/trade-records?uniqueName=5286E5DD17588061&limit=1&startTime=12%2F01%2F2024&endTime=12%2F08%2F2024', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "alias": "",
      "avgPx": "59000",
      "baseName": "BTC",
      "cTime": "1723131070352",
      "fillTime": "1723131142594",
      "instFamily": "BTC-USDT",
      "instId": "BTC-USDT-SWAP",
      "instType": "SWAP",
      "lever": "20.0",
      "nickName": "Kobe13",
      "ordId": "1698816276605140992",
      "ordType": "limit",
      "posSide": "short",
      "px": "59000",
      "quoteName": "USDT",
      "side": "sell",
      "uTime": "1723131142595",
      "uly": "BTC-USDT",
      "uniqueName": "5286E5DD17588061"
    }
  ],
  "msg": ""
}
```

#### 17. **`GET /trader/positionv2`**
-   **Description**: Retrieves the positions for a specific trader using version 2 of the endpoint.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `limit` | string | `10` | Number of positions to retrieve | No |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/positionv2?uniqueName=5286E5DD17588061&limit=1', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [
    {
      "longLever": "",
      "posData": [
        {
          "alias": "",
          "avgPx": "2600",
          "cTime": "1730167838880",
          "instId": "ETH-USDT-SWAP",
          "instType": "SWAP",
          "lever": "20",
          "liqPx": "2717.9909404354407",
          "mgnMode": "isolated",
          "pos": "1",
          "posCcy": "",
          "posSide": "short",
          "posSpace": "23.3428795479083772",
          "uplRatio": "-0.2173076923076911"
        }
      ],
      "shortLever": "23.34"
    }
  ],
  "msg": ""
}
```

#### 18. **`GET /trader/bots`**
-   **Description**: Retrieves the trading bots for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |

	
Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/bots?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [],
  "msg": ""
}
```

#### 19. **`GET /trader/bot-history`**
-   **Description**:Retrieves the trading bot history for a specific trader.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `uniqueName` | string | `-` | Unique identifier for the trader | Yes |
| `limit` | string | `10` | Number of history entries to retrieve | No |

	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/bot-history?uniqueName=5286E5DD17588061', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "code": "0",
  "data": [],
  "msg": ""
}
```

#### 20. **`GET /trader/searchby-name`**
-   **Description**: This endpoint allows searching for traders by name.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `query` | string | `-` | The search query (trader name) | Yes |


Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/trader/searchby-name?query=7A26AF50E89FAF5E', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
{
  "data": {
    "defiCoins": [],
    "social": [
      {
        "aum": "92647.79",
        "defaultHeadPictureId": "8",
        "headPicture": "https://static.coinall.ltd/cdn/okex/users/headimages/20240329/7ec0ecaa8c1b4bd28197b25a169f3919",
        "incomeRate": "1.6931",
        "jumpParam": "7B17F2000A241F78",
        "nickNameCn": "长期稳定收益",
        "nickNameEn": "Stable income",
        "pnl": "19099.15",
        "type": 1
      }
    ],
    "tradingBot": []
  }
}
```

### **Rank**

#### 1. **`GET /rank`**
-   **Description**: Retrieves the follow rank for traders.
- **Parameters**

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `limit` | string | `10` | Number of results to return | No |
| `page` | string | `1` | Page number for pagination | No |
| `traderPeriod` | string | `7` | Trading period in days (Values: `7`, `30`,`90`... (as in days. example `30`, corresponding to 30 days)) | No |
	

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/rank/', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
[
  {
    "dataVersion": "20241029190000",
    "pages": 827,
    "ranks": [
      {
        "apiTrader": "0",
        "aum": "99009.2948457482470559",
        "channel": 0,
        "copyRelId": "",
        "emptyMinderState": "0",
        "followPnl": "43535.9436973363225799",
        "followType": "0",
        "followerLimit": "50",
        "followerNum": "50",
        "fullStatus": true,
        "hasAffiliateInvitee": false,
        "historyFollowerNum": "167",
        "initialDay": "214",
        "instruments": [
          {
            "instId": "BTC-USDT-SWAP",
            "name": "BTC"
          },
          {
            "instId": "ETH-USDT-SWAP",
            "name": "ETH"
          },
          {
            "instId": "DOGE-USDT-SWAP",
            "name": "DOGE"
          },
          {
            "instId": "SOL-USDT-SWAP",
            "name": "SOL"
          },
          ...
        ],
        "isAffiliateInvitee": false,
        "nickName": "Stable income",
        "pnl": "20750.4417750012077645",
        "portrait": "https://www.okx.com/cdn/okex/users/headimages/20240329/7ec0ecaa8c1b4bd28197b25a169f3919",
        "rates": [
          {
            "ratio": "0.0",
            "statTime": "1722355200000"
          },
          {
            "ratio": "-0.0572",
            "statTime": "1722787200000"
          },
          {
            "ratio": "0.0716",
            "statTime": "1723219200000"
          },
          ...
        ],
        "symbol": "USDT",
        "targetId": "8",
        "tier": {
          "level": "Lvl 0",
          "name": "Basic",
          "tierKey": "0"
        },
        "totalLeadInstNum": "193",
        "uniqueName": "7B17F2000A241F78",
        "winRatio": "0.5556",
        "yieldRatio": "1.8395"
      },
      ...
    ],
    "total": 8265
  }
]
```


#### 2. **`GET /rank-win-ratio`**
-   **Description**: Retrieves the follow rank based on win ratio.

-   **Parameters**:

| Parameter         | Type    | Default   | Description                                                                 | Required |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|----------|
| `limit` | string | `10` | Number of results to return | No |
| `page` | string | `1` | Page number for pagination | No |

Example request:
```javascript
fetch('https://okx-copy-trading1.p.rapidapi.com/rank-win-ratio', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'okx-copy-trading1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
Example response:
```json
[
  {
    "dataVersion": "20241029190000",
    "pages": 239,
    "ranks": [
      {
        "apiTrader": "0",
        "aum": "189513.1100922831081484",
        "channel": 0,
        "copyRelId": "",
        "emptyMinderState": "0",
        "followPnl": "2179.1887121220790667",
        "followType": "0",
        "followerLimit": "300",
        "followerNum": "277",
        "fullStatus": false,
        "hasAffiliateInvitee": false,
        "historyFollowerNum": "978",
        "initialDay": "41",
        "instruments": [
          {
            "instId": "BTC-USDT-SWAP",
            "name": "BTC"
          },
          {
            "instId": "ETH-USDT-SWAP",
            "name": "ETH"
          },
          {
            "instId": "DOGE-USDT-SWAP",
            "name": "DOGE"
          },
          {
            "instId": "SOL-USDT-SWAP",
            "name": "SOL"
          },
          ...
        ],
        "isAffiliateInvitee": false,
        "nickName": "Forked-Rig-Wasabi",
        "pnl": "18846.3914662447903944",
        "portrait": "https://www.okx.com/cdn/okex/users/headimages/20240918/19d5c68e70ac4d5c96e3898115a184bf",
        "rates": [
          {
            "ratio": "0.1771",
            "statTime": "1726675200000"
          },
          {
            "ratio": "0.6791",
            "statTime": "1726848000000"
          },
          {
            "ratio": "1.1731",
            "statTime": "1727020800000"
          },
          {
            "ratio": "1.1769",
            "statTime": "1727193600000"
          },
          ...
        ],
        "symbol": "USDT",
        "targetId": "9",
        "tier": {
          "level": "Lvl 1",
          "name": "Bronze",
          "tierKey": "1"
        },
        "totalLeadInstNum": "193",
        "uniqueName": "FEC7FB0AC101A831",
        "winRatio": "1",
        "yieldRatio": "1.2819"
      }
    ],
    "total": 239
  }
]
```


# Notes
- The `uniqueName` parameter is frequently used and typically looks like this: `5286E5DD17588061`.
- Some endpoints have default values for optional parameters. It's recommended to review the endpoint details for specific default values.
- Date formats may vary between endpoints. Always check the specific endpoint documentation for the correct date format.


## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |
