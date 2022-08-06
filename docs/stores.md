## Create a store

=== "Request"
    ```gql
    mutation (
        $name: String!
        $shortDescription: String
        $longDescription: String
        $location: String!
        $phoneNumber: String!
        $storeType: ID!
        $categories: [ID]!
        $logo: Upload
        $pictures: [StoreImageInput]!
        $country:String
        $state: String
        $city: String
        $street: String
        $zipCode: String
        $taxRate: Float
        $orderPreparationTimeHours: Float
        $deliveryCostPerMile: Decimal
        $deliveryCostPerMileCurrency: String
        $deliveryDistanceLimitMiles: Float
        $schedules: [StoreAvailabilityInput]!
        $customDates: [StoreCustomDateInput]
    ){
        createStore(
            input: {
                name: $name
                shortDescription: $shortDescription
                longDescription: $longDescription
                location: $location
                phoneNumber: $phoneNumber
                storeType: $storeType
                categories: $categories
                logo: $logo
                pictures: $pictures
                country: $country
                state: $state
                city: $city
                zipCode: $zipCode
                street: $street
                taxRate: $taxRate
                orderPreparationTimeHours: $orderPreparationTimeHours
                deliveryCostPerMile: $deliveryCostPerMile
                deliveryCostPerMileCurrency: $deliveryCostPerMileCurrency
                deliveryDistanceLimitMiles: $deliveryDistanceLimitMiles
                schedules: $schedules
                customDates: $customDates
            }
        ) {
            success
            errors
            store {
                id
            }
        }
    }
    ```

=== "Variables"
    ```json
    {
        "name": "Test store",
        "shortDescription": "",
        "longDescription": "",
        "location": "36.3633,6.6133",
        "phoneNumber": "+12125552368",
        "storeType": 4,
        "categories": [2],
        "logo": "",
        "pictures": [],
        "taxRate": 0.5,
        "orderPreparationTimeHours": 0.5,
        "deliveryCostPerMile": "1.00",
        "deliveryDistanceLimitMiles": 2,
        "schedules": [
            {"day": 1, "startTime": "7:00", "endTime": "12:00"},
            {"day": 1, "startTime": "12:00", "endTime": "20:00"}
        ],
        "customDates": [
            {"description": "Easter Holiday", "start": "2022-04-17", "end": "2022-04-18"}
        ]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createStore": {
                "success": true,
                "errors": null,
                "store": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Update a store

=== "Request"
    ```gql
    mutation (
        $id: ID!
        $name: String
        $location: String
        $phoneNumber: String
        $country: String
        $state: String
        $city: String
        $street: String
        $zipCode: String
        $taxRate: Float
        $shortDescription: String
        $longDescription: String
        $storeType: ID
        $categories: [ID]
        $deliveryCostPerMile: Decimal
        $deliveryCostPerMileCurrency: String
        $deliveryDistanceLimitMiles: Float
        $disableOnlineOrders: Boolean
        $orderPreparationTimeHours: Float
        $pictures: [StoreImageInput]
        $schedules: [StoreAvailabilityInput]
        $customDates: [StoreCustomDateInput]
        $logo: Upload
    ){
        updateStore(
            input: {
                id: $id
                name: $name
                location: $location
                phoneNumber: $phoneNumber
                country: $country
                state: $state
                city: $city
                street: $street
                zipCode: $zipCode
                taxRate: $taxRate
                shortDescription: $shortDescription
                longDescription: $longDescription
                storeType: $storeType
                categories: $categories
                deliveryCostPerMile: $deliveryCostPerMile
                deliveryCostPerMileCurrency: $deliveryCostPerMileCurrency
                deliveryDistanceLimitMiles: $deliveryDistanceLimitMiles
                disableOnlineOrders: $disableOnlineOrders
                orderPreparationTimeHours: $orderPreparationTimeHours
                pictures: $pictures
                schedules: $schedules
                customDates: $customDates
                logo: $logo
            }
        ) {
            success
            errors
            store {
                id
            }
        }
    }
    ```

=== "Variables"
    ```json
    {
        "id": 131,
        "name": "Edited store name"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateStore": {
                "success": true,
                "errors": null,
                "store": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Delete a store

=== "Request"
    ```gql
    mutation (
        $id: ID!
    ){
        deleteStore(
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
        "id": 131
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteStore": {
                "success": true,
                "errors": null,
            }
        }
    }
    ```



## List stores

```gql
query {
	stores{
		edges {
			node {
				pk
				id
			}
		}
	}
}
```

## Get a single store

```gql
query {
	store(id: "U3RvcmVOb2RlOjE5"){
		pk
		id
		name
	}
}
```
