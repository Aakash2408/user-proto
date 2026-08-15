# Breaking Change: v2.0.0

## Summary

The `phone_number` field has been **removed** from `User`, `CreateUserRequest`, and related messages. Phone number management is now handled by the new `ContactService`.

## Reason

Phone numbers require PII-specific handling (encryption at rest, GDPR right-to-erasure, carrier validation). Centralizing this in `ContactService` enables:

- Unified compliance across all contact channels
- Multi-phone support (work, personal, emergency)
- Carrier validation and formatting normalization

## Migration

| Before (v1) | After (v2) |
|---|---|
| `user.phone_number` | `ContactService.GetPhone(user_id)` |
| `CreateUserRequest.phone_number` | `ContactService.AddPhone(user_id, number)` |

## Affected Services

- `auth-service` — remove phone from signup flow, call ContactService
- `billing-api` — replace `user.phone_number` with ContactService lookup
- `notifications-svc` — switch SMS routing to ContactService.GetPhone
- `tests/test_user_api` — update fixtures, remove phone assertions
