# graphql with cognite

- aggregate queries work - to count how many nodes are there in a view -

  ```
  query MyQuery {
    aggregateProduct(filter: {externalId: {prefix: "abc"}}) {
      items {
        count {
          externalId
        }
      }
    }
  }
  ```