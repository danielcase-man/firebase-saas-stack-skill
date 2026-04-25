# Official Firebase Docs To Check

Use current official Firebase docs before making time-sensitive claims about product names, quotas, pricing, or deployment commands.

## Core Stack

- Firebase App Hosting SDK integration: https://firebase.google.com/docs/app-hosting/firebase-sdks
- Firebase Authentication: https://firebase.google.com/docs/auth
- Firebase Security Rules: https://firebase.google.com/docs/rules
- Cloud Firestore data model: https://firebase.google.com/docs/firestore/data-model
- Firestore role-based access example: https://firebase.google.com/docs/firestore/solutions/role-based-access
- Firestore rules structure: https://firebase.google.com/docs/firestore/security/rules-structure
- Firebase App Check: https://firebase.google.com/docs/app-check

## Security, Billing, And Quotas

- Firebase security checklist: https://firebase.google.com/support/guides/security-checklist
- Firebase API keys: https://firebase.google.com/docs/projects/api-keys
- Firestore quotas and limits: https://firebase.google.com/docs/firestore/quotas
- Firebase pricing plans: https://firebase.google.com/docs/projects/billing/firebase-pricing-plans
- Advanced billing alerts: https://firebase.google.com/docs/projects/billing/advanced-billing-alerts-logic

## AI

- Firebase AI Logic: https://firebase.google.com/docs/ai-logic
- Firebase Genkit: https://firebase.google.com/products/genkit

## Current Notes From 2026-04 Docs Snapshot

- Firebase App Hosting is positioned for modern dynamic web apps using Firebase JavaScript SDK and Admin SDK.
- Firebase Auth supports common SaaS identity needs, and Identity Platform adds enterprise features such as MFA, blocking functions, SAML/OIDC, audit logging, and multi-tenancy.
- Firestore is a NoSQL document database with documents organized in collections, not SQL tables/rows.
- Security Rules protect Firebase database/storage paths and should be tested with emulators before production.
- Firebase security guidance recommends production/locked rules by default and treating rules like schema.
- Firebase API keys for Firebase services are not the authorization mechanism, but API key restrictions and limits are still recommended.
- Service account keys, FCM server keys, Gemini Developer API keys, Stripe keys, and other third-party secrets must stay private.
- App Check complements Auth and Security Rules by helping reject requests from unauthorized clients.
- Budget alerts help detect spend, but alerts are not a complete hard cap.
