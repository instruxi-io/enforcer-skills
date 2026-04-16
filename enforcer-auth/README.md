# /enforcer-auth

Authentication, authorization, and verification flows for the Enforcer platform.

## When to use
- Building login or signup (SIWE, passkeys, OAuth, email OTP, Privy)
- Managing API keys (create, rotate, revoke)
- Setting up verification (email, phone, group challenge)
- Handling terms of service acceptance
- Configuring OPA-based authorization policies

## What it covers
- SIWE (Sign-In With Ethereum) and passkey auth flows
- OAuth and email OTP login
- Privy integration
- API key lifecycle management
- OPA authorization rules and middleware
- Email and phone verification
- Group challenge verification
- Terms acceptance tracking

## Tips
- Auth flows return JWTs; most downstream endpoints require a valid bearer token
- API keys are scoped per tenant; use the admin skill for tenant-level key management
- Verification endpoints are separate from login; call them after initial auth
- Group challenges require the user to already belong to the target group
