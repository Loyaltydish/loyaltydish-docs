## The offer node

| Method               | Type                              | Description |
| -------------------- | --------------------------------- | ----------- |
| id                   | `ID!`                             |
| pk                   | `Int`                             |
| merchant             | `UserNode`                        |
| campaign             | `CampaignNode!`                   |
| stores               | `StoreNodeConnection!`            |
| storeGroups          | `StoreGroupNodeConnection!`       |
| products             | `ProductNodeConnection!`          |
| name                 | `String!`                         |
| shortDescription     | `String!`                         |
| longDescription      | `String!`                         |
| offerType            | `OfferOfferType!`                 |
| offerValue           | `Float!`                          |
| numOfItems           | `Int`                             |
| placement            | `OfferPlacement!`                 |
| startTime            | `DateTime!`                       |
| endTime              | `DateTime!`                       |
| redemptionCodeType   | `OfferRedemptionCodeType!`        |
| enrollmentLimit      | `Int!`                            |
| repeatable           | `Boolean!`                        |
| repeatDelayHours     | `Int`                             |
| dayStartTime         | `Time`                            |
| dayEndTime           | `Time`                            |
| daysOfWeek           | `[String]`                        |
| weather              | `String!`                         |
| earnPoints           | `Boolean!`                        |
| segmentationRules    | `JSONString`                      |
| termsAndConditions   | `String`                          |
| minimumSpendCurrency | `OfferMinimumSpendCurrency`       |
| minimumSpend         | `String`                          |
| code                 | `String`                          |
| totalRating          | `Float!`                          |
| status               | `OfferStatus!`                    |
| refreshHours         | `Int!`                            |
| redemptionIntents    | `RedemptionIntentNodeConnection!` |
| redemptions          | `RedemptionNodeConnection`        |
| pictures             | `OfferPictureNodeConnection!`     |
| offerConsumers       | `OfferConsumerNodeConnection!`    |
| minimumSpendAmount   | `Float`                           |
| consumers            | `OfferConsumerNodeConnection`     |
| extraInfo            | `JSONString`                      |
| createdAt            | `DateTime!`                       |
| updatedAt            | `DateTime!`                       |

## Create an offer

=== "Request"
    ```gql
    mutation CreateOffer(
      $stores: [ID]!
      $storeGroups: [ID]!
      $products: [ID]
      $name: String!
      $shortDescription: String!
      $longDescription: String!
      $placement: String!
      $startTime: DateTime!
      $endTime: DateTime!
      $redemptionCodeType: String!
      $enrollmentLimit: Int!
      $repeatable: Boolean!
      $dayStartTime: Time
      $dayEndTime: Time
      $daysOfWeek: [String]!
      $earnPoints: Boolean!
      $repeatDelayHours: Int
      $termsAndConditions: String
      $minimumSpend: String
      $code: String
      $pictures: [OfferImageInput]!
      $campaignId: ID!
      $weather: String!
      $offerType: String! # PERCENTAGE, FIXED_AMOUNT, BOGO
      $offerValue: Float!
      $numOfItems: Int
    ){
      createOffer(
        input: {
          stores: $stores
          storeGroups: $storeGroups
          products: $products
          name: $name
          shortDescription: $shortDescription
          longDescription: $longDescription
          placement: $placement
          startTime: $startTime
          endTime: $endTime
          redemptionCodeType: $redemptionCodeType
          enrollmentLimit: $enrollmentLimit
          repeatable: $repeatable
          dayStartTime: $dayStartTime
          dayEndTime: $dayEndTime
          daysOfWeek: $daysOfWeek
          earnPoints: $earnPoints
          repeatDelayHours: $repeatDelayHours
          termsAndConditions: $termsAndConditions
          minimumSpend: $minimumSpend
          code: $code
          pictures: $pictures
          campaign: $campaignId
          weather: $weather
          offerType: $offerType
          offerValue: $offerValue
          numOfItems: $numOfItems
        }
      ) {
        success
        errors
        offer {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "20% off Birth day offer",
      "campaign": 3,
      "longDescription": "20% off Birth day offer",
      "shortDescription": "20% off Birth day offer",
      "pictures": [],
      "termsAndConditions": "",
      "segmentationRules": "[]",
      "offerType": "PERCENTAGE",
      "offerValue": 20,
      "numOfItems": 1,
      "products": [],
      "redemptionCodeType": "AUTOGENERATED",
      "code": "",
      "minimumSpend": "0.00",
      "earnPoints": true,
      "repeatDelayHours": 48,
      "repeatable": true,
      "stores": ["1", "9", "2", "10", "15", "13", "7", "12", "8", "11", "14"],
      "storeGroups": [],
      "enrollmentLimit": 100,
      "enrollmentUnlimited": true,
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
      "placement": "TOP",
      "weather": "Sunny",
      "campaignId": 1
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOffer": {
                "success": true,
                "errors": null,
                "offer": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Update an offer

=== "Request"
    ```gql
    mutation CreateOffer(
      $id: ID!
      $stores: [ID]
      $storeGroups: [ID]
      $products: [ID]
      $name: String
      $shortDescription: String
      $longDescription: String
      $placement: String
      $startTime: DateTime
      $endTime: DateTime
      $redemptionCodeType: String
      $enrollmentLimit: Int
      $repeatable: Boolean
      $dayStartTime: Time
      $dayEndTime: Time
      $daysOfWeek: [String]
      $earnPoints: Boolean
      $repeatDelayHours: Int
      $termsAndConditions: String
      $minimumSpend: String
      $code: String
      $pictures: [OfferImageInput]
      $campaignId: ID
      $weather: String
      $offerType: String # PERCENTAGE, FIXED_AMOUNT, BOGO
      $offerValue: Float
      $numOfItems: Int
    ){
      updateOffer(
        input: {
          id: $id
          stores: $stores
          storeGroups: $storeGroups
          products: $products
          name: $name
          shortDescription: $shortDescription
          longDescription: $longDescription
          placement: $placement
          startTime: $startTime
          endTime: $endTime
          redemptionCodeType: $redemptionCodeType
          enrollmentLimit: $enrollmentLimit
          repeatable: $repeatable
          dayStartTime: $dayStartTime
          dayEndTime: $dayEndTime
          daysOfWeek: $daysOfWeek
          earnPoints: $earnPoints
          repeatDelayHours: $repeatDelayHours
          termsAndConditions: $termsAndConditions
          minimumSpend: $minimumSpend
          code: $code
          pictures: $pictures
          campaign: $campaignId
          weather: $weather
          offerType: $offerType
          offerValue: $offerValue
          numOfItems: $numOfItems
        }
      ) {
        success
        errors
        offer {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
        "name": "Editd offer name"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateOffer": {
                "success": true,
                "errors": null,
                "offer": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```


## Delete an offer

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteOffer(
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
        "id": 5
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteOffer": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## List Offers

```gql
query {
	offers{
		edges {
			node {
				pk
				id
			}
		}
	}
}
```

## Get a single offer

```gql
query {
	offer(id: "U3RvcmVOb2RlOjE5"){
		pk
		id
		name
	}
}
```
