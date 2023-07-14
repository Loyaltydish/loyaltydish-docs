## The terminal node

| Method    | Type                     | Description |
| --------- | ------------------------ | ----------- |
| id        | `ID!`                    |
| pk        | `Int`                    |
| section   | `SectionNode!`           |
| name      | `String!`                |
| key       | `String!`                |
| printers  | `PrinterNodeConnection!` |
| extraInfo | `JSONString`             |
| createdAt | `DateTime!`              |
| updatedAt | `DateTime!`              |

## Add a terminal

=== "Request"
    ```gql
    mutation (
      $sectionId: ID!
      $name: String!
    ){
      createTerminal(
        input: {
          sectionId: $sectionId
          name: $name
        }
      ) {
        errors
        success
        terminal {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "sectionId": 1,
      "productId": "Terminal 01"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createTerminal": {
                "success": true,
                "errors": null,
                "terminal": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Sign in to a terminal

=== "Request"
    ```gql
    mutation (
      $key: String!
    ){
      terminalSignIn(
        input: {
          key: $key
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
      "key": "67MU4G93RRYH"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "terminalSignIn": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Update a terminal

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $sectionId: ID
      $name: String
    ){
      updateTerminal(
        input: {
          id: $id
          sectionId: $sectionId
          name: $name
        }
      ) {
        errors
        success
        terminal {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 1,
      "productId": "Terminal 01 - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateTerminal": {
                "success": true,
                "errors": null,
                "terminal": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a terminal

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteTerminal(
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
            "deleteTerminal": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
