## The product node

| Method                | Type                                    | Description |
| --------------------- | --------------------------------------- | ----------- |
| id                    | `ID!`                                   |
| pk                    | `Int `                                  |
| name                  | `String!`                               |
| shortDescription      | `String!`                               |
| description           | `String!`                               |
| category              | `ProductCategoryNode `                  |
| pictures              | `ProductPictureNodeConnection!`         |
| price                 | `String `                               |
| priceCurrency         | `ProductPriceCurrency!`                 |
| priceAmount           | `Float `                                |
| previousPrice         | `Decimal `                              |
| previousPriceCurrency | `ProductPreviousPriceCurrency `         |
| quantities            | `ProductQuantityNodeConnection!`        |
| availabilities        | `ProductAvailabilityNodeConnection!`    |
| outOfStock            | `Boolean!`                              |
| stores                | `StoreNodeConnection!`                  |
| storeGroups           | `StoreGroupNodeConnection!`             |
| allStores             | `StoreNodeConnection `                  |
| modifiersGroups       | `ProductComponentsGroupNodeConnection ` |
| appliedTaxes          | `AppliedTaxNodeConnection`              |
| extraInfo             | `JSONString `                           |
| createdAt             | `DateTime!`                             |
| updatedAt             | `DateTime!`                             |


## List product categories

```gql
{
	productCategories {
		edges {
			node {
				pk
				name
			}
		}
	}
}
```


## Create a product

=== "Request"
    ```gql
    mutation (
      $name: String!
      $categoryId: ID!
      $productComponentsGroups: [ID]!
      $price: Decimal!
      $priceCurrency: String
      $outOfStock: Boolean
      $shortDescription: String!
      $description: String!
      $stores: [ID]!
      $storeGroups: [ID]!
      $pictures: [ProductImageInput]
      $extraInfo: JSONString
    ){
      createProduct(
        input: {
          name: $name
          categoryId: $categoryId
          productComponentsGroups: $productComponentsGroups
          price: $price
          priceCurrency: $priceCurrency
          outOfStock: $outOfStock
          shortDescription: $shortDescription
          description: $description
          stores: $stores
          storeGroups: $storeGroups
          pictures: $pictures
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        product {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Pizza",
      "categoryId": 56,
      "productComponentsGroups": [5, 9, 8, 6],
      "price": "2.00",
      "priceCurrency": "USD",
      "outOfStock": false,
      "shortDescription": "Pizza short description",
      "description": "Pizza long description",
      "stores": [1, 2, 3],
      "storeGroups": [5, 8, 7]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProduct": {
                "success": true,
                "errors": null,
                "product": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```



## Update a product

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $categoryId: ID
      $productComponentsGroups: [ID]
      $price: Decimal
      $priceCurrency: String
      $outOfStock: Boolean
      $shortDescription: String
      $description: String
      $stores: [ID]
      $storeGroups: [ID]
      $extraInfo: JSONString
    ){
      createProduct(
        input: {
          id: $id
          name: $name
          categoryId: $categoryId
          productComponentsGroups: $productComponentsGroups
          price: $price
          priceCurrency: $priceCurrency
          outOfStock: $outOfStock
          shortDescription: $shortDescription
          description: $description
          stores: $stores
          storeGroups: $storeGroups
          extraInfo: $extraInfo
        }
      ) {
        errors
        success
        product {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 90,
      "name": "Pizza - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProduct": {
                "success": true,
                "errors": null,
                "product": {
                  "id": "U3RvcmVOb2RlOjE5"
                }
            }
        }
    }
    ```


## Delete a product

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProduct(
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
      "id": 90
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProduct": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Add product picture

=== "Request"
    ```gql
    mutation (
      $productId: ID!
      $picture: Upload!
      $order: Int!
    ){
      createProductPicture(
        input: {
          productId: $productId
          picture: $picture
          order: $order
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
      "productId": 18,
      "picture": null,
      "order": 1
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProductPicture": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Update product picture

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $picture: Upload
      $order: Int
    ){
      updateProductPicture(
        input: {
          id: $id
          picture: $picture
          order: $order
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
      "id": 18,
      "picture": null,
      "order": 2
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProductPicture": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Delete product picture

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProductPicture(
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
      "id": 18
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProductPicture": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Add product quantity

=== "Request"
    ```gql
    mutation (
      $productId: ID!
      $storeId: ID!
      $order: Int!
    ){
      createProductQuantity(
        input: {
          productId: $productId
          storeId: $storeId
          quantity: $quantity
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
      "productId": 18,
      "storeId": 22,
      "quantity": 100
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProductQuantity": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Update product quantity

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $productId: ID
      $storeId: ID
      $order: Int
    ){
      updateProductQuantity(
        input: {
          id: $id
          productId: $productId
          storeId: $storeId
          quantity: $quantity
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
      "id": 2,
      "productId": 18,
      "storeId": 22,
      "quantity": 100
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProductQuantity": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Delete product quantity

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProductQuantity(
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
      "id": 2
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProductQuantity": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Add product availability

=== "Request"
    ```gql
    mutation (
      $productId: ID!
      $storeId: ID!
      $startTime: Time!
      $endTime: Time!
    ){
      createProductAvailability(
        input: {
          productId: $productId
          storeId: $storeId
          startTime: $startTime
          endTime: $endTime
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
      "productId": 18,
      "storeId": 22,
      "startTime": "10:00",
      "endTime": "13:00"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createProductAvailability": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Update product availability

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $storeId: ID
      $startTime: Time
      $endTime: Time
    ){
      updateProductAvailability(
        input: {
          id: $id
          storeId: $storeId
          startTime: $startTime
          endTime: $endTime
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
      "id": 18,
      "storeId": 22,
      "startTime": "10:00",
      "endTime": "13:00"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateProductAvailability": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Delete product availability

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteProductAvailability(
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
      "id": 18
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteProductAvailability": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## List product taxes

```gql
query ($id: ID!){
	product(id: $id) {
		appliedTaxes {
			edges {
				node {
					taxRate {
						name
						taxType
						valueType
						valueAmount
					}
				}
			}
		}
	}
}
```