## The order item node

| Method               | Type                                | Description |
| -------------------- | ----------------------------------- | ----------- |
| id                   | `ID!`                               |
| pk                   | `Int`                               |
| order                | `OrderNode!`                        |
| product              | `ProductNode`                       |
| quantity             | `Int!`                              |
| numOfDiscountedUnits | `Int!`                              |
| costCurrency         | `OrderItemCostCurrency!`            |
| cost                 | `String`                            |
| isRawCost            | `Boolean!`                          |
| isCompleted          | `Boolean!`                          |
| extraInfo            | `JSONString`                        |
| createdAt            | `DateTime!`                         |
| updatedAt            | `DateTime!`                         |
| entitySource         | `OrderItemEntitySource`             |
| entitySourceId       | `String`                            |
| components           | `OrderItemComponentNodeConnection!` |
| refund               | `RefundNode`                        |

## Create an order item

=== "Request"
    ```gql
    mutation (
      $orderId: ID!
      $productId: ID!
      $quantity: Int
      $modifiers: [OrderItemComponentInput]
      $extraInfo: JSONString
    ){
      createOrder(
        input: {
          orderId: $orderId
          productId: $productId
          quantity: $quantity
          modifiers: $modifiers
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        orderItem {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "orderId": "19220112164",
      "productId": 20,
      "quantity": 2
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOrderItem": {
                "success": true,
                "errors": null,
                "orderItem": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Update an order item

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $quantity: Int
      $isCompleted: Boolean
    ){
      updateOrderItem(
        input: {
          id: $id
          quantity: $quantity
          isCompleted: $isCompleted
        }
      ) {
        errors
        success
        orderItem {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 5,
      "isCompleted": true
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateOrderItem": {
                "success": true,
                "errors": null,
                "orderItem": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete an order item

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteOrderItem(
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
      "id": 5
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteOrderItem": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
