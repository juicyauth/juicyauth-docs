# Send OTP

**Endpoint:**  
`POST https://api.juicyauth.dev/auth/send-otp/`

This endpoint is used by the **frontend** to send a one-time password (OTP) to the user's email address. The OTP is used for user authentication.

## Request Body

```json
{
  "email": "user@example.com",
  "app_id": "your_app_id"
}
```

- `email`: The email address where the OTP will be sent.
- `app_id`: The application’s unique identifier.

## Response
- `200 OK`: OTP successfully sent.
- `422 Unprocessable Entity`: Invalid input (e.g., missing email or app_id).

## Example Request

```bash
curl -X POST "https://api.juicyauth.com/auth/send-otp/" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "app_id": "your_app_id"
}'
```
