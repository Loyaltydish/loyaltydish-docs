LoyaltyDish provides an API to create email templates based on the [Jinja](https://jinja.palletsprojects.com/en/3.1.x/) templating language

## Create an email template

=== "Request"
    ```gql
    mutation (
        $name: String!
        $description: String
        $template: JSONString
        $prebuiltTemplateId: ID
    ) {
        createEmailTemplate(input: {
            name: $name
            description: $description
            template: $template
            prebuiltTemplateId: $prebuiltTemplateId
        }) {
            success
            errors
            emailTemplate {
                pk
                name
                description
                template
                merchant {
                    pk
                }
            }
        }
    }
    ```

=== "Variables"
    ```json
    {
        "name": "Email template 1",
        "description": "The first email template",
        "template": "{\"design\": {}}"
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
    ) {
        updateEmailTemplate(input: {
            id: $id
            name: $name
            description: $description
            template: $template
        }) {
            success
            errors
            emailTemplate {
                pk
                name
                description
                template
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
    ) {
        deleteEmailTemplate(input: {
            id: $id
        }) {
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


## Create an prebuilt email template

```gql
mutation (
    $name: String!
    $description: String
    $template: JSONString
    $activeFrom: DateTime!
    $activeTo: DateTime!
    $categoryId: ID!
) {
    createPrebuiltEmailTemplate(input: {
        name: $name
        description: $description
        template: $template
        activeFrom: $activeFrom
        activeTo: $activeTo
        categoryId: $categoryId
    }) {
        success
        errors
        prebuiltEmailTemplate {
            pk
            name
            description
            template
            activeFrom
            activeTo
        }
    }
}
```

## Update a prebuilt email template


```gql
mutation (
    $id: ID!
    $name: String
    $description: String
    $template: JSONString
    $activeFrom: DateTime
    $activeTo: DateTime
    $categoryId: ID
) {
    updatePrebuiltEmailTemplate(input: {
        id: $id
        name: $name
        description: $description
        template: $template
        activeFrom: $activeFrom
        activeTo: $activeTo
        categoryId: $categoryId
    }) {
        success
        errors
        prebuiltEmailTemplate {
            pk
            name
            description
            template
            activeFrom
            activeTo
        }
    }
}
```


## Delete a prebuilt email template


```gql
mutation (
    $id: ID!
) {
    deletePrebuiltEmailTemplate(input: {
        id: $id
    }) {
        success
        errors
    }
}
```

## List prebuilt email templates

```gql
query ($categoryId: ID){
    prebuiltEmailTemplates(categoryId: $categoryId) {
        count
        edges {
            node {
                pk
                id
            }
        }
    }
}
```

## Get a single prebuilt email template

```gql
query ($id: ID!) {
    prebuiltEmailTemplate(id: $id) {
        id
        pk
        name
        template
        activeFrom
        activeTo
    }
}
```




## Create an prebuilt email template category

```gql
mutation (
    $name: String!
    $displayName: String!
) {
    createPrebuiltEmailTemplateCategory(input: {
        name: $name
        displayName: $displayName
    }) {
        success
        errors
        category {
            pk
            name
            displayName
        }
    }
}
```

## Update a prebuilt email template category


```gql
mutation (
    $id: ID!
    $name: String
    $displayName: String
) {
    updatePrebuiltEmailTemplateCategory(input: {
        id: $id
        name: $name
        displayName: $displayName
    }) {
        success
        errors
        category {
            pk
            name
            displayName
        }
    }
}
```


## Delete a prebuilt email template


```gql
mutation (
    $id: ID!
) {
    deletePrebuiltEmailTemplateCategory(input: {
        id: $id
    }) {
        success
        errors
    }
}
```

## List prebuilt email templates

```gql
query {
    prebuiltEmailTemplateCategories {
        count
        edges {
            node {
                pk
                id
                name
                displayName
            }
        }
    }
}
```

## Get a single prebuilt email template

```gql
query ($id: ID!) {
    prebuiltEmailTemplateCategory(id: $id) {
        id
        pk
        name
        displayName
    }
}
```


