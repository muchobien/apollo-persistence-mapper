# @muchobien/apollo-persistence-mapper

#### Usage

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
