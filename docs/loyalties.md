## Loyalty card object

| Method                   | Type                                    | Description |
| ------------------------ | --------------------------------------- | ----------- |
| id                       | `ID!`                                   |
| pk                       | `Int`                                   |
| merchant                 | `UserNode`                              |
| stores                   | `StoreNodeConnection!`                  |
| storeGroups              | `StoreGroupNodeConnection!`             |
| products                 | `ProductNodeConnection!`                |
| campaign                 | `CampaignNode`                          |
| name                     | `String!`                               |
| shortDescription         | `String`                                |
| longDescription          | `String`                                |
| placement                | `LoyaltyCardPlacement`                  |
| startTime                | `DateTime!`                             |
| endTime                  | `DateTime!`                             |
| redemptionCodeType       | `LoyaltyCardRedemptionCodeType!`        |
| enrollmentLimit          | `Int`                                   |
| repeatable               | `Boolean`                               |
| repeatDelayHours         | `Int`                                   |
| dayStartTime             | `Time`                                  |
| dayEndTime               | `Time`                                  |
| daysOfWeek               | `[String]`                              |
| weather                  | `String`                                |
| termsAndConditions       | `String`                                |
| minimumSpendCurrency     | `LoyaltyCardMinimumSpendCurrency`       |
| minimumSpend             | `String`                                |
| minPriceCurrency         | `LoyaltyCardMinPriceCurrency`           |
| minPrice                 | `String`                                |
| maxPriceCurrency         | `LoyaltyCardMaxPriceCurrency`           |
| maxPrice                 | `String`                                |
| loyaltyType              | `LoyaltyCardLoyaltyType!`               |
| pointsLoyaltyType        | `LoyaltyCardPointsLoyaltyType`          |
| code                     | `String`                                |
| redemptionExpirationDays | `Int`                                   |
| initialPoints            | `Int`                                   |
| validityInMonths         | `Int`                                   |
| stampsNeeded             | `Int`                                   |
| stampExpirationDays      | `Int`                                   |
| maxPointsPerDay          | `Int`                                   |
| maxStampsPerDay          | `Int`                                   |
| pointsNeeded             | `Int`                                   |
| incrementalPoints        | `Int`                                   |
| dollarWorth              | `Int`                                   |
| pointWorthCurrency       | `LoyaltyCardPointWorthCurrency`         |
| pointWorth               | `String`                                |
| status                   | `LoyaltyCardStatus!`                    |
| pictures                 | `LoyaltyCardPictureNodeConnection!`     |
| rewards                  | `LoyaltyRewardNodeConnection!`          |
| stampsRedemptionIntents  | `StampsRedemptionIntentNodeConnection!` |
| stampsRedemptions        | `StampsRedemptionNodeConnection!`       |
| pointsRedemptionIntents  | `PointsRedemptionIntentNodeConnection!` |
| pointsRedemptions        | `PointsRedemptionNodeConnection!`       |
| stamps                   | `StampNodeConnection`                   |
| minimumSpendAmount       | `Float`                                 |
| minPriceAmount           | `Float`                                 |
| maxPriceAmount           | `Float`                                 |
| pointWorthAmount         | `Float`                                 |
| checkedStamps            | `Int`                                   |
| earnedPoints             | `Int`                                   |
| rewardAvailable          | `Boolean`                               |
| visits                   | `VisitNodeConnection`                   |
| extraInfo                | `JSONString`                            |
| createdAt                | `DateTime!`                             |
| updatedAt                | `DateTime!`                             |


## Create a points loyalty

### Reward flat amount

=== "Request"
    ```gql
    mutation CreateLoyalty(
      stores: [ID]!
      storeGroups: [ID]!
      campaignId: ID
      weather: String
      name: String!
      shortDescription: String
      longDescription: String
      placement: String
      startTime: DateTime!
      endTime: DateTime!
      redemptionCodeType: String!
      enrollmentLimit: Int!
      dayStartTime: Time
      dayEndTime: Time
      daysOfWeek: [String]!
      termsAndConditions: String
      loyaltyType: String!
      code: String
      pictures: [LoyaltyImageInput]!
      repeatable: Boolean!
      repeatDelayHours: Int
      redemptionExpirationDays: Int!
      minPrice: Decimal!
      minPriceCurrency: String
      maxPrice: Decimal!
      maxPriceCurrency: String
      minimumSpend: Decimal
      minimumSpendCurrency: String
      pointsLoyaltyType: String
      dollarWorth: Int
      maxPointsPerDay: Int
      initialPoints: Int
      pointWorth: Decimal
      pointWorthCurrency: String
      pointsNeeded: Int
      incrementalPoints: Int
      rewards: [LoyaltyRewardInput]
      products: [ID]
      stampsNeeded: Int
      stampExpirationDays: Int
      validityInMonths: Int
      maxStampsPerDay: Int
    ){
      createLoyaltyCard(
        input: {
          stores: $stores
          storeGroups: $storeGroups
          campaignId: $campaignId
          weather: $weather
          name: $name
          shortDescription: $shortDescription
          longDescription: $longDescription
          placement: $placement
          startTime: $startTime
          endTime: $endTime
          redemptionCodeType: $redemptionCodeType
          enrollmentLimit: $enrollmentLimit
          dayStartTime: $dayStartTime
          dayEndTime: $dayEndTime
          daysOfWeek: $daysOfWeek
          termsAndConditions: $termsAndConditions
          loyaltyType: $loyaltyType
          code: $code
          pictures: $pictures
          repeatable: $repeatable
          repeatDelayHours: $repeatDelayHours
          redemptionExpirationDays: $redemptionExpirationDays
          minPrice: $minPrice
          minPriceCurrency: $minPriceCurrency
          maxPrice: $maxPrice
          maxPriceCurrency: $maxPriceCurrency
          minimumSpend: $minimumSpend
          minimumSpendCurrency: $minimumSpendCurrency
          pointsLoyaltyType: $pointsLoyaltyType
          dollarWorth: $dollarWorth
          maxPointsPerDay: $maxPointsPerDay
          initialPoints: $initialPoints
          pointWorth: $pointWorth
          pointWorthCurrency: $pointWorthCurrency
          pointsNeeded: $pointsNeeded
          incrementalPoints: $incrementalPoints
          rewards: $rewards
          products: $products
          stampsNeeded: $stampsNeeded
          stampExpirationDays: $stampExpirationDays
          validityInMonths: $validityInMonths
          maxStampsPerDay: $maxStampsPerDay
        }
      ) {
        success
        errors
        loyaltyCard {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Points loyalty",
      "shortDescription": "Points loyalty short description",
      "longDescription": "Points loyalty long description",
      "loyaltyType": "POINTS",
      "redemptionCodeType": "AUTOGENERATED",
      "enrollmentLimit": 2000,
      "repeatable": true,
      "repeatDelayHours": 48,
      "redemptionExpirationDays": 24,
      "minPrice": "10.00",
      "maxPrice": "100.00",
      "pointsLoyaltyType": "FLAT",
      "dollarWorth": 5,
      "maxPointsPerDay": 20,
      "initialPoints": 5,
      "pointWorth": "1.00",
      "pointsNeeded": 200,
      "incrementalPoints": 10,
      "products": [1, 2, 3],
      "startTime": "2022-04-25T11:40",
      "endTime": "2023-12-31T23:40",
      "dayStartTime": "06:11",
      "dayEndTime": "23:41",
      "daysOfWeek": [
        "MONDAY",
        "TUESDAY",
        "WEDNESDAY",
        "THURSDAY",
        "FRIDAY",
        "SATURDAY",
        "SUNDAY"
      ],
      "campaignId": 5,
      "stores": [7, 8, 9],
      "storeGroups": [20, 23, 25]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createLoyaltyCard": {
                "success": true,
                "errors": null,
                "loyaltyCard": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

### Reward a product

=== "Request"
    ```gql
    mutation CreateLoyalty(
      stores: [ID]!
      storeGroups: [ID]!
      campaignId: ID
      weather: String
      name: String!
      shortDescription: String
      longDescription: String
      placement: String
      startTime: DateTime!
      endTime: DateTime!
      redemptionCodeType: String!
      enrollmentLimit: Int!
      dayStartTime: Time
      dayEndTime: Time
      daysOfWeek: [String]!
      termsAndConditions: String
      loyaltyType: String!
      code: String
      pictures: [LoyaltyImageInput]!
      repeatable: Boolean!
      repeatDelayHours: Int
      redemptionExpirationDays: Int!
      minPrice: Decimal!
      minPriceCurrency: String
      maxPrice: Decimal!
      maxPriceCurrency: String
      minimumSpend: Decimal
      minimumSpendCurrency: String
      pointsLoyaltyType: String
      dollarWorth: Int
      maxPointsPerDay: Int
      initialPoints: Int
      pointWorth: Decimal
      pointWorthCurrency: String
      pointsNeeded: Int
      incrementalPoints: Int
      rewards: [LoyaltyRewardInput]
      products: [ID]
      stampsNeeded: Int
      stampExpirationDays: Int
      validityInMonths: Int
      maxStampsPerDay: Int
    ){
      createLoyaltyCard(
        input: {
          stores: $stores
          storeGroups: $storeGroups
          campaignId: $campaignId
          weather: $weather
          name: $name
          shortDescription: $shortDescription
          longDescription: $longDescription
          placement: $placement
          startTime: $startTime
          endTime: $endTime
          redemptionCodeType: $redemptionCodeType
          enrollmentLimit: $enrollmentLimit
          dayStartTime: $dayStartTime
          dayEndTime: $dayEndTime
          daysOfWeek: $daysOfWeek
          termsAndConditions: $termsAndConditions
          loyaltyType: $loyaltyType
          code: $code
          pictures: $pictures
          repeatable: $repeatable
          repeatDelayHours: $repeatDelayHours
          redemptionExpirationDays: $redemptionExpirationDays
          minPrice: $minPrice
          minPriceCurrency: $minPriceCurrency
          maxPrice: $maxPrice
          maxPriceCurrency: $maxPriceCurrency
          minimumSpend: $minimumSpend
          minimumSpendCurrency: $minimumSpendCurrency
          pointsLoyaltyType: $pointsLoyaltyType
          dollarWorth: $dollarWorth
          maxPointsPerDay: $maxPointsPerDay
          initialPoints: $initialPoints
          pointWorth: $pointWorth
          pointWorthCurrency: $pointWorthCurrency
          pointsNeeded: $pointsNeeded
          incrementalPoints: $incrementalPoints
          rewards: $rewards
          products: $products
          stampsNeeded: $stampsNeeded
          stampExpirationDays: $stampExpirationDays
          validityInMonths: $validityInMonths
          maxStampsPerDay: $maxStampsPerDay
        }
      ) {
        success
        errors
        loyaltyCard {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Points loyalty",
      "shortDescription": "Points loyalty short description",
      "longDescription": "Points loyalty long description",
      "loyaltyType": "POINTS",
      "redemptionCodeType": "AUTOGENERATED",
      "enrollmentLimit": 2000,
      "repeatable": true,
      "repeatDelayHours": 48,
      "redemptionExpirationDays": 24,
      "minPrice": "10.00",
      "maxPrice": "100.00",
      "pointsLoyaltyType": "PRODUCT",
      "rewards": [5, 6, 7],
      "dollarWorth": 5,
      "maxPointsPerDay": 20,
      "initialPoints": 5,
      "pointWorth": "1.00",
      "pointsNeeded": 200,
      "incrementalPoints": 10,
      "products": [1, 2, 3],
      "startTime": "2022-04-25T11:40",
      "endTime": "2023-12-31T23:40",
      "dayStartTime": "06:11",
      "dayEndTime": "23:41",
      "daysOfWeek": [
        "MONDAY",
        "TUESDAY",
        "WEDNESDAY",
        "THURSDAY",
        "FRIDAY",
        "SATURDAY",
        "SUNDAY"
      ],
      "campaignId": 5,
      "stores": [7, 8, 9],
      "storeGroups": [20, 23, 25]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createLoyaltyCard": {
                "success": true,
                "errors": null,
                "loyaltyCard": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Create a stamps loyalty

=== "Request"
    ```gql
    mutation CreateLoyalty(
      stores: [ID]!
      storeGroups: [ID]!
      campaignId: ID
      weather: String
      name: String!
      shortDescription: String
      longDescription: String
      placement: String
      startTime: DateTime!
      endTime: DateTime!
      redemptionCodeType: String!
      enrollmentLimit: Int!
      dayStartTime: Time
      dayEndTime: Time
      daysOfWeek: [String]!
      termsAndConditions: String
      loyaltyType: String!
      code: String
      pictures: [LoyaltyImageInput]!
      repeatable: Boolean!
      repeatDelayHours: Int
      redemptionExpirationDays: Int!
      minPrice: Decimal!
      minPriceCurrency: String
      maxPrice: Decimal!
      maxPriceCurrency: String
      minimumSpend: Decimal
      minimumSpendCurrency: String
      pointsLoyaltyType: String
      dollarWorth: Int
      maxPointsPerDay: Int
      initialPoints: Int
      pointWorth: Decimal
      pointWorthCurrency: String
      pointsNeeded: Int
      incrementalPoints: Int
      rewards: [LoyaltyRewardInput]
      products: [ID]
      stampsNeeded: Int
      stampExpirationDays: Int
      validityInMonths: Int
      maxStampsPerDay: Int
    ){
      createLoyaltyCard(
        input: {
          stores: $stores
          storeGroups: $storeGroups
          campaignId: $campaignId
          weather: $weather
          name: $name
          shortDescription: $shortDescription
          longDescription: $longDescription
          placement: $placement
          startTime: $startTime
          endTime: $endTime
          redemptionCodeType: $redemptionCodeType
          enrollmentLimit: $enrollmentLimit
          dayStartTime: $dayStartTime
          dayEndTime: $dayEndTime
          daysOfWeek: $daysOfWeek
          termsAndConditions: $termsAndConditions
          loyaltyType: $loyaltyType
          code: $code
          pictures: $pictures
          repeatable: $repeatable
          repeatDelayHours: $repeatDelayHours
          redemptionExpirationDays: $redemptionExpirationDays
          minPrice: $minPrice
          minPriceCurrency: $minPriceCurrency
          maxPrice: $maxPrice
          maxPriceCurrency: $maxPriceCurrency
          minimumSpend: $minimumSpend
          minimumSpendCurrency: $minimumSpendCurrency
          pointsLoyaltyType: $pointsLoyaltyType
          dollarWorth: $dollarWorth
          maxPointsPerDay: $maxPointsPerDay
          initialPoints: $initialPoints
          pointWorth: $pointWorth
          pointWorthCurrency: $pointWorthCurrency
          pointsNeeded: $pointsNeeded
          incrementalPoints: $incrementalPoints
          rewards: $rewards
          products: $products
          stampsNeeded: $stampsNeeded
          stampExpirationDays: $stampExpirationDays
          validityInMonths: $validityInMonths
          maxStampsPerDay: $maxStampsPerDay
        }
      ) {
        success
        errors
        loyaltyCard {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Stamps loyalty",
      "shortDescription": "Stamps loyalty short description",
      "longDescription": "Stamps loyalty long description",
      "loyaltyType": "STAMPS",
      "redemptionCodeType": "AUTOGENERATED",
      "enrollmentLimit": 2000,
      "repeatable": true,
      "repeatDelayHours": 48,
      "redemptionExpirationDays": 24,
      "minPrice": "10.00",
      "maxPrice": "100.00",
      "stampsNeeded": 5,
      "stampExpirationDays": 3,
      "maxStampsPerDay": 1,
      "products": [1, 2, 3],
      "startTime": "2022-04-25T11:40",
      "endTime": "2023-12-31T23:40",
      "dayStartTime": "06:11",
      "dayEndTime": "23:41",
      "daysOfWeek": [
        "MONDAY",
        "TUESDAY",
        "WEDNESDAY",
        "THURSDAY",
        "FRIDAY",
        "SATURDAY",
        "SUNDAY"
      ],
      "campaignId": 5,
      "stores": [7, 8, 9],
      "storeGroups": [20, 23, 25]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createLoyaltyCard": {
                "success": true,
                "errors": null,
                "loyaltyCard": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```


## Update a loyalty card

=== "Request"
    ```gql
    mutation UpdateLoyalty(
      id: ID!
      stores: [ID]
      storeGroups: [ID]
      campaignId: ID
      weather: String
      name: String
      shortDescription: String
      longDescription: String
      placement: String
      startTime: DateTime
      endTime: DateTime
      redemptionCodeType: String
      enrollmentLimit: Int
      dayStartTime: Time
      dayEndTime: Time
      daysOfWeek: [String]
      termsAndConditions: String
      loyaltyType: String
      code: String
      pictures: [LoyaltyImageInput]
      repeatable: Boolean
      repeatDelayHours: Int
      redemptionExpirationDays: Int
      minPrice: Decimal
      minPriceCurrency: String
      maxPrice: Decimal
      maxPriceCurrency: String
      minimumSpend: Decimal
      minimumSpendCurrency: String
      pointsLoyaltyType: String
      dollarWorth: Int
      maxPointsPerDay: Int
      initialPoints: Int
      pointWorth: Decimal
      pointWorthCurrency: String
      pointsNeeded: Int
      incrementalPoints: Int
      rewards: [LoyaltyRewardInput]
      products: [ID]
      stampsNeeded: Int
      stampExpirationDays: Int
      validityInMonths: Int
      maxStampsPerDay: Int
    ){
      updateLoyaltyCard(
        input: {
          id: $id
          stores: $stores
          storeGroups: $storeGroups
          campaignId: $campaignId
          weather: $weather
          name: $name
          shortDescription: $shortDescription
          longDescription: $longDescription
          placement: $placement
          startTime: $startTime
          endTime: $endTime
          redemptionCodeType: $redemptionCodeType
          enrollmentLimit: $enrollmentLimit
          dayStartTime: $dayStartTime
          dayEndTime: $dayEndTime
          daysOfWeek: $daysOfWeek
          termsAndConditions: $termsAndConditions
          loyaltyType: $loyaltyType
          code: $code
          pictures: $pictures
          repeatable: $repeatable
          repeatDelayHours: $repeatDelayHours
          redemptionExpirationDays: $redemptionExpirationDays
          minPrice: $minPrice
          minPriceCurrency: $minPriceCurrency
          maxPrice: $maxPrice
          maxPriceCurrency: $maxPriceCurrency
          minimumSpend: $minimumSpend
          minimumSpendCurrency: $minimumSpendCurrency
          pointsLoyaltyType: $pointsLoyaltyType
          dollarWorth: $dollarWorth
          maxPointsPerDay: $maxPointsPerDay
          initialPoints: $initialPoints
          pointWorth: $pointWorth
          pointWorthCurrency: $pointWorthCurrency
          pointsNeeded: $pointsNeeded
          incrementalPoints: $incrementalPoints
          rewards: $rewards
          products: $products
          stampsNeeded: $stampsNeeded
          stampExpirationDays: $stampExpirationDays
          validityInMonths: $validityInMonths
          maxStampsPerDay: $maxStampsPerDay
        }
      ) {
        success
        errors
        loyaltyCard {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 100,
      "name": "Stamps loyalty - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateLoyaltyCard": {
                "success": true,
                "errors": null,
                "loyaltyCard": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Delete a loyalty card

=== "Request"
    ```gql
    mutation DeleteLoyalty(
      id: ID!
    ){
      updateLoyaltyCard(
        input: {
          id: $id
        }
      ) {
        success
        errors
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 100
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteLoyaltyCard": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Create a loyalty reward

=== "Request"
    ```gql
    mutation CreateLoyaltyReward(
      $loyaltyCardId: ID!
      $productId: ID!
      $points: Int!
      $expiry: Date!
    ){
      createLoyaltyReward(
        input: {
          loyaltyCardId: $loyaltyCardId
          productId: $productId
          points: $points
          expiry: $expiry
        }
      ) {
        success
        errors
        loyaltyReward {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "loyaltyCardId": 100,
      "productId": 5,
      "points": 200,
      "expiry": "2022-07-31"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createLoyaltyReward": {
                "success": true,
                "errors": null,
                "loyaltyReward": {
                  "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Update a loyalty reward

=== "Request"
    ```gql
    mutation CreateLoyaltyReward(
      $id: ID!
      $loyaltyCardId: ID
      $productId: ID
      $points: Int
      $expiry: Date
    ){
      updateLoyaltyReward(
        input: {
          id: $id
          loyaltyCardId: $loyaltyCardId
          productId: $productId
          points: $points
          expiry: $expiry
        }
      ) {
        success
        errors
        loyaltyReward {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 1,
      "expiry": "2022-08-08"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateLoyaltyReward": {
                "success": true,
                "errors": null,
                "loyaltyReward": {
                  "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Create a stamp

=== "Request"
    ```gql
    mutation CreateStamp(
      $consumerLoyaltyString: String!
    ){
      createStamp(
        input: {
          consumerLoyaltyString: $consumerLoyaltyString
        }
      ) {
        success
        errors
        stamp {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "consumerLoyaltyString": "59841898004705"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createStamp": {
                "success": true,
                "errors": null,
                "stamp": {
                  "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Create stamps redemption intent

=== "Request"
    ```gql
    mutation (
      $loyaltyCardId: ID!
    ){
      createStampsRedemptionIntent(
        input: {
          loyaltyCardId: $loyaltyCardId
        }
      ) {
        success
        errors
        stampsRedemptionIntent {
          id
          code
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "loyaltyCardId": 100
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createStampsRedemptionIntent": {
                "success": true,
                "errors": null,
                "stamp": {
                  "id": "U3RvcmVOb2RlOjEzMQ==",
                  "code": "..."
                }
            }
        }
    }
    ```

## Confirm stamps redemption

=== "Request"
    ```gql
    mutation (
      $code: String!
    ){
      confirmStampsRedemption(
        input: {
          code: $code
        }
      ) {
        success
        errors
        stampsRedemption {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "code": "..."
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "confirmStampsRedemption": {
                "success": true,
                "errors": null,
                "stampsRedemption": {
                  "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Create a visit

=== "Request"
    ```gql
    mutation (
      $consumerLoyaltyId: String!
      $amountSpent: Decimal!
      $amountSpentCurrency: String
      $storeId: ID
    ){
      createVisit(
        input: {
          consumerLoyaltyId: $consumerLoyaltyId
          amountSpent: $amountSpent
          amountSpentCurrency: $amountSpentCurrency
          storeId: $storeId
        }
      ) {
        success
        errors
        visit {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "consumerLoyaltyId": "59841898004705",
      "amountSpent": "20.00",
      "storeId": 5
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createVisit": {
                "success": true,
                "errors": null,
                "visit": {
                  "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Create points redemption intent

=== "Request"
    ```gql
    mutation (
      $loyaltyCardId: ID!
      $pointsToRedeem: Int
      $loyaltyRewardId: ID
    ){
      createPointsRedemptionIntent(
        input: {
          loyaltyCardId: $loyaltyCardId
          pointsToRedeem: $pointsTor_redeem
          loyaltyRewardId: $loyaltyRewardId
        }
      ) {
        success
        errors
        pointsRedemptionIntent {
          id
          code
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "loyaltyCardId": 100,
      "pointsToRedeem: 50,
      "loyaltyRewardId: 9
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createPointsRedemptionIntent": {
                "success": true,
                "errors": null,
                "stamp": {
                  "id": "U3RvcmVOb2RlOjEzMQ==",
                  "code": "..."
                }
            }
        }
    }
    ```

## Confirm points redemption

=== "Request"
    ```gql
    mutation (
      $code: String!
    ){
      confirmPointsRedemption(
        input: {
          code: $code
        }
      ) {
        success
        errors
        pointsRedemption {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "code": "..."
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "confirmPointsRedemption": {
                "success": true,
                "errors": null,
                "pointsRedemption": {
                  "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Verify redemption code

=== "Request"
    ```gql
    mutation (
      $consumerLoyaltyId: $String
      $code: String!
    ){
      verifyRedemptionCode(
        input: {
          consumerLoyaltyId: $consumerLoyaltyId
          code: $code
        }
      ) {
        success
        errors
      }
    }
    ```

=== "Variables"
    ```json
    {
      "consumerLoyaltyId": "59841898004705",
      "code": "..."
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "verifyRedemptionCode": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
