## Create a staff merchant
By running the payload below, the merchant will receive two email, the first is an activation email and the second contains an auto generated password for him to login.

=== "Request"
    ```gql
    mutation (
      $email: String!
      $firstname: String!
      $lastname: String!
      $phoneNumber: String
      $country: String
      $city: String
      $street: String
      $zipCode: String
      $birthday: Date
      $stores: [ID]
      $roles: [ID]
    ) {
      createMerchant(
        input: {
          email: $email
          firstname: $firstname
          lastname: $lastname
          birthday: $birthday
          phoneNumber: $phoneNumber
          country: $country
          city: $city
          zipCode: $zipCode
          street: $street
          stores: $stores
          roles: $roles
        }
      ) {
        success
        errors
        merchant {
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "email": "joxiye6010@tlhao86.com",
      "firstname": "Manager",
      "lastname": "One",
      "stores": [5, 7, 15],
      "roles": [6],
      "merchantType": "STAFF"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createMerchant": {
                "success": true,
                "errors": null,
                "merchant": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Delete a merchant

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ) {
      deleteMerchant(
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
      "id": 10
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteMerchant": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## Recruit a merchant to a store

```gql
mutation (
  $merchantId: ID!
  $storeId: ID!
) {
  addStoreToMerchant(
    input: {
      merchantId: $merchantId
      storeId: $storeId
    }
  ) {
    success
    errors
  }
}
```

## Remove a merchant from a store

```gql
mutation (
  $merchantId: ID!
  $storeId: ID!
) {
  removeStoreFromMerchant(
    input: {
      merchantId: $merchantId
      storeId: $storeId
    }
  ) {
    success
    errors
  }
}
```


## Recruit a merchant to a store group

```gql
mutation (
  $merchantId: ID!
  $storeGroupId: ID!
) {
  addStoreGroupToMerchant(
    input: {
      merchantId: $merchantId
      storeGroupId: $storeGroupId
    }
  ) {
    success
    errors
  }
}
```

## Remove a merchant from a store group

```gql
mutation (
  $merchantId: ID!
  $storeGroupId: ID!
) {
  removeStoreGroupFromMerchant(
    input: {
      merchantId: $merchantId
      storeGroupId: $storeGroupId
    }
  ) {
    success
    errors
  }
}
```
