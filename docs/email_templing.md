LoyaltyDish provides an API to create email templates based on the [Jinja](https://jinja.palletsprojects.com/en/3.1.x/) templating language

## Create an email template

=== "Request"
    ```gql
    mutation (
      $name: String!
      $description: String!
      $template: JSONString
    ){
      createEmailTemplate(
        input: {
          name: $name
          description: $description
          template: $template
        }
      ) {
        success
        errors
        emailTemplate {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "name": "Email template 1",
      "description": "The first email template",
      "template": "<p>Order #{{ order.order_id }} completed successfully!</p>"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createEmailTemplate": {
                "success": true,
                "errors": null,
                "emailTemplate": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Update an email template

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $description: String
      $template: JSONString
    ){
      updateEmailTemplate(
        input: {
          id: $id
          name: $name
          description: $description
          template: $template
        }
      ) {
        success
        errors
        emailTemplate {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
      "id": 1,
      "name": "Email template 1 - edited"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateEmailTemplate": {
                "success": true,
                "errors": null,
                "emailTemplate": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```


## Delete an email template

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteEmailTemplate(
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
            "deleteEmailTemplate": {
                "success": true,
                "errors": null
            }
        }
    }
    ```


## List email templates

```gql
query {
	emailTemplates{
		edges {
			node {
				pk
				id
			}
		}
	}
}
```

## Get a single email template

```gql
query {
	emailTemplate(id: "U3RvcmVOb2RlOjE5"){
		pk
		id
		name
	}
}
```
