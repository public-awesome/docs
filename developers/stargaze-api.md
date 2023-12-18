# Stargaze API

The Stargaze API provides programmatic access to Stargaze data.

{% embed url="https://graphql.mainnet.stargaze-apis.com/graphql" %}

Query data on collections, offers on Marketplace, NFT media info, Stargaze Names, or whatever you want. Everything that is on the website at stargaze.zone is available via this API.

### GraphQL
 
 Here is a quick and dirty example which returns a subset of available data for a given `collectionAddr` and `tokenId` using the [`@apollo/client`](https://www.npmjs.com/package/@apollo/client) package.

```typescript
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';

const client = new ApolloClient({
	uri: 'https://graphql.mainnet.stargaze-apis.com/graphql',
	cache: new InMemoryCache(),
});

const getTraitsAndOwner = (collectionAddr, tokenId) =>
	client.query({
		query: gql`
            query Query {
                token(
                    collectionAddr: "${collectionAddr}"
                    tokenId: "${tokenId}"
                ) {
                    traits {
                        name
                        value
                    }
                    owner {
                        address
                        name {
                            name
                        }
                    }
                }
            }
        `,
    });

```

Notes:

- You can use your favorite GraphQL tech and tools such as [`react-query`](https://www.npmjs.com/package/react-query) if you wish
- If you run into `CORS` issues you can proxy the request through your own server or a serverless solution such as [CloudFlare functions](https://developers.cloudflare.com/pages/functions/) ([example](https://gist.github.com/jason-c-child/e9ebf988ab0ef740a03d221b0c702567)).