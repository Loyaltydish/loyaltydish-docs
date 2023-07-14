To ensure our platform remains stable and fair for everyone, all LoyaltyDish APIs are rate-limited.

## Rate limits
LoyaltyDish API is rate limited to 1000 requets/m.

## Error handling
Our API replies with 3 types of errors for various reasons. Each error contains a `code` and a `message` properties.

- `permission_denied`: returned when the user does not have access to the requested resources.
- `does_not_exist`: returned when the requested resource does not exist.
- `invalid`: returned when the request properties or a business requirement is not fulfilled.
