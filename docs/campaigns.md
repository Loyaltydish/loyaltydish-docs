## Create a campaign
=== "Request"
    ```gql
    mutation (
      $name: String!
      $start: Date!
      $end: Date!
      $status: String
      $stores: [ID]
      $storeGroups: [ID]
      $images: [ImageInput]!
    ){
      createCampaign(
        input: {
          name: $name
          start: $start
          end: $end
          status: $status
          stores: $stores
          storeGroups: $storeGroups
          images: $images
        }
      ) {
        success
        errors
        campaign {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
        "name": "Summer campaign",
        "start": "2022-07-21",
        "end": "2022-07-30",
        "status": "SCHEDULED",
        "stores": [4, 5, 6]
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "createCampaign": {
                "success": true,
                "errors": null,
                "campaign": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```

## Update a campaign

=== "Request"
    ```gql
    mutation (
      $id: ID!
      $name: String
      $start: Date
      $end: Date
      $status: String
      $stores: [ID]
      $storeGroups: [ID]
      $images: [ImageInput]
    ){
      updateCampaign(
        input: {
          id: $id
          name: $name
          start: $start
          end: $end
          status: $status
          stores: $stores
          storeGroups: $storeGroups
          images: $images
        }
      ) {
        success
        errors
        campaign {
          pk
          id
        }
      }
    }
    ```

=== "Variables"
    ```json
    {
        "name": "Editd - Summer campaign"
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "updateCampaign": {
                "success": true,
                "errors": null,
                "campaign": {
                    "id": "U3RvcmVOb2RlOjEzMQ=="
                }
            }
        }
    }
    ```


## Delete a campaign

=== "Request"
    ```gql
    mutation (
      $id: ID!
    ){
      deleteCampaign(
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
        "id": 5
    }
    ```

=== "Response"
    ```json
    {
        "data": {
            "deleteCampaign": {
                "success": true,
                "errors": null
            }
        }
    }
    ```

## List Campaigns

```gql
query {
	campaigns{
		edges {
			node {
				pk
				id
			}
		}
	}
}
```

## Get a single campaign

```gql
query {
	campaign(id: "U3RvcmVOb2RlOjE5"){
		pk
		id
		name
	}
}
```
