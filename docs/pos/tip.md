## Create a tip

=== "Request"
    ```gql
    mutation (
      $orderId: ID!
      $amount: Decimal!
      $amountCurrency: String
    ){
      createTip(
        input: {
          orderId: $orderId
          amount: $amount
          amountCurrency: $amountCurrency
        }
      ) {
        errors
        success
        tip {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "orderId": "19220112164",
      "amount": "5.00"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createTip": {
                "success": true,
                "errors": null,
                "tip": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Update a tip

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $amount: Decimal
      $amountCurrency: String
    ){
      updateTip(
        input: {
          id: $id
          amount: $amount
          amountCurrency: $amountCurrency
        }
      ) {
        errors
        success
        tip {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 10,
      "amount": "6.00"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateTip": {
                "success": true,
                "errors": null,
                "tip": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a tip

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteTip(
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
      "id": 10
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteTip": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
