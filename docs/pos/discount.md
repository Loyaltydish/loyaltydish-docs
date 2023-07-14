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
