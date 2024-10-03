# Verify OTP

**Endpoint:**  
`POST https://api.juicyauth.dev/auth/verify-otp/`

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
- **200 OK**: OTP successfully verified.
    ```
    {
      "jwt": ""
    }
    ```

- **400 Bad Request**: OTP verification failed or the OTP is invalid.
    ```
    {
      "error_code": "otp_verified_failed",
      "error_description": "OTP verification failed."
    }
    ```
- **422 Unprocessable Entity**: Invalid OTP, email, or app ID.


## Error Codes for Bad Request

| Error Code              | Description                             |
|-------------------------|-----------------------------------------|
| `otp_verified_failed`    | The OTP verification has failed.        |
| `otp_expired`            | The OTP has expired.                    |
| `user_banned`            | The user has been banned from the app.  |
| `otp_sent_failed`        | Failed to send OTP email.               |


## Example Request

```bash
curl -X POST "https://api.juicyauth.com/auth/verify-otp/" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "otp": "123456",
  "app_id": "your_app_id"
}'
```