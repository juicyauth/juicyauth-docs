# Get Public Key

**Endpoint:**  
`GET https://api.juicyauth.dev/auth/public-key/`

This endpoint is used by the **backend** to retrieve the public key used for verifying JWTs (JSON Web Tokens) issued by JuicyAuth.

## Response
- `200 OK`: A string containing the public key in PEM format.

## Example Request

```bash
curl -X GET "https://api.juicyauth.com/auth/public-key/"
```
