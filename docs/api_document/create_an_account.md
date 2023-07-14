=== "Request"
    ```gql
    mutation SignUp(
      $email: String!
      $password: String!
      $firstname: String!
      $lastname: String!
      $userType: String!
      $merchantType: String
      $phoneNumber: String
      $birthday: String
      $country: String
      $city: String
      $street: String
      $zipCode: String
      $gender: String
    ) {
      register(
          email: $email
          password1: $password
          password2: $password
          firstname: $firstname
          lastname: $lastname
          userType: $userType
          merchantType: $merchantType
          phoneNumber: $phoneNumber
          birthday: $birthday
          country: $country
          city: $city
          street: $street
          zipCode: $zipCode
          gender: $gender
      ) {
        success
        errors
        token
        refreshToken
      }
    }
    ```

=== "Variables"
    ```json
    {
      "email": "merch17@gmail.com",
      "password": "12345@abc",
      "firstname": "Test",
      "lastname": "merchant",
      "userType": "MERCHANT"
    }
    ```

=== "Response"
    ```json
    {
      "data": {
        "register": {
          "success": true,
          "errors": null,
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoMThAZ21haWwuY29tIiwiZXhwIjoxNjk1Mzc5MDg0LCJvcmlnSWF0IjoxNjU5MzgyNjg0fQ.M6zrDOQ3Gn5LxrkLl1T3xUMz2xOrnL8CxHWOfAaOOSc",
          "refreshToken": "f5ee1e870f8fc78dbe9f12ae700460e9f4df9d55"
        }
      }
    }
    ```
