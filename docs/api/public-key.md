# Get Public Key

**Endpoint:**  
`GET https://api.lockless.dev/auth/public-key/`

This endpoint is used by the **backend** to retrieve the public key used for verifying JWTs (JSON Web Tokens) issued by Lockless.

## Response
- `200 OK`: A string containing the public key in PEM format.

## Example Request

```bash
curl -X GET "https://api.lockless.com/auth/public-key/"
```
