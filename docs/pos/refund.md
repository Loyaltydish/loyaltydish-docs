## The refund node

| Method    | Type            | Description |
| --------- | --------------- | ----------- |
| id        | `ID!`           |
| order     | `OrderNode `    |
| orderItem | `OrderItemNode` |
| isCash    | `Boolean`       |
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
      $orderItems: [OrderItemRefundInput]!
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
      "orderItems": [
        { "orderItemId": 45, "reason": "some reason" },
        { "orderItemId": 46 }
      ]
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

## Cash refund
Setting `isCash` to `true` will make all the previously mentioned scenarios to cash refunds.

=== "Request"
    ```gql
    mutation (
      $orderItems: [OrderItemRefundInput]!
      $isCash: Boolean
    ){
      createOrderItemsRefund(
        input: {
          orderItems: $orderItems
          isCash: $isCash
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
      "orderItems": [
        { "orderItemId": 45, "reason": "some reason" },
        { "orderItemId": 46 }
      ],
      "isCash": true
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
