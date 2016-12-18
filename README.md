Docs for the WIP GraphQL support in Flow. Most importantly validation
differences between this implementation and the GraphQL spec.

Tracking issue: facebook/flow#2823

Operations
==========

### Regular operation

- Variables
  - Checked if declared
  - Inferred if not declared

```javascript
gql`query { me { name } }`;
```

### Relay query

Conditions:
- Operation type: query
- No var declaration
- Single field

```javascript
gql`query { user(id: $userID) }`;
```

### Relay mutation

Conditions:
- Operation type: mutation
- No var declaration
- Single field with no args
  - Field accepts one argument named `input`

```javascript
gql`mutation { likeStory }`;
```

Fragments
=========

```javascript
gql`fragment on User { id name }`;
gql`fragment UserInfo on User { id name }`;
```
