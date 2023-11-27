## Send receipt

=== "Request"
    ```gql
    mutation (
      $orderId: String!
      $customerEmail: String
      $customerPhoneNumber: String
    ){
      sendOrderReceipt(
        input: {
          orderId: $orderId
          customerEmail: $customerEmail
          customerPhoneNumber: $customerPhoneNumber
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
      "orderId": "19220112164",
      "customerEmail": "cutomer@email.com",
      "customerPhoneNumber": "+1111111111"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "sendOrderReceipt": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
