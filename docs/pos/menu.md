## The menu node

| Method             | Type                             | Description |
| ------------------ | -------------------------------- | ----------- |
| id                 | `ID!`                            |
| pk                 | `Int`                            |
| merchant           | `MerchantNode!`                  |
| name               | `String!`                        |
| description        | `String!`                        |
| startTime          | `Time!`                          |
| endTime            | `Time!`                          |
| productsCategories | `ProductCategoryNodeConnection!` |
| extraInfo          | `JSONString`                     |
| createdAt          | `DateTime!`                      |
| updatedAt          | `DateTime!`                      |


## Create a menu

=== "Request"
    ```gql
    mutation (
      $name: String!
      $description: String!
      $startTime: Time!
      $endTime: Time!
      $extraInfo: JSONString
    ){
      createMenu(
        input: {
          name: $name
          description: $description
          startTime: $startTime
          endTime: $endTime
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        menu {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Breakfast",
      "description": "Menu description",
      "startTime": "07:00",
      "endTime": "12:00",
      "extraInfo": "{}"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createMenu": {
                "success": true,
                "errors": null,
                "menu": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## update a menu

=== "Request"
    ```gql
    mutation (
      $id: ID
      $name: String
      $description: String
      $startTime: Time
      $endTime: Time
      $extraInfo: JSONString
    ){
      updateMenu(
        input: {
          id: $id
          name: $name
          description: $description
          startTime: $startTime
          endTime: $endTime
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        menu {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 10,
      "name": "Breakfast - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateMenu": {
                "success": true,
                "errors": null,
                "menu": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Delete a menu

=== "Request"
    ```gql
    mutation (
      $id: ID
    ){
      deleteMenu(
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
            "deleteMenu": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
