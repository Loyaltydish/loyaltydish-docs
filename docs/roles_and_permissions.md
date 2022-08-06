## List available permissions

```gql
query {
  permissions {
    edges {
      node {
        pk
        id
        codename
        displayName
      }
    }
  }
}
```

## Add permission to merchant

=== "Request"
    ```gql
     mutation (
      $merchantId: ID!
      $permissionId: ID!
    ) {
      addPermissionToMerchant(
        input: {
          merchantId: $merchantId
          permissionId: $permissionId
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
      "merchantId": 84,
      "permissionId": 5
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "addPermissionToMerchant": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Create a role

=== "Request"
    ```gql
     mutation (
      $displayName: String!
      $permissions: [ID]
    ) {
      createRole(
        input: {
          displayName: $displayName
          permissions: $permissions
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
      "displayName": "Manager",
      "permissions": [1, 2, 3]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createRole": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Update a role

=== "Request"
    ```gql
     mutation (
      $id: ID!
      $displayName: String
      $permissions: [ID]
    ) {
      updateRole(
        input: {
          id: $id
          displayName: $displayName
          permissions: $permissions
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
      "id": 1,
      "displayName": "Manager - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateRole": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Delete a role

=== "Request"
    ```gql
     mutation (
      $id: ID!
    ) {
      deleteRole(
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
      "id": 1
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteRole": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## Add role to merchant

=== "Request"
    ```gql
     mutation (
      $merchantId: ID!
      $roleId: ID!
    ) {
      addRoleToMerchant(
        input: {
          merchantId: $merchantId
          roleId: $roleId
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
      "merchantId": 84,
      "roleId": 5
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "addRoleToMerchant": {
                "success": true,
                "errors": null
            }
        }
    }
    ```
