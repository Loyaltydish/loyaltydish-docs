## Create store group

=== "Request"
    ```gql
    mutation (
        $name: String!
        $stores: [ID]
    ){
        createStoreGroup(
            input: {
                name: $name
                stores: $stores
            }
        ) {
            success
            errors
            storeGroup {
                id
            }
        }
    }
    ```

=== "Variables"
    ```json
    {
        "name": "Test store group",
        "stores": [100, 154, 123]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createStoreGroup": {
                "success": true,
                "errors": null,
                "storeGroup": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Update store group

=== "Request"
    ```gql
    mutation (
        $id: ID!
        $name: String
        $stores: [ID]
    ){
        updateStoreGroup(
            input: {
                id: $id
                name: $name
                stores: $stores
            }
        ) {
            success
            errors
            storeGroup {
                id
            }
        }
    }
    ```

=== "Variables"
    ```json
    {
        "id": 4,
        "name": "Test store group",
        "stores": [100, 154, 123]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateStoreGroup": {
                "success": true,
                "errors": null,
                "storeGroup": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Delete store group

=== "Request"
    ```gql
    mutation (
        $id: ID!
    ){
        deleteStoreGroup(
            input: {
                id: $id
            }
        ) {
            success
            errors
        }
    }
    ```

=== "Variables"
    ```json
    {
        "id": 4
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteStoreGroup": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## List store groups

```gql
query {
	storeGroups{
		edges {
			node {
				pk
				id
			}
		}
	}
}
```

## Get a single store group

```gql
query {
	storeGroup(id: "U3RvcmVOb2RlOjE5"){
		pk
		id
        name
	}
}
```
