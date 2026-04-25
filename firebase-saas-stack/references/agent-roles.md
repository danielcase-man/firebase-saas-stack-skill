# Agent Roles And Ownership

Use these roles when Daniel asks for subagents or when the Firebase work is large enough to split.

## Firebase Architect

Owns:

- `docs/firebase/fit-report.md`
- `docs/firebase/architecture-plan.md`

Prompt:

```text
Use $firebase-saas-stack to evaluate whether Firebase fits this SaaS product. Produce docs/firebase/fit-report.md and docs/firebase/architecture-plan.md. Do not edit implementation files.
```

## Firestore Data Modeler

Owns:

- `docs/firebase/firestore-data-model.md`
- Firestore index planning docs if present

Prompt:

```text
Use $firebase-saas-stack to design the Firestore data model, tenant paths, roles, query patterns, indexes, and server-only mutations. Own only docs/firebase/firestore-data-model.md unless implementation ownership is explicitly assigned.
```

## Security Rules Lead

Owns:

- `firestore.rules`
- `storage.rules`
- rule tests
- `docs/firebase/security-rules-checklist.md`

Prompt:

```text
Use $firebase-saas-stack and references/security-first.md to implement or review Firebase Security Rules. Start locked down, add path-specific rules, test with the emulator where practical, and do not edit unrelated app code.
```

## Backend Implementer

Owns:

- assigned Firebase client/admin initialization files
- assigned Cloud Functions/server files
- assigned payment/AI integration files

Prompt:

```text
Use $firebase-saas-stack to implement the approved Firebase architecture. Keep secrets server-side, keep privileged writes in trusted backend code, and preserve existing repo patterns.
```

## Firebase QA Reviewer

Owns:

- `docs/firebase/firebase-implementation-qa.md`

Prompt:

```text
Use $firebase-saas-stack to review the Firebase implementation. Verify auth, tenant isolation, rules, emulator tests, secrets, budget alerts, App Check plan, and deployment risk. Record findings in docs/firebase/firebase-implementation-qa.md.
```

## Coordination Rules

- Claim file ownership on Engram/project board before editing.
- Keep architecture docs, rules, and implementation ownership separate unless explicitly handed off.
- Do not let multiple agents edit the same Firebase rules or initialization files concurrently.
- Stop and surface conflicts if another agent owns the target file.
