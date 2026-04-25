# Firebase Fit Gate

Use this before recommending Firebase or refactoring an existing app to Firebase.

## Good Fit

Firebase is usually a good candidate when the product is:

- document-centric rather than join-heavy
- built around customers, tenants, cases, jobs, projects, files, messages, approvals, or status updates
- web/mobile customer-facing SaaS
- real-time or collaboration-heavy
- early-stage and needs auth, database, storage, backend functions, hosting, and analytics quickly
- expected to start small and harden as revenue grows

Examples:

- attorney case/DV workflow portal
- appraiser intake and report workflow
- construction vendor bid/status portal
- internal-to-customer approval dashboard
- mobile companion app with the same backend

## Conditional Fit

Firebase can work, but require extra design effort, when:

- customers need strict tenant isolation
- users can belong to many organizations with different roles
- workflows have important audit history
- the app has reporting needs but not complex analytics
- payment state must be reconciled with Stripe or another payment provider
- files contain sensitive customer documents

For these, require a written architecture plan, data model, and Security Rules checklist before implementation.

## Poor Fit Or Needs SQL

Do not blindly choose Firestore when the product is dominated by:

- complex joins
- many-to-many relational queries
- ad hoc reporting
- normalized accounting/ledger data
- strict transactional constraints across many records
- complex analytics across tenants
- existing Postgres workflows that already fit the product

When these dominate, consider Postgres, Supabase, Cloud SQL, Firebase SQL/Data Connect options, or a hybrid architecture where Firebase handles auth/hosting/realtime edges and SQL handles relational core data.

## Required Decision Output

Write:

- verdict: good fit, conditional fit, poor fit
- reason
- core entities
- tenant boundary
- top 5 query patterns
- sensitive data involved
- services selected
- services deliberately not selected
- risks and mitigations
