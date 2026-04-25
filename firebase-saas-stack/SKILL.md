---
name: "firebase-saas-stack"
description: "Evaluate and implement secure Firebase SaaS stacks for customer-facing workflow apps."
---

# Firebase SaaS Stack

## Overview

Use this skill to decide whether Firebase is the right backend for a customer-facing SaaS product and, if it is, to implement it with security, data modeling, billing protection, and production readiness as first-class requirements.

Firebase is a strong default candidate for fast web/mobile SaaS workflows, but it is not an automatic answer. Firestore is document/NoSQL, so start with a fit gate before refactoring or committing to the stack.

## Workflow

1. Inspect the project and product.
   - Identify the frontend framework, current backend, auth, database, payments, file storage, and deployment path.
   - Identify customer type, tenant boundaries, workflow objects, sensitive data, and expected usage.
   - If UI work is also involved, use `$saas-ui-design` alongside this skill.

2. Produce a Firebase fit report before implementation.
   - Copy/adapt `assets/templates/firebase-fit-report.md` to `docs/firebase/fit-report.md`.
   - Decide: good fit, conditional fit, or poor fit.
   - Do not proceed with Firestore if the core product needs heavy joins, strict relational constraints, SQL reporting, complex ledger accounting, or cross-tenant analytics that would be awkward in a document model.

3. Design the architecture.
   - Copy/adapt `assets/templates/firebase-architecture-plan.md` to `docs/firebase/architecture-plan.md`.
   - Select only the Firebase services needed for the product.
   - Default web SaaS candidate: Firebase App Hosting or Hosting, Firebase Auth, Cloud Firestore, Cloud Functions, Cloud Storage, App Check, Security Rules, Emulator Suite, and budget alerts.
   - For AI features, prefer Firebase AI Logic for supported client-side Gemini use cases with App Check, or Genkit/Cloud Functions for server-side AI workflows and non-Google model access.

4. Model data and authorization together.
   - Copy/adapt `assets/templates/firestore-data-model.md` to `docs/firebase/firestore-data-model.md`.
   - Treat Firestore Security Rules as part of the schema, not a launch-week afterthought.
   - Design tenant boundaries, role maps/custom claims, document paths, query patterns, indexes, and server-only mutations before coding.

5. Apply the security gate before writing production code.
   - Read `references/security-first.md`.
   - Copy/adapt `assets/templates/security-rules-checklist.md` to `docs/firebase/security-rules-checklist.md`.
   - Start locked down. Never deploy broad `allow read, write: if true` rules.
   - Never put service account keys, Stripe secrets, OpenAI/Anthropic keys, Gemini Developer API keys, webhook secrets, or third-party API secrets in frontend code.

6. Implement incrementally.
   - Use the Firebase Emulator Suite for local auth/database/functions/rules testing when available.
   - Add rule tests for each collection path and role.
   - Keep dev and prod Firebase projects separate.
   - Keep Firestore paths, generated indexes, rules, and function triggers in source control.
   - Prefer server-side Cloud Functions for privileged writes, payment webhooks, external API calls, and irreversible workflow changes.

7. Validate before final answer.
   - Run typecheck/lint/tests used by the repo.
   - Run Firebase rules/emulator tests if configured.
   - Confirm no secrets are committed.
   - Confirm budget alerts/quotas are documented before Blaze/paid services.
   - Produce `docs/firebase/firebase-implementation-qa.md` from `assets/templates/firebase-implementation-qa.md` for non-trivial work.

## Fit Gate

Load `references/fit-gate.md` before recommending Firebase for an existing app or new vertical SaaS.

Good Firebase candidates:

- customer portals
- intake/review/approval workflows
- real-time status tracking
- document-centric case/project/job records
- small teams with role-based collaboration
- mobile plus web apps sharing one backend
- prototypes that need auth, database, storage, and deployment quickly

Use caution or consider Postgres/Supabase/Firebase SQL options when:

- the product is heavily relational
- the product needs complex SQL reporting
- cross-entity joins dominate the workflow
- strong transactional accounting/ledger behavior is central
- tenant isolation must satisfy enterprise audit requirements beyond app-level rules
- the app already works well on Postgres and Firebase would be a costly rewrite without product gain

## Security Defaults

For any Firebase implementation, apply these defaults:

- Use Firebase Auth or Identity Platform for user identity.
- Use Security Rules for every Firestore/Storage path accessed by clients.
- Use App Check for web/mobile apps before production.
- Use Cloud Functions or server code for privileged operations.
- Store sensitive third-party secrets only in server-side secret storage/config.
- Restrict Firebase API keys even though normal Firebase web config keys are not authorization secrets.
- Set budget alerts before enabling paid usage.
- Test Security Rules in the emulator and CI where practical.
- Use separate dev/staging/prod Firebase projects.

## Payment And AI

For payments:

- Use `$saas-ui-design` for checkout/billing UI.
- Keep Stripe secret keys and webhook secrets server-side.
- Handle Stripe webhooks in Cloud Functions or another trusted backend.
- Record payment state server-side and reconcile from Stripe events, not client redirects alone.

For AI features:

- Do not expose model provider secrets in client code.
- Use Firebase AI Logic only when its current model/provider/security constraints fit.
- Use App Check and per-user rate limits for client AI calls.
- Use Genkit/Cloud Functions when prompts need server-side tools, external providers, private data, RAG, or stronger governance.

## References And Templates

Load only what is needed:

- `references/fit-gate.md`: Firebase vs Postgres/Supabase/SQL decision gate.
- `references/security-first.md`: production security and billing checklist.
- `references/architecture-patterns.md`: standard Firebase SaaS architecture patterns.
- `references/agent-roles.md`: subagent prompts and ownership boundaries.
- `references/official-docs.md`: current official Firebase documentation links used by this skill.
- `assets/templates/firebase-fit-report.md`: fit analysis artifact.
- `assets/templates/firebase-architecture-plan.md`: architecture plan artifact.
- `assets/templates/firestore-data-model.md`: data model and rules plan artifact.
- `assets/templates/security-rules-checklist.md`: security gate artifact.
- `assets/templates/firebase-implementation-qa.md`: final QA artifact.
