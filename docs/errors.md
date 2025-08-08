# Error Handling

The API uses standard HTTP status codes and structured error responses to help you diagnose and resolve issues quickly.

---

## ⚠️ HTTP Status Codes

| Code | Meaning                  | When it Occurs                                      |
|------|--------------------------|-----------------------------------------------------|
| 200  | OK                       | Successful request                                  |
| 400  | Bad Request              | Missing or invalid parameters                       |
| 401  | Unauthorized             | Missing or invalid API key or token                 |
| 403  | Forbidden                | Access denied to resource                           |
| 404  | Not Found                | Invalid endpoint or resource                        |
| 429  | Too Many Requests        | Rate limit exceeded                                 |
| 500  | Internal Server Error    | Unexpected error on the server                      |

---

## 🔁 Common Error Responses

```json
{
  "error": "invalid_request",
  "message": "Missing required field: message"
}
```

```json
{
  "error": "unauthorized",
  "message": "Invalid API key provided"
}
```

```json
{
  "error": "rate_limit_exceeded",
  "retry_after_seconds": 60
}
```

---

## 🧠 Handling Inappropriate Responses

In rare cases, the AI may return responses deemed inappropriate for your brand. We recommend :

- Filtering sensitive content on your frontend
- Reporting flagged messages to support for retraining
- Using moderation settings (coming soon)

---

## 🔧 Best Practices

- Validate input fields before calling the API
- Use try/catch or `.catch()` blocks to handle errors gracefully
- Log errors for future diagnosis
- Respect rate limit headers to prevent interruptions.
