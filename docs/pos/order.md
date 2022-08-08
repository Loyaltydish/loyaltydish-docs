## The order node

| Method               | Type                           | Description |
| -------------------- | ------------------------------ | ----------- |
| id                   | `ID!`                          |
| extraInfo            | `JSONString`                   |
| isActive             | `Boolean!`                     |
| deletedAt            | `DateTime`                     |
| orderId              | `String`                       |
| consumer             | `ConsumerNode`                 |
| merchant             | `MerchantNode`                 |
| waiter               | `MerchantNode`                 |
| phoneNumber          | `String`                       |
| store                | `StoreNode`                    |
| orderType            | `OrderTypeNode`                |
| state                | `OrderStateNode`               |
| pickupDt             | `DateTime`                     |
| paymentType          | `OrderPaymentType!`            |
| cashReceivedCurrency | `OrderCashReceivedCurrency`    |
| cashReceived         | `String`                       |
| changeCurrency       | `OrderChangeCurrency`          |
| change               | `String`                       |
| numOfGuests          | `Int`                          |
| taxCurrency          | `OrderTaxCurrency!`            |
| tax                  | `String`                       |
| isRawTotal           | `Boolean!`                     |
| totalCurrency        | `OrderTotalCurrency!`          |
| total                | `String`                       |
| completed            | `Boolean!`                     |
| completedAt          | `DateTime`                     |
| createdAt            | `DateTime!`                    |
| updatedAt            | `DateTime!`                    |
| table                | `TableNode`                    |
| entitySource         | `OrderEntitySource`            |
| entitySourceId       | `String`                       |
| items                | `OrderItemNodeConnection!`     |
| tips                 | `TipNodeConnection!`           |
| delivery             | `DeliveryNode`                 |
| discounts            | `OrderDiscountNodeConnection!` |
| refund               | `RefundNode`                   |
| reservation          | `ReservationNode`              |
| pk                   | `Int`                          |
| cashReceivedAmount   | `Float`                        |
| changeAmount         | `Float`                        |
| paymentTypeDisplay   | `String`                       |


## List order types

=== "Request"
    ```gql
    {
      orderTypes {
        edges {
          node {
            id
            pk
            name
          }
        }
      }
    }
    ```

=== "Response"
    ```json
    {
      "data": {
        "orderTypes": {
          "edges": [
            {
              "node": {
                "id": "T3JkZXJUeXBlTm9kZTox",
                "pk": 1,
                "name": "In Store"
              }
            },
            {
              "node": {
                "id": "T3JkZXJUeXBlTm9kZToy",
                "pk": 2,
                "name": "To Go"
              }
            },
            {
              "node": {
                "id": "T3JkZXJUeXBlTm9kZToz",
                "pk": 3,
                "name": "Online"
              }
            }
          ]
        }
      }
    }
    ```

## Create an order

=== "Request"
    ```gql
    mutation (
      $storeId: ID!
      $consumerId: ID
      $phoneNumber: String
      $numOfGuests: Int
      $orderTypeId: ID
      $waiterId: ID
      $pickupDt: DateTime
      $deliveryLocation: String
      $paymentType: String
    ){
      createOrder(
        input: {
          storeId: $storeId
          consumerId: $consumerId
          phoneNumber: $phoneNumber
          numOfGuests: $numOfGuests
          orderTypeId: $orderTypeId
          waiterId: $waiterId
          pickupDt: $pickupDt
          deliveryLocation: $deliveryLocation
          paymentType: $paymentType
        }
      ) {
        errors
        success
        order {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "storeId": 14,
      "consumerId": 20,
      "orderTypeId": 2,
      "waiterId": 80
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOrder": {
                "success": true,
                "errors": null,
                "order": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Update an order

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $phoneNumber: String
      $storeId: ID!
      $orderTypeId: ID
      $paymentType: String
      $pickupDt: DateTime
      $deliveryLocation: String
      $waiterId: ID
      $consumerId: ID
      $tableId: ID
      $numOfGuests: Int
    ){
      updateOrder(
        input: {
          id: $id
          storeId: $storeId
          consumerId: $consumerId
          phoneNumber: $phoneNumber
          numOfGuests: $numOfGuests
          tableId: $tableId
          orderTypeId: $orderTypeId
          waiterId: $waiterId
          pickupDt: $pickupDt
          deliveryLocation: $deliveryLocation
          paymentType: $paymentType
        }
      ) {
        errors
        success
        order {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 25,
      "tableId": 10
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateOrder": {
                "success": true,
                "errors": null,
                "order": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Delete an order

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      updateOrder(
        input: {
          id: $id
        }
      ) {
        errors
        success
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 25
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteOrder": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
