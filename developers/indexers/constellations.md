# Constellations

## Intro

**Constellations** is a high-performance and real-time indexer currently used
by [Stargaze](https://www.stargaze.zone). It has a free to use API.

Constellations is:

1. A public facing website available at
   [www.constellations.zone](https://www.constellations.zone) to view content.

2. A set of GraphQL API to fetch data Constellations has indexed.
   Self-generated GraphQL documentation is enabled and you can [read the
   Constellations book](http://book.constellations.zone).

You should already know about GraphQL to use Constellations. You can read more
about GraphQL [here](https://graphql.org).

## How is it built?

Constellations is built entirely in Rust, backed with Posgresql and hosted on
bare metal servers for optimum performance. It fetches blocks live from the
blockchain over websockets, parse them instantly and store blocks,
transactions, messages and events.

## API example

### Get most recent minted collections

This will get the most recent minted collections on Stargaze.

Query
```graphql
query Collections($collectionsLimit: Int, $sortBy: CollectionSortBy) {
  collections(limit: $collectionsLimit, sortBy: $sortBy) {
    collections {
      image
      description
      tokensCount
      website
      createdAt
      collectionAddr
      name
      mintedAt
    }
  }
}
```

Variables
```
{
  "collectionsLimit": 2,
  "sortBy": "MINTED_AT_DESC"
}
```

> [Try it out live on explorer](https://studio.apollographql.com/sandbox/explorer?endpoint=https%3A%2F%2Fconstellations-api.mainnet.stargaze-apis.com%2Fgraphql&explorerURLState=N4IgJg9gxgrgtgUwHYBcQC4QEcYIE4CeABAMIQA25CUKAlhEgM4AUAJFBVTfUwDK1xaKdEQCSqADRFWjCHhQAhAiLKVqdBgGU5iggEoiwADpIiRDmu4MW5AUJHtO6no36CUU2fKUOvug8amZuZOVkyGJsHBAgCGAOYIkVFEYAiMUHi0AA4aSElRKBAA1siMZDCo%2BcEA7ggARoxCiUFRGQgxKAhgAIIoVWYWXLndYGB4-URIMYgTgqhdvVUAvkkrSEsgEiAAbjGZMXVUjBgggWZGIIPO1m5CFyIATBJJF35K90QXALKiAHIAKgBRAAiAH1uv9QcDAZoSBcTBstulMjkTiAlkA)
