## The modifier node

| Method               | Type                                    | Description |
| -------------------- | --------------------------------------- | ----------- |
| id                   | `ID!`                                   |
| pk                   | `Int`                                   |
| merchant             | `MerchntNode!`                          |
| name                 | `String!`                               |
| shortDescription     | `String!`                               |
| description          | `String!`                               |
| pictures             | `ProductComponentPictureNodeConection!` |
| price                | `String`                                |
| priceCurrency        | `ProductComponentPriceCrrency!`         |
| priceAmount          | `Float`                                 |
| outOfStock           | `Boolean!`                              |
| order                | `Int!`                                  |
| groups               | `ProductComponentsGroupNodeConection!`  |
| orderItemsComponents | `OrderItemComponentNodeConection!`      |
| extraInfo            | `JSOString`                             |
| createdAt            | `DateTime!`                             |
| updatedAt            | `DateTime!`                             |


## Create a modifier

=== "Request"
    ```gql
    mutation (
      $name: String!
      $price: Decimal!
      $priceCurrency: String
      $outOfStock: Boolean
      $shortDescription: String!
      $description: String!
      $order: Int!
      $groups: [ID]!
    ){
      createProductComponent(
        input: {
          name: $name
          price: $price
          priceCurrency: $priceCurrency
          outOfStock: $outOfStock
          shortDescription: $shortDescription
          description: $description
          order: $order
          groups: $groups
        }
      ) {
        errors
        success
        modifier {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Cheese",
      "price": "1.00",
      "priceCurrency": "USD",
      "outOfStock": false,
      "shortDescription": "Cheese description",
      "description": "Cheese long description",
      "order": 2,
      "picture": null,
      "groups": [12, 18, 20]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProductComponent": {
                "success": true,
                "errors": null,
                "modifier": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Update a modifier

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $price: Decimal
      $priceCurrency: String
      $outOfStock: Boolean
      $shortDescription: String
      $description: String
      $order: Int
      $groups: [ID]
    ){
      updateProductComponent(
        input: {
          id: $id
          name: $name
          price: $price
          priceCurrency: $priceCurrency
          outOfStock: $outOfStock
          shortDescription: $shortDescription
          description: $description
          order: $order
          groups: $groups
        }
      ) {
        errors
        success
        modifier {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 100,
      "name": "Cheese - edited",
      "price": "2.00",
      "priceCurrency": "USD"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProductComponent": {
                "success": true,
                "errors": null,
                "modifier": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a modifier

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProductComponent(
        input: {
          id: $id
        }
      ) {
        errors
        success
        modifier {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 100
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProductComponent": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Create a modifier picture

=== "Request"
    ```gql
    mutation (
      $productComponentId: ID!
      $picture: Upload!
      $order: Int!
    ){
      createProductComponentPicture(
        input: {
          productComponentId: $productComponentId
          picture: $picture
          order: $order
        }
      ) {
        errors
        success
        productComponentPicture {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "productComponentId": 15,
      "picture": null,
      "order": 3
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProductComponentPicture": {
                "success": true,
                "errors": null,
                "productComponentPicture": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Update a modifier picture

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $picture: Upload
      $order: Int
    ){
      updateProductComponentPicture(
        input: {
          id: $id
          picture: $picture
          order: $order
        }
      ) {
        errors
        success
        productComponentPicture {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 15,
      "picture": null,
      "order": 3
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProductComponentPicture": {
                "success": true,
                "errors": null,
                "productComponentPicture": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a modifier picture

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProductComponentPicture(
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
      "id": 15
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProductComponentPicture": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## the modifier group node

| Method             | Type                              | Description |
| ------------------ | --------------------------------- | ----------- |
| id                 | `ID!`                             |
| extraInfo          | `JSONString`                      |
| isActive           | `Boolean!`                        |
| createdAt          | `DateTime!`                       |
| updatedAt          | `DateTime!`                       |
| deletedAt          | `DateTime`                        |
| merchant           | `MerchantNode!`                   |
| components         | `ProductComponentNodeConnection!` |
| name               | `String!`                         |
| description        | `String!`                         |
| isRequired         | `Boolean!`                        |
| maxNumOfComponents | `Int!`                            |
| minNumOfComponents | `Int!`                            |
| products           | `ProductNodeConnection!`          |
| pk                 | `Int`                             |
| modifiers          | `ProductComponentNodeConnection`  |


## Create a modifier group

=== "Request"
    ```gql
    mutation (
      $name: String!
      $description: String!
      $isRequired: Boolean
      $maxNumOfComponents: Int!
      $minNumOfComponents: Int!
      $components: [ID]
      $products: [ID]
      $extraInfo: JSONString
    ){
      createProductComponentsGroup(
        input: {
          name: $name
          description: $description
          isRequired: $isRequired
          maxNumOfComponents: $maxNumOfComponents
          minNumOfComponents: $minNumOfComponents
          components: $components
          products: $products
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        modifiersGroup {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Toppings",
      "description": "Your toppings",
      "isRequired": false,
      "maxNumOfComponents": 10,
      "minNumOfComponents": 1,
      "components": [1, 2, 4, 5],
      "products": [100, 45, 48],
      "extraInfo": "{}"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProductComponentsGroup": {
                "success": true,
                "errors": null,
                "productComponentsGroup": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Update a modifier group

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $description: String
      $isRequired: Boolean
      $maxNumOfComponents: Int
      $minNumOfComponents: Int
    ){
      updateProductComponentsGroup(
        input: {
          id: $id
          name: $name
          description: $description
          isRequired: $isRequired
          maxNumOfComponents: $maxNumOfComponents
          minNumOfComponents: $minNumOfComponents
        }
      ) {
        errors
        success
        modifiersGroup {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 1,
      "name": "Toppings - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProductComponentsGroup": {
                "success": true,
                "errors": null,
                "productComponentsGroup": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a modifier group

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProductComponentsGroup(
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
      "id": 1
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProductComponentsGroup": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
