# Firebase SaaS Stack Skill

Codex skill for evaluating and implementing secure Firebase-backed SaaS stacks for customer-facing workflow apps.

## One-Line Install Prompt

Give Codex this prompt:

```text
Use $skill-installer to install the Codex skill from https://github.com/danielcase-man/firebase-saas-stack-skill/tree/main/firebase-saas-stack, then tell me to restart Codex.
```

## What It Does

The skill makes Codex perform a Firebase fit check before building or refactoring. It covers:

- Firebase vs SQL/Postgres fit
- Firestore NoSQL data modeling
- Firebase Auth / Identity Platform
- Security Rules and App Check
- Cloud Functions for privileged operations
- Cloud Storage for customer files
- budget alerts and billing risk
- Stripe/payment boundaries
- Firebase AI Logic vs Genkit/Cloud Functions

## Direct Manual Install

If the installer is not available, copy the `firebase-saas-stack` folder into:

```text
~/.codex/skills/firebase-saas-stack
```

Then restart Codex.
