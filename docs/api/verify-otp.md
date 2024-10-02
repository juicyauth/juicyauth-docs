# Verify OTP

**Endpoint:**  
`POST https://api.lockless.dev/auth/verify-otp/`

This endpoint is used by the **backend** to verify the one-time password (OTP) sent to the user's email.

## Request Body

```json
{
  "email": "user@example.com",
  "otp": "123456",
  "app_id": "your_app_id"
}
```

- `email`: The user's email address.
- `otp`: The OTP received by the user via email.
- `app_id`: The application’s unique identifier.

## Response
- `200 OK`: OTP successfully verified.
```json
{"jwt": ""}
```
- `422 Unprocessable Entity`: Invalid OTP, email, or app ID.

## Example Request

```bash
curl -X POST "https://api.lockless.com/auth/verify-otp/" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "otp": "123456",
  "app_id": "your_app_id"
}'
```