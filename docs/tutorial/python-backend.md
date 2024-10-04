# Python JWT Verification

This tutorial will guide you through verifying JSON Web Tokens (JWTs) in Python using JuicyAuth's public key. JWTs are used to securely transmit information between parties as a JSON object.

## Step 1: Install Required Libraries

First, ensure you have the `PyJWT` library installed:

```bash
pip install PyJWT requests
```

## Step 2: Fetch the Public Key

To verify a JWT, you need to fetch the public key from the JuicyAuth API. Here's how you can retrieve it:

```python
import requests

def get_public_key():
    url = "https://api.juicyauth.com/auth/public-key/"
    response = requests.get(url)
    return response.text

# Example usage
public_key = get_public_key()
print(public_key)
```

## Step 3: Verify JWT and Extract Email

Once you have the public key, you can use it to verify the JWT and extract the user's email from the "sub" field in the payload:

```python
import jwt

def verify_jwt(token: str, public_key: str) -> str:
    try:
        payload = jwt.decode(token, public_key, algorithms=["RS256"])
        user_id = payload.get("sub")  # Extract the user's id
        return user_id
    except jwt.ExpiredSignatureError:
        raise ValueError("Token has expired")
    except jwt.InvalidTokenError:
        raise ValueError("Invalid token")

# Example usage
token = "your_jwt_token"
public_key = get_public_key()

try:
    user_id = verify_jwt(token, public_key)
    print("Token is valid, user id:", user_id)
except ValueError as e:
    print("Token verification failed:", str(e))
```

This function will decode and validate the JWT, and extract the user's email (which is stored in the "sub" field). If the token has expired or is invalid, an appropriate exception will be raised.


## Step 4: Using JWT Verification in FastAPI

To integrate this into a FastAPI application, you can use the verify_jwt function as a dependency in your request handlers. Here's how to extract the JWT from the Authorization header:

```python
from fastapi import FastAPI, Depends, HTTPException, Header

app = FastAPI()

def jwt_dependency(authorization: str = Header(...)):
    if not authorization.startswith("Bearer "):
        raise HTTPException(status_code=400, detail="Invalid authorization header format")
    
    token = authorization.split(" ")[1]  # Extract the token from the header
    public_key = get_public_key()

    try:
        user_id = verify_jwt(token, public_key)
        return user_id
    except ValueError as e:
        raise HTTPException(status_code=401, detail="Invalid or expired token")

@app.get("/protected-route/")
def protected_route(user_id: str = Depends(jwt_dependency)):
    return {"message": "Access granted", "user_id": user_id}
```

