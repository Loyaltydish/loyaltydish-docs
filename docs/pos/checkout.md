LoyaltyDish supports 3 payment types: Credit card, PayPal and Cash.


## Checkout mutation

```gql
mutation (
  $id: ID!
  $paymentType: String!
  $cashReceived: Decimal
  $cashReceivedCurrency: String
  $change: Decimal
  $changeCurrency: String
  $consumerPaypalEmail: String
  $paymentGatewayParams: JSONString
){
  checkoutOrder(
    input: {
      id: $id
      paymentType: $paymentType
      cashReceived: $cashReceived
      cashReceivedCurrency: $cashReceivedCurrency
      change: $change
      changeCurrency: $changeCurrency
      consumerPaypalEmail: $consumerPaypalEmail
      paymentGatewayParams: $paymentGatewayParams
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

## Credit card checkout
`paymentGatewayParams` depends in the payment gateway you configured for your system
Currently, there are 3 available payment gateways: Stripe, Square, Razorpay
```json
// Stripe params schema
{
  "payment_method_id": {
      "type": "string",
  },
}

// Square params schema
{
  "source_id": {
      "type": "string",
  }
}

// Razorpay params schema
{
  "payment_id": {
    "type": "string",
  }
}
```

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $paymentType: String!
      $paymentGatewayParams: JSONString
    ){
      checkoutOrder(
        input: {
          id: $id
          paymentType: $paymentType
          paymentGatewayParams: $paymentGatewayParams
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
      "id": 15,
      "paymentType": "CREDIT_CARD",
      "paymentGatewayParams": "{\"payment_method_id\": \"pm_1LUGLo2eZvKYlo2CO9peySAz\""
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "checkoutOrder": {
                "success": true,
                "errors": null,
                "order": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## PayPal checkout

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $paymentType: String!
      $consumerPaypalEmail: String
    ){
      checkoutOrder(
        input: {
          id: $id
          paymentType: $paymentType
          consumerPaypalEmail: $consumerPaypalEmail
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
      "id": 15,
      "paymentType": "PAYPAL",
      "consumerPaypalEmail": "customer@gmail.com"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "checkoutOrder": {
                "success": true,
                "errors": null,
                "order": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Cash checkout

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $paymentType: String!
      $cashReceived: Decimal
      $cashReceivedCurrency: String
      $change: Decimal
      $changeCurrency: String
    ){
      checkoutOrder(
        input: {
          id: $id
          paymentType: $paymentType
          cashReceived: $cashReceived
          cashReceivedCurrency: $cashReceivedCurrency
          change: $change
          changeCurrency: $changeCurrency
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
      "id": 15,
      "paymentType": "CASH",
      "cashReceived": "20.00",
      "cashReceivedCurrency": "USD",
      "change": "15.00",
      "changeCurrency": "USD"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "checkoutOrder": {
                "success": true,
                "errors": null,
                "order": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```
