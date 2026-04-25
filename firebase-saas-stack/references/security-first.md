# Firebase Security First

Security does not happen automatically. Firebase gives strong building blocks, but the app is unsafe if rules, auth, server-side secrets, and billing guardrails are sloppy.

## Non-Negotiable Gates

- Start Firestore, Realtime Database, and Storage rules locked down.
- Write Security Rules when adding each document path or storage path.
- Test rules locally with the Emulator Suite when practical.
- Never deploy broad public write rules.
- Never rely on client code to enforce authorization.
- Never put service account private keys in frontend code or committed files.
- Never put Stripe secret keys, webhook secrets, model provider keys, email provider secrets, or payment processor credentials in frontend code.
- Keep privileged writes in Cloud Functions or trusted server code.
- Enforce tenant IDs and roles in rules and server code.
- Set billing budgets and alerts before paid production usage.
- Use separate dev/staging/prod Firebase projects.

## API Keys

Normal Firebase web config API keys identify the project and are not the same as private service credentials. Do not treat hiding them as the security model.

Still apply restrictions and limits:

- restrict API keys to expected APIs
- restrict web keys to expected referrers where appropriate
- monitor unusual usage
- use Security Rules and App Check for actual access control

Treat these as secrets:

- service account private keys
- FCM server keys
- Gemini Developer API keys
- Stripe secret and webhook keys
- OpenAI/Anthropic/other model provider keys
- email/SMS provider credentials
- private OAuth client secrets

## App Check

Use App Check for production web/mobile clients to reduce abuse from unauthorized clients. App Check complements Auth and Security Rules; it does not replace either.

## Auth And Roles

Prefer managed OAuth/OIDC providers when they fit the customer base. For B2B SaaS:

- model organizations/tenants explicitly
- store roles or membership documents intentionally
- consider custom claims for coarse-grained authorization
- enforce fine-grained role checks in Firestore rules or server code
- support account recovery and admin transfer paths

## Billing Risk

Budget alerts notify; they do not hard-cap all usage. For paid projects:

- create budget alerts before production
- monitor Firestore reads/writes/storage and Functions invocations
- avoid unbounded list queries
- paginate aggressively
- avoid repeated listeners on high-volume collections
- consider kill-switches or feature flags for runaway workloads
