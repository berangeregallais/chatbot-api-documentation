# Rate Limits & Best Practices

To ensure fair usage and system stability, the E-commerce Chatbot API enforces rate limiting on all endpoints.

---

## ⏱️ Global Rate Limits

| Endpoint Category     | Limit                    | Window     |
|-----------------------|--------------------------|------------|
| `/chat/send`          | 60 requests per minute   | per user   |
| `/chat/history`       | 100 requests per minute  | per user   |
| `/chat/analytics`     | 30 requests per minute   | per account |

> ⚠️ If you exceed the limit, the API will return a `429 Too Many Requests` response.

---

## 📦 Response on Limit Exceeded

```json
{
  "error": {
    "code": 429,
    "message": "Rate limit exceeded. Try again later."
  }
}
```

---

## 🔄 Retry-After Header

When throttled, the response will include a `Retry-After` header indicating how many seconds to wait :

```makefile
Retry-After: 30
```

---

## ✅ Best Practices

- Use exponential backoff when retrying failed requests.
- Avoid loops or bulk calls without delays.
- Cache frequent responses where possible.
- Monitor rate limit headers returned by the API :

```makefile
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1718023980
```

- Plan for spikes : if your app may exceed limits, contact support for higher quotas.

---

## 📌 Contact

If your app requires a custom rate limit due to business needs, please reach out via the developer portal.
