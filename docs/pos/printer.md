## The printer node

| Method                | Type                     | Description |
| --------------------- | ------------------------ | ----------- |
| id                    | `ID!`                    |
| pk                    | `Int`                    |
| terminal              | `TerminalNode!`          |
| name                  | `String!`                |
| connectionType        | `PrinterConnectionType!` |
| ipAddress             | `String`                 |
| macAddress            | `String`                 |
| port                  | `Int!`                   |
| serialNumber          | `String`                 |
| registrationCode      | `String`                 |
| stripeReader          | `JSONString`             |
| connectionTypeDisplay | `String`                 |
| extraInfo             | `JSONString`             |
| createdAt             | `DateTime!`              |
| updatedAt             | `DateTime!`              |



## Add a printer

=== "Request"
    ```gql
    mutation (
      $terminalId: ID!
      $name: String!
      $connectionType: String! # WIFI, BLUETOOTH
      $macAddress: String
      $ipAddress: String
      $port: Int!
      $serialNumber: String
      $registrationCode: String
    ){
      createPrinter(
        input: {
          terminalId: $terminalId
          name: $name
          connectionType: $connectionType
          macAddress: $macAddress
          ipAddress: $ipAddress
          port: $port
          serialNumber: $serialNumber
          registrationCode: $registrationCode
        }
      ) {
        errors
        success
        printer {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "terminalId": 10,
      "name": "Printer #1",
      "connectionType": "WIFI",
      "ipAddress": "192.1.1.6",
      "port": 9999
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createPrinter": {
                "success": true,
                "errors": null,
                "printer": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Update a printer

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $terminalId: ID
      $name: String
      $connectionType: String # WIFI, BLUETOOTH
      $macAddress: String
      $ipAddress: String
      $port: Int
      $serialNumber: String
    ){
      updatePrinter(
        input: {
          id: $id
          terminalId: $terminalId
          name: $name
          connectionType: $connectionType
          macAddress: $macAddress
          ipAddress: $ipAddress
          port: $port
          serialNumber: $serialNumber
        }
      ) {
        errors
        success
        printer {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 5,
      "name": "Printer #1 - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updatePrinter": {
                "success": true,
                "errors": null,
                "printer": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a printer

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deletePrinter(
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
            "deletePrinter": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
