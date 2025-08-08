# Authentication

To use the E-commerce Chatbot API, all requests must be authenticated using an API key or OAuth 2.0.

---

## 🔑 API Key (Simple Auth)

### Sending an API Key

You must include your API key in the `Authorization` header of each request:

```makefile
Authorization: Bearer YOUR_API_KEY
```

---

### Example (cURL)

```bash
curl -X POST https://api.example.com/api/v1/chat/send \
  -H "Authorization: Bearer sk_test_your_api_key" \
  -H "Content-Type: application/json" \
  -d '{
        "message": "I need help with my order",
        "user_id": "user_123"
      }'
```

---

## 🔐 OAuth 2.0 (Advanced Auth)

> **Optional** — for apps with multiple users or needing delegated access.

1. Obtain a client ID and secret from the developer dashboard.  
2. Implement the OAuth 2.0 flow (authorization code grant or client credentials).  
3. Use the returned access token as a Bearer token in the `Authorization` header.

---

### Example Header with OAuth Token

```makefile
Authorization: Bearer ya29.a0ARrdaM9XYZabcToken
```

---

## 🚫 Common Errors

| Error Code | Message             | Explanation                                   |
| ---------- | ------------------- | --------------------------------------------- |
| 401        | `Unauthorized`      | Missing or invalid token/API key              |
| 403        | `Forbidden`         | Token is valid but lacks required permissions |
| 429        | `Too Many Requests` | Rate limit exceeded                           |

---

## 🧪 Tips

- Never expose your API keys in frontend apps.
- Rotate API keys periodically.
- Use OAuth if you need to access the API on behalf of end users.
