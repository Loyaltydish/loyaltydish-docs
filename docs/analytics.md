All analytics queries accepts a `timeUnit` input proprty which accepts `minute`, `hour`, `day`, `week`, `month` as values and a `timeFrame` property with `start` and `end` of type `DateTime`.

## Offers redemptions

```gql
{
  myOffersRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }

  storeOffersRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```


## Single offer redemptions

```gql
{
  offerRedemptions(
    timeUnit: "day"
    filters: {
      offerId: 1
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```

## Offers impressions

```gql
{
  myOffersImpressions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }

  storeOffersImpressions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```


## Loyalty rewards redemptions

```gql
{
  myLoyaltyRewardsRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }

  storeLoyaltyRewardsRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```

## Loyalty stamps redemptions

```gql
{
  myLoyaltyStampsRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }

  storeLoyaltyStampsRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```

## Loyalty points redemptions

```gql
{
  myLoyaltyPointsRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }

  storeLoyaltyPointsRedemptions(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```

## Loyalty points earned

```gql
{
  merchantLoyaltyPointsEarned(
    timeUnit: "day"
    filters: {
      timeFrame: {}
    }
  ) {
    timestamp
    total
  }

  storeLoyaltyPointsEarned(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
    }
  ) {
    timestamp
    total
  }
}
```

## Loyalty points issued

```gql
{
  myLoyaltyPointsIssued(
    timeUnit: "day"
    filters: {
      timeFrame: {}
    }
  ) {
    timestamp
    total
  }

  storeLoyaltyPointsIssued(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
    }
  ) {
    timestamp
    total
  }
}
```

## Loyalty stamps issued

```gql
{
  myLoyaltyStampsIssued(
    timeUnit: "day"
    filters: {
      timeFrame: {}
    }
  ) {
    timestamp
    total
  }

  storeLoyaltyStampsIssued(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
    }
  ) {
    timestamp
    total
  }
}
```

## Total customers joined

```gql
{
  totalConsumers(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    timestamp
    total
  }
}
```

## Store earnings

```gql
{
  myEarnings(
    timeUnit: "day"
    filters: {
      timeFrame: {}
    }
  ) {
    timestamp
    total
  }

  storeEarnings(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
    }
  ) {
    timestamp
    total
  }
}
```

## Store refunds

```gql
{
  myRefunds(
    timeUnit: "day"
    filters: {
      timeFrame: {}
    }
  ) {
    timestamp
    total
  }

  storeRefunds(
    timeUnit: "day"
    filters: {
      timeFrame: {}
      storeId: 19
    }
  ) {
    timestamp
    total
  }
}
```

## General report

```gql
{
  storeGeneralReport(
    filters: {
      storeId: 47
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    totalConsumers
    offersRedemptions
    pointsRedemptions
    pointsEarned
    stampsRedemptions
    stampsEarned
  }

	myGeneralReport(
    filters: {
      country: ""
      city: ""
      gender: ""
      zipCode: ""
    }
  ) {
    totalConsumers
    offersRedemptions
    pointsRedemptions
    pointsEarned
    stampsRedemptions
    stampsEarned
  }
}
```
