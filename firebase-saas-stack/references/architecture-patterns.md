# Firebase SaaS Architecture Patterns

## Default Web SaaS Candidate

- Frontend: existing app framework, often Next.js/React.
- Hosting: Firebase App Hosting for modern full-stack web apps, or Firebase Hosting for static/SPAs.
- Auth: Firebase Auth or Identity Platform.
- Data: Cloud Firestore for document-centric workflow data.
- Files: Cloud Storage for PDFs, images, signed uploads, generated reports.
- Backend: Cloud Functions for privileged writes, payment webhooks, external APIs, scheduled jobs, and sensitive logic.
- Security: Firebase Security Rules, App Check, IAM, server-side secrets.
- Local testing: Firebase Emulator Suite.
- Observability: Firebase/Google Cloud logs, Performance Monitoring, Analytics where appropriate.
- Config: Remote Config for rollout switches and model names.

## Multi-Tenant Shape

Prefer paths that make tenant boundaries obvious:

```text
organizations/{orgId}
organizations/{orgId}/members/{uid}
organizations/{orgId}/cases/{caseId}
organizations/{orgId}/cases/{caseId}/events/{eventId}
organizations/{orgId}/cases/{caseId}/files/{fileId}
users/{uid}
```

Security checks should prove:

- authenticated user exists
- user belongs to the org
- user has the required role
- target document is within the same org
- server-only fields cannot be client-written

## Server-Only Mutations

Use Cloud Functions or trusted server routes for:

- Stripe webhooks and billing state
- role changes
- invite acceptance with token validation
- document generation
- external API calls
- AI calls using private provider keys
- cross-document workflows that need transactional consistency
- audit event creation that clients must not forge

## Client-Side Firestore Access

Direct client Firestore access is acceptable only when:

- rules are strict
- query paths map to tenant boundaries
- list queries are bounded
- writes validate ownership and immutable fields
- sensitive computed fields are not client-writable

## AI Features

Use Firebase AI Logic when:

- using supported Gemini features directly from web/mobile fits the product
- App Check and per-user limits are acceptable
- prompts do not require private server-side tools or non-Google providers

Use Genkit/Cloud Functions when:

- prompts need private data retrieval
- outputs need validation before storage
- external model providers are involved
- auditability and observability matter
- you need server-side orchestration or RAG
