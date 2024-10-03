### OTP Authentication Prompt

You can use this prompt in ChatGPT or Gemini to get help with implementing OTP login on your website or mobile app (client-side). 

---

**Prompt:**

I need help implementing OTP authentication in my project using these two API endpoints:  
1. `POST https://api.juicyauth.dev/auth/send-otp/` to send an OTP to the user's email (`email`, `app_id` required).  
2. `POST https://api.juicyauth.dev/auth/verify-otp/` to verify the OTP (`email`, `otp`, `app_id` required). On success, the response returns a JWT in the format: `{"jwt": "your_jwt_token"}`.

Can you provide an implementation example in [your chosen technology]?

---

**Important:** Remember to replace `[your chosen technology]` with the specific technology you're using (e.g., Flutter, React).
