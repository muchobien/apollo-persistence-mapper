# @muchobien/apollo-persistence-mapper

## Install

```sh
npm i @muchobien/apollo-persistence-mapper
```

or 

```sh
yarn add @muchobien/apollo-persistence-mapper
```

## Usage

### Graphql

```gql
query FooQuery {
  foos @persist {
    id
    name
    description
  }
}
```

or

```gql
query FooQuery {
  foos {
    __persist
    id
    name
    description
  }
}
```

### Apollo

```ts
import {
  persistenceMapper,
  createPersistLink,
} from '@muchobien/apollo-persistence-mapper';

...

  persistCacheSync({
    cache,
    storage: new MMKVWrapper(storage.instance),
    persistenceMapper,
    trigger: 'write',
    debug: __DEV__,
  });

  const persistLink = createPersistLink();
  
  const client = new ApolloClient({
    cache,
    link: ApolloLink.from([persistLink, httpLink]),
  });
```
