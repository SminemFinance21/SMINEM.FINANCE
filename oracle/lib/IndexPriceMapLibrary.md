# `SmindexPriceMapLibrary`

# Functions:
- [`toPriceKey(uint256 timestamp)`](#SmindexPriceMapLibrary-toPriceKey-uint256-)
- [`timeElapsedSinceWindowStart(uint256 timestamp)`](#SmindexPriceMapLibrary-timeElapsedSinceWindowStart-uint256-)
- [`writePriceObservation(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, struct PriceLibrary.PriceObservation observation)`](#SmindexPriceMapLibrary-writePriceObservation-struct-SmindexPriceMapLibrary-SmindexPriceMap-struct-PriceLibrary-PriceObservation-)
- [`sufficientDelaySinceLastPrice(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint32 newTimestamp)`](#SmindexPriceMapLibrary-sufficientDelaySinceLastPrice-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint32-)
- [`canUpdatePrice(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint32 newTimestamp)`](#SmindexPriceMapLibrary-canUpdatePrice-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint32-)
- [`hasPriceInWindow(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 priceKey)`](#SmindexPriceMapLibrary-hasPriceInWindow-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-)
- [`getPriceInWindow(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 priceKey)`](#SmindexPriceMapLibrary-getPriceInWindow-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-)
- [`getPriceObservationsInRange(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 timeFrom, uint256 timeTo)`](#SmindexPriceMapLibrary-getPriceObservationsInRange-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-uint256-)
- [`getLastPriceObservation(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 timestamp, uint256 minTimeElapsed, uint256 maxTimeElapsed)`](#SmindexPriceMapLibrary-getLastPriceObservation-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-uint256-uint256-)

## <a id='SmindexPriceMapLibrary-toPriceKey-uint256-'></a> `toPriceKey`

```
function toPriceKey(uint256 timestamp) returns (uint256)
```



Returns the price key for `timestamp`, which is the hour index.


## <a id='SmindexPriceMapLibrary-timeElapsedSinceWindowStart-uint256-'></a> `timeElapsedSinceWindowStart`

```
function timeElapsedSinceWindowStart(uint256 timestamp) returns (uint256)
```



Returns the number of seconds that have passed since the beginning of the hour.


## <a id='SmindexPriceMapLibrary-writePriceObservation-struct-SmindexPriceMapLibrary-SmindexPriceMap-struct-PriceLibrary-PriceObservation-'></a> `writePriceObservation`

```
function writePriceObservation(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, struct PriceLibrary.PriceObservation observation) returns (bool)
```

Writes `observation` to storage if the price can be updated. If it is
updated, also marks the price key for the observation as having a value in
the key index.

**Note:** The price can be updated if there is none recorded for the current
hour 30 minutes have passed since the last price update.
Returns a boolean indicating whether the price was updated.


## <a id='SmindexPriceMapLibrary-sufficientDelaySinceLastPrice-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint32-'></a> `sufficientDelaySinceLastPrice`

```
function sufficientDelaySinceLastPrice(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint32 newTimestamp) returns (bool)
```

Checks whether sufficient time has passed since the beginning of the observation
window or since the price recorded in the previous window (if any) for a new price
to be recorded.


## <a id='SmindexPriceMapLibrary-canUpdatePrice-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint32-'></a> `canUpdatePrice`

```
function canUpdatePrice(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint32 newTimestamp) returns (bool)
```

Checks if a price can be updated. Prices can be updated if there is no price
observation for the current hour and at least 30 minutes have passed since the
observation in the previous hour (if there is one).


## <a id='SmindexPriceMapLibrary-hasPriceInWindow-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-'></a> `hasPriceInWindow`

```
function hasPriceInWindow(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 priceKey) returns (bool)
```

Checks the key index to see if a price is recorded for `priceKey`


## <a id='SmindexPriceMapLibrary-getPriceInWindow-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-'></a> `getPriceInWindow`

```
function getPriceInWindow(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 priceKey) returns (struct PriceLibrary.PriceObservation)
```



Returns the price observation for `priceKey`


## <a id='SmindexPriceMapLibrary-getPriceObservationsInRange-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-uint256-'></a> `getPriceObservationsInRange`

```
function getPriceObservationsInRange(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 timeFrom, uint256 timeTo) returns (struct PriceLibrary.PriceObservation[] prices)
```


## <a id='SmindexPriceMapLibrary-getLastPriceObservation-struct-SmindexPriceMapLibrary-SmindexPriceMap-uint256-uint256-uint256-'></a> `getLastPriceObservation`

```
function getLastPriceObservation(struct SmindexPriceMapLibrary.SmindexPriceMap smindexPriceMap, uint256 timestamp, uint256 minTimeElapsed, uint256 maxTimeElapsed) returns (bool, uint256)
```



Finds the most recent price observation before `timestamp` with a minimum
difference in observation times of `minTimeElapsed` and a maximum difference in
observation times of `maxTimeElapsed`.

**Note:** `maxTimeElapsed` is only accurate to the nearest hour (rounded down) unless
it is below one hour.


## Parameters:
- `smindexPriceMap`: Struct with the indexed price mapping for the token.

- `timestamp`: Timestamp to search backwards from.

- `minTimeElapsed`: Minimum time elapsed between price observations.

- `maxTimeElapsed`: Maximum time elapsed between price observations.
Only accurate to the nearest hour (rounded down) unless it is below 1 hour.

