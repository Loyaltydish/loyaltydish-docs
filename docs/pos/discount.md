## The discount node

| Method           | Type                   | Description |
| ---------------- | ---------------------- | ----------- |
| id               | `ID!`                  |
| pk               | `Int`                  |
| order            | `OrderNode!`           |
| pointsRedemption | `PointsRedemptionNode` |
| stampsRedemption | `StampsRedemptionNode` |
| offerRedemption  | `RedemptionNode`       |
| createdAt        | `DateTime!`            |
| updatedAt        | `DateTime!`            |


## Add discount to order

=== "Request"
    ```gql
    mutation (
      $orderId: ID!
      $redemptionCode: String!
    ){
      createOrderDiscount(
        input: {
          orderId: $orderId
          redemptionCode: $redemptionCode
        }
      ) {
        errors
        success
        discount {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "orderId": "19220112164",
      "redemptionCode": "7782878702082007"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createOrderDiscount": {
                "success": true,
                "errors": null,
                "discount": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Remove discount from order

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteOrderDiscount(
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
            "deleteOrderDiscount": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Verify discount code

### Input

| Field            | Type                             | Description |
| ---------------- | -------------------------------- | ----------- |
| code             | `String!`                        | Discount code
| subtotal         | `Decimal!`                       | Order subtotal 
| items            | `[VerifyDiscountCodeItemsInput]` | List of `productId` and `quantity`
| storeId          | `ID!`                            | Store id
| consumerId       | `ID`                             | Not required, used when calling the API as a merchant


### Mutation

=== "Request"
    ```gql
    mutation (
      $code: String!
      $subtotal: Decimal!
      $items: [VerifyDiscountCodeItemsInput]
      $storeId: ID!
      $consumerId: ID
    ){
      verifyDiscountCode(input: {
        code : $code,
        subtotal: $subtotal,
        items: $items,
        storeId: $storeId,
        consumerId: $consumerId
        
      }) {
        success
        errors
      }
    }
    ```

=== "Variables"
    ```json
    {
      "code" : "CCEHX9ZF",
      "subtotal": "10.00",
      "items": [{
        "productId": 12,
        "quantity": 2
      }],
      "storeId": 9,
      "consumerId": 3
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "verifyDiscountCode": {
                "success": true,
                "errors": null
            }
        }
    }
 