# Key Components

- `schema.graphql` - Objects used in GraphQL layer are defined here. Notice, that they are *not written `go` code*. 

- `graph/model/models_gen.go` - Based on the definitions in `schema.graphql`, corresponding structs *in `go`* are generated here.

- `graph/generated/generated.go` - Also, based on the definitions in `schema.graphql`, necessary queries and mutations declarations are generated *in `go`* here.

- `schema.resolvers.go` - Queries and mutations declared in `graph/generated/generated.go` need to be implemented here. You can (and should) use structs generated in `graph/model/models_gen.go` here.

- `internal` folder - Code that interacts with DB is located here.


# Code Writing Workflow


```mermaid
flowchart TD
  start --> |define objects| schema.graphql --> |generate| models_gen.go & generated.go --> |implement| schema.resolvers.go
```


# Handling Requests

- Example: query `users`

```mermaid
sequenceDiagram
    participant UsersQueryResolver
    participant schema.resolvers.go
    participant users.go
    UsersQueryResolver->>schema.resolvers.go: Users(ctx)
    schema.resolvers.go->>users.go: GetAll()
    users.go->>users.go: getData from Db
    users.go->>schema.resolvers.go: []User 
    schema.resolvers.go->>UsersQueryResolver: []User
```