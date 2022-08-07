LoyaltyDish supports 3 payment types: Credit card (Stripe), PayPal and Cash.


## Checkout mutation

```gql
mutation (
  $id: ID!
  $paymentType: String!
  $cashReceived: Decimal
  $cashReceivedCurrency: String
  $change: Decimal
  $changeCurrency: String
  $stripePaymentMethodId: String
  $consumerPaypalEmail: String
){
  checkoutOrder(
    input: {
      id: $id
      paymentType: $paymentType
      cashReceived: $cashReceived
      cashReceivedCurrency: $cashReceivedCurrency
      change: $change
      changeCurrency: $changeCurrency
      stripePaymentMethodId: $stripePaymentMethodId
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

## Credit card checkout

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $paymentType: String!
      $cashReceived: Decimal
      $cashReceivedCurrency: String
      $change: Decimal
      $changeCurrency: String
      $stripePaymentMethodId: String
      $consumerPaypalEmail: String
    ){
      checkoutOrder(
        input: {
          id: $id
          paymentType: $paymentType
          cashReceived: $cashReceived
          cashReceivedCurrency: $cashReceivedCurrency
          change: $change
          changeCurrency: $changeCurrency
          stripePaymentMethodId: $stripePaymentMethodId
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
      "paymentType": "CREDIT_CARD",
      "stripePaymentMethodId": "pm_1LUGLo2eZvKYlo2CO9peySAz"
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
      $cashReceived: Decimal
      $cashReceivedCurrency: String
      $change: Decimal
      $changeCurrency: String
      $stripePaymentMethodId: String
      $consumerPaypalEmail: String
    ){
      checkoutOrder(
        input: {
          id: $id
          paymentType: $paymentType
          cashReceived: $cashReceived
          cashReceivedCurrency: $cashReceivedCurrency
          change: $change
          changeCurrency: $changeCurrency
          stripePaymentMethodId: $stripePaymentMethodId
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
      $stripePaymentMethodId: String
      $consumerPaypalEmail: String
    ){
      checkoutOrder(
        input: {
          id: $id
          paymentType: $paymentType
          cashReceived: $cashReceived
          cashReceivedCurrency: $cashReceivedCurrency
          change: $change
          changeCurrency: $changeCurrency
          stripePaymentMethodId: $stripePaymentMethodId
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
