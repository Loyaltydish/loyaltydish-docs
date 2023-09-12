## Sections

### The section node

| Method            | Type                             | Description |
| ----------------- | -------------------------------- | ----------- |
| id                | `ID!`                            |
| pk                | `Int`                            |
| store             | `StoreNode!`                     |
| name              | `String!`                        |
| costCurrency      | `SectionCostCurrency`            |
| cost              | `String`                         |
| stripeLocationId  | `String`                         |
| productCategories | `ProductCategoryNodeConnection!` |
| tables            | `TableNodeConnection!`           |
| terminals         | `TerminalNodeConnection!`        |
| costAmount        | `Float`                          |
| extraInfo         | `JSONString`                     |
| createdAt         | `DateTime!`                      |
| updatedAt         | `DateTime!`                      |

### Create a section

```gql
input TableInput {
  id: ID
  name: String!
  maxSeatsNumber: Int!
  costAmount: Decimal
  shape: String
}
```

=== "Request"
    ```gql
    mutation (
      $storeId: ID!
      $name: String!
      $costAmount: Decimal
      $productCategories: [ID]
      $tables: [TableInput]
    ){
      createSection(
        input: {
          storeId: $storeId
          name: $name
          costAmount: $costAmount
          productCategories: $productCategories
          tables: $tables
        }
      ) {
        errors
        success
        section {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "storeID": 19,
      "name": "Rooftop"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createSection": {
                "success": true,
                "errors": null,
                "section": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

### Update a section

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $costAmount: Decimal
      $productCategories: [ID]
      $tables: [TableInput]
    ){
      updateSection(
        input: {
          id: $id
          name: $name
          costAmount: $costAmount
          productCategories: $productCategories
          tables: $tables
        }
      ) {
        errors
        success
        section {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 19,
      "name": "Rooftop - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateSection": {
                "success": true,
                "errors": null,
                "section": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

### Delete a section

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteSection(
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
      "id": 19
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteSection": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Tables

### The table node

| Method         | Type                            | Description |
| -------------- | ------------------------------- | ----------- |
| id             | `ID!`                           |
| pk             | `Int`                           |
| section        | `SectionNode!`                  |
| name           | `String!`                       |
| maxSeatsNumber | `Int!`                          |
| costCurrency   | `TableCostCurrency`             |
| cost           | `String`                        |
| shape          | `TableShape!`                   |
| floorPlans     | `FloorPlanTableNodeConnection!` |
| orders         | `OrderNodeConnection!`          |
| reservations   | `ReservationNodeConnection!`    |
| costAmount     | `Float`                         |
| extraInfo      | `JSONString`                    |
| createdAt      | `DateTime!`                     |
| updatedAt      | `DateTime!`                     |

### Create a table

=== "Request"
    ```gql
    mutation (
      $sectionId: ID!
      $name: String!
      $maxSeatsNumber: Int!
      $costAmount: Decimal
    ){
      createTable(
        input: {
          sectionId: $sectionId
          name: $name
          maxSeatsNumber: $maxSeatsNumber
          costAmount: $costAmount
        }
      ) {
        errors
        success
        table {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "sectionId": 19,
      "name": "Balcony table 1"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createTable": {
                "success": true,
                "errors": null,
                "table": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

### Update a table

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $maxSeatsNumber: Int
      $costAmount: Decimal
    ){
      updateTable(
        input: {
          id: $id
          name: $name
          maxSeatsNumber: $maxSeatsNumber
          costAmount: $costAmount
        }
      ) {
        errors
        success
        table {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 10,
      "name": "Balcony table 2"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateTable": {
                "success": true,
                "errors": null,
                "table": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


### Delete a table

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      updateTable(
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
            "deleteTable": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## The floor plan node

| Method    | Type                            | Description |
| --------- | ------------------------------- | ----------- |
| id        | `ID!`                           |
| pk        | `Int`                           |
| store     | `StoreNode!`                    |
| name      | `String!`                       |
| tables    | `FloorPlanTableNodeConnection!` |
| extraInfo | `JSONString`                    |
| createdAt | `DateTime!`                     |
| updatedAt | `DateTime!`                     |


## Create a floor plan

=== "Request"
    ```gql
    mutation (
      $storeId: ID!
      $name: String
    ){
      createFloorPlan(
        input: {
          storeId: $storeId
          name: $name
        }
      ) {
        errors
        success
        floorPlan {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "storeId": 19,
      "name": "Floor plan 1"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createFloorPlan": {
                "success": true,
                "errors": null,
                "floorPlan": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Update a floor plan

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $storeId: ID
      $name: String
    ){
      updateFloorPlan(
        input: {
          id: $id
          storeId: $storeId
          name: $name
        }
      ) {
        errors
        success
        floorPlan {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 22,
      "name": "Floor plan 1 - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateFloorPlan": {
                "success": true,
                "errors": null,
                "floorPlan": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Delete a floor plan

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteFloorPlan(
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
      "id": 22
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteFloorPlan": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Add table to floor plan
Note that `extraInfo` input field should have the following data:

```json
{
  "size": {
    "h": 75,
    "w": 75
  },
  "position": {
    "x": 285,
    "y": 120
  }
}
```

=== "Request"
    ```gql
    mutation (
      $floorPlanId: ID!
      $tableId: ID!
      $extraInfo: JSONString
    ){
      createFloorPlanTable(
        input: {
          floorPlanId: $floorPlanId
          tableId: $tableId
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        floorPlanTable {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "floorPlanId": 22,
      "tableId": 10,
      "extraInfo": "{...}"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createFloorPlanTable": {
                "success": true,
                "errors": null,
                "floorPlanTable": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Update table on a floor plan

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $extraInfo: JSONString
    ){
      updateFloorPlanTable(
        input: {
          id: $id
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        floorPlanTable {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 22,
      "extraInfo": "{...}"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateFloorPlanTable": {
                "success": true,
                "errors": null,
                "floorPlanTable": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```

## Remove a table from a floor plan

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteFloorPlanTable(
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
      "id": 22
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteFloorPlanTable": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
