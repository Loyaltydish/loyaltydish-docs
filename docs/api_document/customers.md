Create, manage and sync customers from internal and external sources (like Spotify, salesforce, etc.)

The customer APIs also enable to fetch all customer-related resources like orders, promotions, loyalty points, and more

## Customer Signup

Create a new customer

=== "Request"
`gql mutation SignUp( $email: String! $password: String! $firstname: String! $lastname: String! $userType: String! $merchantType: String $phoneNumber: String $birthday: String $country: String $city: String $street: String $zipCode: String $gender: String ) { register( email: $email password1: $password password2: $password firstname: $firstname lastname: $lastname userType: $userType merchantType: $merchantType phoneNumber: $phoneNumber birthday: $birthday country: $country city: $city street: $street zipCode: $zipCode gender: $gender ) { success errors token refreshToken } } `

=== "Variables"
`json { "email": "consumer@loyaltydish.com", "password": "XXXXXX", "firstname": "John", "lastname": "Doe", "userType": "CONSUMER" } `

=== "Response"
`json { "data": { "register": { "success": true, "errors": null, "token": "eyJ0eXAjOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoMThAZ21haWwuY29tIiwiZXhwIjoxNjk1Mzc5MDg0LCJvcmlnSWF0IjoxNjU5MzgyNjg0fQ.M6zrDOQ3Gn5LxrkLl1T3xUMz2xOrnL8CxHWOfAaOOSc", "refreshToken": "f5ee1e870f8fc78dbe9f12ae700460e9f4df9d55" } } } `

## Customer Login

Mutation to login the customer to access the system. Access token will be generated to access other resources

=== "Request"
```gql mutation ( $email: String! $password: String! ){ obtainToken( email: $email password: $password ) { token refreshToken success errors } } ```

=== "Variables"
```json { "email": "consumer@loyaltydish.com", "password": "XXXXXX" } ```

=== "Response"
```json { "data": { "signIn": { "token": "eyJ0eXSiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoYW50M0BnbWFpbC5jb20iLCJleHAiOjE2OTUzNjQ4NzQsIm9yaWdJYXQiOjE2NTkzNjg0NzR9.9jYPs1ThFW_kiC2SeIacjOM-sQuMbdbYtyGor5X78Ug", "refreshToken": "4ce1ac944d9658c1e72999efbf497dc2a05138ac", "success": true, "errors": null } } } ```

## List customers

List all the customers in the system

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

Returns the customer resource by ID 

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

Returns all the promotions target to the customer

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

Return all the orders placed by the customer ID filter by duration  

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

## Customers object

Provides the fields and values to use when creating or updating a customer.


| Method                     | Type               | Description |
| -------------------------- | ------------------ | ----------- |
| id                         | `ID!`              |Unique ID of the customer
| lastLogin                  | `DateTime`         |The last time the customer login time to the system
| extraInfo                  | `JSONString`       |Create custom fields in key/value pair
| deletedAt                  | `DateTime`         |Datetime when customer is inactivated
| userType                   | `UserUserType!`    |Default to "CONSUMER"
| email                      | `String`           |Unique email ID for the customer
| firstname                  | `String!`          |The customer's first name.
| lastname                   | `String!`          |The customer's last name.
| phoneNumber                | `String`           |The customer's primary phone #. The phone number should comply with the E.164 international telephone numbering plan.
| birthday                   | `Date`             |The customer's birth date
| gender                     | `UserGender`       |Gender of the customer
| country                    | `UserCountry`      |The customer's country
| city                       | `String`           |The customer's city
| street                     | `String`           |The customer's street address
| zipCode                    | `String`           |The customer's zip code
| picture                    | `String`           |Profile picture of the customer
| merchantType               | `UserMerchantType` |Default to Null
| creator                    | `IUserNode`        |Default to Null
| logo                       | `String`           |Default to Null
| numOfOrderDiscountsAllowed | `Int!`             |Default to Null
| loyaltyId                  | `String`           |The customer's unique Loyalty ID
| entitySource               | `UserEntitySource` |Source from which the customer's is created 
| entitySourceId             | `String`           |Unique Entity ID of the customer created from the source
| active                     | `Boolean!`         |False if the customer's is deleted
| staff                      | `Boolean!`         |Default to Null
| admin                      | `Boolean!`         |Default to Null
| createdAt                  | `DateTime!`        |The time the customer's was created
| updatedAt                  | `DateTime!`        |The time the customer's was last updated
| archived                   | `Boolean`          |false if customer is no-longer active
| verified                   | `Boolean`          |Confirms whether the customer's email ID is verified 
| secondaryEmail             | `String`           |Secondary email of the customer
| address                    | `String`           |Complete address of the customer
| pointsEarned               | `Int`              |Loyalty Points earned by the customer by merchant
