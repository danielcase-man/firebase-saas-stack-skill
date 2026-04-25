# Firebase Security Rules Checklist

## Project

- Firebase project:
- Environment:
- Date:

## Global Gates

- [ ] Firestore starts locked down.
- [ ] Storage starts locked down.
- [ ] No broad public writes.
- [ ] Rules exist for every client-accessed path.
- [ ] Rules validate tenant membership.
- [ ] Rules validate user roles.
- [ ] Rules prevent client writes to server-only fields.
- [ ] Rules separate create/update/delete where behavior differs.
- [ ] Rules tests exist or gap is documented.
- [ ] App Check plan exists.
- [ ] Secrets are server-side only.
- [ ] Budget alerts are configured or tracked as a launch blocker.

## Path Review

| Path | Rule status | Tests | Notes |
|---|---|---|---|
| | | | |

## Known Gaps

-

## Launch Decision

- Approved:
- Blockers:
