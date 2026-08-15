# user-proto

Shared protobuf definitions for the User domain. This package is consumed by:

- **auth-service** (Go) — user identity and authentication
- **billing-api** (TypeScript) — account and payment association
- **notifications-svc** (Python) — delivery preferences and contact routing

## Usage

Generated clients are published to the internal registry on each tag. Downstream services pin to a specific version and receive Ripple-generated fix PRs on breaking changes.
# v2
# trigger v3
# trigger v3
# trigger v4
