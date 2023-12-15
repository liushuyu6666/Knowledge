# Components:
## Resolvers
Resolvers works as a handler to response the GraphQL queries by determining what data to return for a given query.

1. All resolvers must be defined in a "resolver map" object.
2. Bind resolver map with `schema` using `addResolversToSchema` API to Create an Apollo Server
3. When a query is made, the server uses the resolver functions from the resolver map to fetch the necessary data for each field.

## Schema
Schema is actually the type, Schema need to be compatible with Resolvers. There is a gap, because we are using typescript to develop, and we need to make our typescript type be align with schema so that Resolvers in the code is able to use that. `codegen` is used to translate Graphql schema to Typescript type.

For example, the schema is defined:
```typescript
export default gql`
  input CreatePaymentInput {
    invoiceId: ObjectID!
    method: PaymentMethod!
    provider: Provider!
  }
`
```
After translating, it becomes to
```typescript
export type CreatePaymentInput = {
  invoiceId: Scalars['ObjectID'];
  method: PaymentMethod;
  provider: Provider;
};
```

Then resolvers can use this type in the code.

## Context
context shares resources across different parts of your application:

Common use cases for the `context` object include:
1. Authentication: Storing information about the authenticated user.
2. Database Connections: Providing access to database connections.
3. Utility Functions: Making utility functions available to resolver functions.
4. Logging and Monitoring: Including logging or monitoring functionality.