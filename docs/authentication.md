LoyaltyDish offers a simple interface for handling authentication. Its based on the JWT convention where each request should contain the `Authorization: Bearer <access_token>` header.

## Obtain access token
Once you have created an account with an email and password, the `signIn` mutation will be available to obtain your access token.

**Access token**: A token that grants access to a client's resources and has some privileges attached to it. Access tokens expire after a certain amount of time.

**Refresh token:** A token that is used to generate more access tokens. If you use the code flow, refresh tokens are valid until their access is revoked. Refresh tokens are single-use tokens and expire after 90 days.
 

=== "Request"
    ```gql
    mutation MerchantSignIn(
      $email: String!
      $password: String!
    ){
      signIn(
        email: $email
        password: $password
      ) {
        token
        refreshToken
        success
        errors
      }
    }
    ```

=== "Variables"
    ```json
    {
      "email": "demo@loyaltydish.com",
      "password": "12345@abc"
    }
    ```

=== "Response"
    ```json
    {
      "data": {
        "signIn": {
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoYW50M0BnbWFpbC5jb20iLCJleHAiOjE2OTUzNjQ4NzQsIm9yaWdJYXQiOjE2NTkzNjg0NzR9.9jYPs1ThFW_kiC2SeIacjOM-sQuMbdbYtyGor5X78Ug",
          "refreshToken": "4ce1ac944d9658c1e72999efbf497dc2a05138ac",
          "success": true,
          "errors": null
        }
      }
    }
    ```

## Refresh token

Exchange access token by passing refresh token

=== "Request"
    ```gql
    mutation ($token: String!){
      refreshToken(
        refreshToken: $token
      ) {
        success,
        errors,
        payload,
        token,
        refreshToken
      }
    }
    ```

=== "Variables"
    ```json
    {
	    "token": "4ce1ac944d9658c1e72999efbf497dc2a05138ac"
    }
    ```

=== "Response"
    ```json
    {
      "data": {
        "refreshToken": {
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6Im1lcmNoYW50M0BnbWFpbC5jb20iLCJleHAiOjE2OTUzNjQ4NzQsIm9yaWdJYXQiOjE2NTkzNjg0NzR9.9jYPs1ThFW_kiC2SeIacjOM-sQuMbdbYtyGor5X78Ug",
          "refreshToken": "4ce1ac944d9658c1e72999efbf497dc2a05138ac",
          "success": true,
          "errors": null
        }
      }
    }
    ```

## Revoke token

API to revoke the refresh token of an user

=== "Request"
    ```gql
    mutation ($token: String!){
      revokeToken(
        refreshToken: $token
      ) {
        success,
        errors,
        payload,
        token,
        refreshToken
      }
    }
    ```

=== "Variables"
    ```json
    {
	    "token": "4ce1ac944d9658c1e72999efbf497dc2a05138ac"
    }
    ```

=== "Response"
    ```json
    {
      "data": {
        "revokeToken": {
          "success": true,
          "errors": null
        }
      }
    }
    ```
