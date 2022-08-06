## Subscribe to notifications
The payload below shoud run with customer credentials.

=== "Request"
    ```gql
    mutation (
      $merchantId: ID
      $topics: [String]! # OFFER, LOYALTY, ORDER, PROMOTION
      $types: [String]! # EMAIL, SMS, PUSH
    ){
      setNotificationsSubscription(
        input: {
          merchantId: $merchantId
          topics: $topics
          types: $types
        }
      ) {
        success
        errors
        notificationsSubscription {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "merchantId": 25,
      "topics": ["OFFER", "ORDER"],
      "types": ["EMAIL", "PUSH"]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "setNotificationsSubscription": {
                "success": true,
                "errors": null,
                "notificationsSubscription": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```


## Set notification device

=== "Request"
    ```gql
    mutation (
      $subscriptionId: ID!
      $deviceType: String!
      $pushSubscription: JSONString # Web Push subscription json payload
      $fcmToken: String # Firebase Cloud Messaging token
      $apnsToken: String # Apple Push Notification Service token
    ){
      setNotificationsDevice(
        input: {
          subscriptionId: $subscriptionId
          deviceType: $deviceType
          pushSubscription: $pushSubscription
          fcmToken: $fcmToken
          apnsToken: $apnsToken
        }
      ) {
        success
        errors
        notificationsDevice {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "subscriptionId": 25,
      "deviceType": "ANDROID",
      "fcmToken": "<fcm-token>",
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "setNotificationsDevice": {
                "success": true,
                "errors": null,
                "notificationsDevice": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```


## Create/send a notification
The payload below shoud run with merchant credentials.
The notification will be sent immediately after creation.

=== "Request"
    ```gql
    mutation (
      $subscriptionId: ID!
      $topic: String
      $emailSubject: String
      $emailBody: String
      $pushTitle: String
      $pushText: String
      $smsText: String
    ){
      createNotification(
        input: {
          subscriptionId: $subscriptionId
          topic: $topic
          emailSubject: $emailSubject
          emailBody: $emailBody
          pushTitle: $pushTitle
          pushText: $pushText
          smsText: $smsText
        }
      ) {
        success
        errors
        notification {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "subscriptionId": 25,
      "pushTitle": "Hey {{ consumer.firstname }}!",
      "pushText": "This is a test push notification"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createNotification": {
                "success": true,
                "errors": null,
                "notification": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```
