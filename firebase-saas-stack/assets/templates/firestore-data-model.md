# Firestore Data Model

## Principles

- Tenant boundary:
- Main list screens:
- High-volume collections:
- Server-only fields:
- Audit trail strategy:

## Collections

| Path | Purpose | Client access | Rules owner | Indexes |
|---|---|---|---|---|
| organizations/{orgId} | | | | |
| organizations/{orgId}/members/{uid} | | | | |

## Documents

### Path

```text
organizations/{orgId}/...
```

Fields:

| Field | Type | Required | Client writable | Notes |
|---|---|---:|---:|---|
| | | | | |

## Query Patterns

| Screen/API | Query | Index needed? | Notes |
|---|---|---:|---|
| | | | |

## Security Rules Sketch

- Auth required:
- Org membership required:
- Role required:
- Create validation:
- Update validation:
- Delete validation:

## Server-Only Mutations

| Mutation | Reason |
|---|---|
| | |
