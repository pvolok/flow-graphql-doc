Docs for the WIP GraphQL support in Flow. Most importantly validation
differences between this implementation and the GraphQL spec.

Tracking issue: https://github.com/facebook/flow/issues/2823

Operations
----------

### Regular operation

- Variables
  - Checked if declared
  - Inferred if not declared

```javascript
gql`query { me { name } }`;
```

### Relay query/mutation

In Relay root query and mutations are specified by the operations with top level
fields with no selections. Selections for those fields are described by
fragments.

Conditions:
- No fields have selection
- No var declaration

Differences from regular operations:
- Cannot extract data

```javascript
gql`query { user(id: $userID) }`;

gql`mutation { likeStory(input: $input) }`;
```

**TODO**: check getMutation() and getFatQuery() compatibility

Fragments
---------

- Variables
  - Checked if declared
  - Inferred if not declared

```javascript
gql`fragment on User { id name }`;
gql`fragment UserInfo on User { id name }`;
```
