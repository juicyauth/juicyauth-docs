# Lockless - OTP Email Authentication

Welcome to Lockless, your solution for simple and secure OTP-based email authentication. This documentation will guide you through integrating Lockless into both your frontend and backend systems.

## What is Lockless?

Lockless is an authentication service that allows users to sign in without the need for passwords. Instead, users receive a One-Time Password (OTP) via email, making the authentication process both secure and user-friendly. Our service is ideal for developers looking for a seamless way to authenticate users in their applications.

## How It Works

Lockless operates in two main parts: **Client** and **Backend**.

### 1. Client

On the client side, users enter their email address to receive a one-time password (OTP). The process looks like this:

- The user enters their email and clicks "Send OTP".
- Lockless sends an OTP to the user's email.
- The user inputs the OTP to complete the authentication process.

### 2. Backend

On the backend side, developers only need to verify the JWT (JSON Web Token) received from the frontend. The process typically involves:

- The frontend sends the verified JWT to the backend.
- The backend verifies the JWT using the public key provided by Lockless through the /auth/public-key/ endpoint.

This setup allows developers to integrate secure authentication into their web, mobile, or CLI applications with minimal effort, focusing solely on JWT verification in the backend.

## Key Features

- **No Passwords**: Users authenticate through email OTP, eliminating the need for traditional passwords.
- **Easy Integration**: Minimal code required to connect Lockless to your frontend and backend.
- **Secure**: Uses RS256 algorithm for JWT verification to ensure high-level security.
- **Flexible**: Works with any platform, including web and mobile apps, without needing embedded webviews.
