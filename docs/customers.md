## The consumer node

| Method                     | Type               | Description |
| -------------------------- | ------------------ | ----------- |
| id                         | `ID!`              |
| lastLogin                  | `DateTime`         |
| extraInfo                  | `JSONString`       |
| deletedAt                  | `DateTime`         |
| userType                   | `UserUserType!`    |
| email                      | `String`           |
| firstname                  | `String!`          |
| lastname                   | `String!`          |
| phoneNumber                | `String`           |
| birthday                   | `Date`             |
| gender                     | `UserGender`       |
| country                    | `UserCountry`      |
| city                       | `String`           |
| street                     | `String`           |
| zipCode                    | `String`           |
| picture                    | `String`           |
| merchantType               | `UserMerchantType` |
| creator                    | `IUserNode`        |
| logo                       | `String`           |
| numOfOrderDiscountsAllowed | `Int!`             |
| loyaltyId                  | `String`           |
| entitySource               | `UserEntitySource` |
| entitySourceId             | `String`           |
| active                     | `Boolean!`         |
| staff                      | `Boolean!`         |
| admin                      | `Boolean!`         |
| createdAt                  | `DateTime!`        |
| updatedAt                  | `DateTime!`        |
| pk                         | `Int`              |
| archived                   | `Boolean`          |
| verified                   | `Boolean`          |
| secondaryEmail             | `String`           |
| address                    | `String`           |
| pointsEarned               | `Int`              |

## Sign up

=== "Request"
`gql mutation SignUp( $email: String! $password: String! $firstname: String! $lastname: String! $userType: String! $merchantType: String $phoneNumber: String $birthday: String $country: String $city: String $street: String $zipCode: String $gender: String ) { register( email: $email password1: $password password2: $password firstname: $firstname lastname: $lastname userType: $userType merchantType: $merchantType phoneNumber: $phoneNumber birthday: $birthday country: $country city: $city street: $street zipCode: $zipCode gender: $gender ) { success errors token refreshToken } } `

=== "Variables"
`json { "email": "consumer1@gmail.com", "password": "12345@abc", "firstname": "John", "lastname": "Doe", "userType": "CONSUMER" } `

=== "Response"
`json { "data": { "register": { "success": true, "errors": null, "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoMThAZ21haWwuY29tIiwiZXhwIjoxNjk1Mzc5MDg0LCJvcmlnSWF0IjoxNjU5MzgyNjg0fQ.M6zrDOQ3Gn5LxrkLl1T3xUMz2xOrnL8CxHWOfAaOOSc", "refreshToken": "f5ee1e870f8fc78dbe9f12ae700460e9f4df9d55" } } } `

## Sign in

=== "Request"
`gql mutation ( $email: String! $password: String! ){ obtainToken( email: $email password: $password ) { token refreshToken success errors } } `

=== "Variables"
`json { "email": "consumer1@gmail.com", "password": "12345@abc" } `

=== "Response"
`json { "data": { "signIn": { "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoYW50M0BnbWFpbC5jb20iLCJleHAiOjE2OTUzNjQ4NzQsIm9yaWdJYXQiOjE2NTkzNjg0NzR9.9jYPs1ThFW_kiC2SeIacjOM-sQuMbdbYtyGor5X78Ug", "refreshToken": "4ce1ac944d9658c1e72999efbf497dc2a05138ac", "success": true, "errors": null } } } `

## List customers

```gql
query {
  consumers(loyaltyId: "", phoneNumber_Icontains: "", email_Icontains: "") {
    edges {
      node {
        pk
        id
        firstname
        lastname
        email
        pointsEarned
        phoneNumber
        birthday
        address
        lastLogin
        loyaltyId
        picture
        city
      }
    }
  }
}
```

## Get a single customer

```gql
query {
  consumer(id: "SVVzZXJOb2RlOjE3Nw==") {
    pointsEarned
    redemptions {
      edges {
        node {
          id
          createdAt
        }
      }
    }
    stampsRedemptions {
      edges {
        node {
          id
          createdAt
        }
      }
    }
    pointsRedemptions {
      edges {
        node {
          id
          createdAt
        }
      }
    }
  }
}
```

## Get customer available promotions

```gql
query (
  $consumerLoyaltyId: String
  $consumerEmail: String
  $consumerPhoneNumber: String
  $storeId: ID
) {
  consumerAvailablePromotions(
    consumerLoyaltyId: $consumerLoyaltyId
    consumerEmail: $consumerEmail
    consumerPhoneNumber: $consumerPhoneNumber
    storeId: $storeId
  ) {
    count
    edges {
      node {
        name
      }
    }
  }
}
```

## Get customer's purchase history

```gql
query (
  $id: ID!
  $storeId: ID
) {
    purchaseHistory: orders(
      consumer_Id: $id
      store_Id: $storeId
    ) {
      edges {
        node {
          orderId
          completedAt
          paymentTypeDisplay
          total
          orderType {
            name
          }
        }
      }
    }
  }
`
```
