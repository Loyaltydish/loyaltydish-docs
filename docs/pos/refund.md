## The refund node

| Method    | Type            | Description |
| --------- | --------------- | ----------- |
| id        | `ID!`           |
| order     | `OrderNode `    |
| orderItem | `OrderItemNode` |
| reason    | `String!`       |
| createdAt | `DateTime!`     |
| pk        | `Int`           |



## Refund order

=== "Request"
    ```gql
    mutation (
      $orderId: ID!
      $amount: Decimal
      $amountCurrency: String
      $reason: String
    ){
      createOrderRefund(
        input: {
          orderId: $orderId
          amount: $amount
          amountCurrency: $amountCurrency
          reason: $reason
        }
      ) {
        errors
        success
        refund {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "orderId": "19220112164",
      "reason": "Reason for refund"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOrderRefund": {
                "success": true,
                "errors": null,
                "refund": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Partial refund

=== "Request"
    ```gql
    mutation (
      $orderId: ID!
      $amount: Decimal
      $amountCurrency: String
      $reason: String
    ){
      createOrderRefund(
        input: {
          orderId: $orderId
          amount: $amount
          amountCurrency: $amountCurrency
          reason: $reason
        }
      ) {
        errors
        success
        refund {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "orderId": "19220112164",
      "amount": "10.00",
      "amountCurrency": "USD",
      "reason": "Reason for refund"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOrderRefund": {
                "success": true,
                "errors": null,
                "refund": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Refund order items

=== "Request"
    ```gql
    mutation (
      $orderItems: [ID]!
    ){
      createOrderItemsRefund(
        input: {
          orderItems: $orderItems
        }
      ) {
        errors
        success
        refunds {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "orderItems": [45, 46]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOrderItemsRefund": {
                "success": true,
                "errors": null,
                "refund": [
                  {
                    "id": "U3RvcmVOb2RlOjE5"
                  },
                  {
                    "id": "U8YfghVOb2HkOjB9"
                  }
                ]
            }
        }
    }
    ```
