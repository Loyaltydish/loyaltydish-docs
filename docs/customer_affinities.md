```gql
input AffinitiesFiltersInput {
  by: String = "purchase" # purchase or impressions
  consumerId: ID!
  storeId: ID
  limit: Int = 5
  startTime: Time
  endTime: Time
}
```

```gql
query ($filters: AffinitiesFiltersInput!) {
    affinityProducts(filters: $filters) {
      percentage
      product {
        id
        name
      }
    }
    affinityCategories(filters: $filters) {
      percentage
      category {
        id
        name
      }
    }
    affinityOrderType(filters: $filters) {
      percentage
      orderType {
        id
        name
      }
    }
    affinityComponents(filters: $filters) {
      percentage
      component {
        id
        name
      }
    }
  }
```
