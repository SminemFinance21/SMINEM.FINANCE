# `SmindexPancakeswapV2Oracle`





# Functions:
- [`constructor(address uniswapFactory, address wBNB)`](#SmindexPancakeswapV2Oracle-constructor-address-address-)
- [`updatePrice(address token)`](#SmindexPancakeswapV2Oracle-updatePrice-address-)
- [`updatePrices(address[] tokens)`](#SmindexPancakeswapV2Oracle-updatePrices-address---)
- [`hasPriceObservationInWindow(address token, uint256 priceKey)`](#SmindexPancakeswapV2Oracle-hasPriceObservationInWindow-address-uint256-)
- [`getPriceObservationInWindow(address token, uint256 priceKey)`](#SmindexPancakeswapV2Oracle-getPriceObservationInWindow-address-uint256-)
- [`getPriceObservationsInRange(address token, uint256 timeFrom, uint256 timeTo)`](#SmindexPancakeswapV2Oracle-getPriceObservationsInRange-address-uint256-uint256-)
- [`canUpdatePrice(address token)`](#SmindexPancakeswapV2Oracle-canUpdatePrice-address-)
- [`canUpdatePrices(address[] tokens)`](#SmindexPancakeswapV2Oracle-canUpdatePrices-address---)
- [`computeTwoWayAveragePrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeTwoWayAveragePrice-address-uint256-uint256-)
- [`computeAverageTokenPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageTokenPrice-address-uint256-uint256-)
- [`computeAverageBNBPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageBNBPrice-address-uint256-uint256-)
- [`computeTwoWayAveragePrices(address[] tokens, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeTwoWayAveragePrices-address---uint256-uint256-)
- [`computeAverageTokenPrices(address[] tokens, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageTokenPrices-address---uint256-uint256-)
- [`computeAverageBNBPrices(address[] tokens, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageBNBPrices-address---uint256-uint256-)
- [`computeAverageBNBForTokens(address token, uint256 tokenAmount, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageBNBForTokens-address-uint256-uint256-uint256-)
- [`computeAverageTokensForBNB(address token, uint256 wBNBAmount, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageTokensForBNB-address-uint256-uint256-uint256-)
- [`computeAverageBNBForTokens(address[] tokens, uint256[] tokenAmounts, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageBNBForTokens-address---uint256---uint256-uint256-)
- [`computeAverageTokensForBNB(address[] tokens, uint256[] wBNBAmounts, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-computeAverageTokensForBNB-address---uint256---uint256-uint256-)
- [`_getTwoWayPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-_getTwoWayPrice-address-uint256-uint256-)
- [`_getTokenPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-_getTokenPrice-address-uint256-uint256-)
- [`_getBNBPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPancakeswapV2Oracle-_getBNBPrice-address-uint256-uint256-)

## <a id='SmindexPancakeswapV2Oracle-constructor-address-address-'></a> `constructor`

```
function constructor(address uniswapFactory, address wBNB)
```

## <a id='IndexedUniswapV2Oracle-updatePrice-address-'></a> `updatePrice`

```
function updatePrice(address token) returns (bool)
```



Attempts to update the price of `token` and returns a boolean
indicating whether it was updated.

**Note:** The price can be updated if there is no observation for the current hour
and at least 30 minutes have passed since the last observation.


## <a id='SmindexPancakeswapV2Oracle-updatePrices-address---'></a> `updatePrices`

```
function updatePrices(address[] tokens) returns (bool[] pricesUpdated)
```

Attempts to update the price of each token in `tokens` and returns a boolean
array indicating which tokens had their prices updated.

**Note:** The price can be updated if there is no observation for the current hour
and at least 30 minutes have passed since the last observation.


## <a id='SmindexPancakeswapV2Oracle-hasPriceObservationInWindow-address-uint256-'></a> `hasPriceObservationInWindow`

```
function hasPriceObservationInWindow(address token, uint256 priceKey) returns (bool)
```



Returns a boolean indicating whether a price was recorded for `token` at `priceKey`.


### Parameters:
- `token`: Token to check if the oracle has a price for

- `priceKey`: Index of the hour to check

## <a id='SmindexPancakeswapV2Oracle-getPriceObservationInWindow-address-uint256-'></a> `getPriceObservationInWindow`

```
function getPriceObservationInWindow(address token, uint256 priceKey) returns (struct PriceLibrary.PriceObservation observation)
```

Returns the price observation for `token` recorded in `priceKey`.
Reverts if no prices have been recorded for that key.


### Parameters:
- `token`: Token to retrieve a price for

- `priceKey`: Index of the hour to query

## <a id='SmindexPancakeswapV2Oracle-getPriceObservationsInRange-address-uint256-uint256-'></a> `getPriceObservationsInRange`

```
function getPriceObservationsInRange(address token, uint256 timeFrom, uint256 timeTo) returns (struct PriceLibrary.PriceObservation[] prices)
```

Returns all price observations for `token` recorded between `timeFrom` and `timeTo`.


## <a id='SmindexPancakeswapV2Oracle-canUpdatePrice-address-'></a> `canUpdatePrice`

```
function canUpdatePrice(address token) returns (bool)
```


Returns a boolean indicating whether the price of `token` can be updated.

**Note:** The price can be updated if there is no observation for the current hour
and at least 30 minutes have passed since the last observation.


## <a id='SmindexPancakeswapV2Oracle-canUpdatePrices-address---'></a> `canUpdatePrices`

```
function canUpdatePrices(address[] tokens) returns (bool[] canUpdateArr)
```

Returns a boolean array indicating whether the price of each token in
`tokens` can be updated.

**Note:** The price can be updated if there is no observation for the current hour
and at least 30 minutes have passed since the last observation.


## <a id='SmindexPancakeswapV2Oracle-computeTwoWayAveragePrice-address-uint256-uint256-'></a> `computeTwoWayAveragePrice`

```
function computeTwoWayAveragePrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct PriceLibrary.TwoWayAveragePrice)
```



Returns the TwoWayAveragePrice struct representing the average price of
wBNB in terms of `token` and the average price of `token` in terms of wBNB.

Computes the time-weighted average price of wBNB in terms of `token` and the price
of `token` in terms of wBNB by getting the current prices from Uniswap and searching
for a historical price which is between `minTimeElapsed` and `maxTimeElapsed` seconds old.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.

**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageTokenPrice-address-uint256-uint256-'></a> `computeAverageTokenPrice`

```
function computeAverageTokenPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct FixedPoint.uq112x112 priceAverage)
```



Returns the UQ112x112 struct representing the average price of
`token` in terms of wBNB.

Computes the time-weighted average price of `token` in terms of wBNB by getting the
current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.

**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageBNBPrice-address-uint256-uint256-'></a> `computeAverageBNBPrice`

```
function computeAverageBNBPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct FixedPoint.uq112x112 priceAverage)
```

Returns the UQ112x112 struct representing the average price of
wBNB in terms of `token`.

Computes the time-weighted average price of wBNB in terms of `token` by getting the
current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.

**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeTwoWayAveragePrices-address---uint256-uint256-'></a> `computeTwoWayAveragePrices`

```
function computeTwoWayAveragePrices(address[] tokens, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct PriceLibrary.TwoWayAveragePrice[] prices)
```

Returns the TwoWayAveragePrice structs representing the average price of
wBNB in terms of each token in `tokens` and the average price of each token
in terms of wBNB.

Computes the time-weighted average price of wBNB in terms of each token and the price
of each token in terms of wBNB by getting the current prices from Uniswap and searching
for a historical price which is between `minTimeElapsed` and `maxTimeElapsed` seconds old.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.

**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageTokenPrices-address---uint256-uint256-'></a> `computeAverageTokenPrices`

```
function computeAverageTokenPrices(address[] tokens, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct FixedPoint.uq112x112[] averagePrices)
```

Returns the UQ112x112 structs representing the average price of
each token in `tokens` in terms of wBNB.

Computes the time-weighted average price of each token in terms of wBNB by getting
the current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.

**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageBNBPrices-address---uint256-uint256-'></a> `computeAverageBNBPrices`

```
function computeAverageBNBPrices(address[] tokens, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct FixedPoint.uq112x112[] averagePrices)
```



Returns the UQ112x112 structs representing the average price of
wBNB in terms of each token in `tokens`.

Computes the time-weighted average price of wBNB in terms of each token by getting
the current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.
**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageBNBForTokens-address-uint256-uint256-uint256-'></a> `computeAverageBNBForTokens`

```
function computeAverageBNBForTokens(address token, uint256 tokenAmount, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (uint144)
```



Compute the average value of `tokenAmount` bnb in terms of wBNB.
Computes the time-weighted average price of `token` in terms of wBNB by getting
the current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old, then multiplies by `wBNBAmount`.
**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.
**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageTokensForBNB-address-uint256-uint256-uint256-'></a> `computeAverageTokensForBNB`

```
function computeAverageTokensForBNB(address token, uint256 wBNBAmount, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (uint144)
```



Compute the average value of `wBNBAmount` bnb in terms of `token`.
Computes the time-weighted average price of wBNB in terms of the token by getting
the current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old, then multiplies by `wBNBAmount`.
**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.
**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageBNBForTokens-address---uint256---uint256-uint256-'></a> `computeAverageBNBForTokens`

```
function computeAverageBNBForTokens(address[] tokens, uint256[] tokenAmounts, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (uint144[] averageValuesInWBNB)
```



Compute the average value of each amount of tokens in `tokenAmounts` in terms
of the corresponding token in `tokens`.
Computes the time-weighted average price of each token in terms of wBNB by getting
the current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old, then multiplies by the corresponding
amount in `tokenAmounts`.
**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.
**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-computeAverageTokensForBNB-address---uint256---uint256-uint256-'></a> `computeAverageTokensForBNB`

```
function computeAverageTokensForBNB(address[] tokens, uint256[] wBNBAmounts, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (uint144[] averageValuesInWBNB)
```



Compute the average value of each amount of bnb in `wBNBAmounts` in terms
of the corresponding token in `tokens`.
Computes the time-weighted average price of wBNB in terms of each token by getting
the current price from Uniswap and searching for a historical price which is between
`minTimeElapsed` and `maxTimeElapsed` seconds old, then multiplies by the corresponding
amount in `wBNBAmounts`.
**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is less than one hour.
**Note:** `minTimeElapsed` is only accurate to the nearest hour (rounded up) unless
it is less than one hour.


## <a id='SmindexPancakeswapV2Oracle-_getTwoWayPrice-address-uint256-uint256-'></a> `_getTwoWayPrice`

```
function _getTwoWayPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct PriceLibrary.TwoWayAveragePrice)
```






## <a id='SmindexPancakeswapV2Oracle-_getTokenPrice-address-uint256-uint256-'></a> `_getTokenPrice`

```
function _getTokenPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct FixedPoint.uq112x112)
```






## <a id='SmindexPancakeswapV2Oracle-_getBNBPrice-address-uint256-uint256-'></a> `_getBNBPrice`

```
function _getBNBPrice(address token, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (struct FixedPoint.uq112x112)
```






