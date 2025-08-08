# GET /api/v1/chat/analytics

Retrieve analytics data about chatbot usage and performance.

---

## 🔐 Authentication

This endpoint requires an API key in the `Authorization` header:

```makefile
Authorization: Bearer YOUR_API_KEY
```

---

## 🧾 Query Parameters

| Parameter     | Type   | Required | Description                          |
|---------------|--------|----------|------------------------------------|
| `start_date`  | string | ❌        | Start date for analytics (YYYY-MM-DD) |
| `end_date`    | string | ❌        | End date for analytics (YYYY-MM-DD)   |

---

## 📤 Response

```json
{
  "total_requests": 1250,
  "average_response_time_ms": 350,
  "error_rate": 0.02,
  "most_common_queries": [
    "return order",
    "track shipment",
    "product recommendation"
  ]
}
```

| Field                      | Type    | Description                              |
| -------------------------- | ------- | ---------------------------------------- |
| `total_requests`           | integer | Total number of chat requests received   |
| `average_response_time_ms` | integer | Average response time in milliseconds    |
| `error_rate`               | float   | Proportion of failed requests (0 to 1)   |
| `most_common_queries`      | array   | List of most frequent user query phrases |

---

## ⚠️ Errors

| Code | Message                 | Meaning                            |
| ---- | ----------------------- | ---------------------------------- |
| 401  | `Unauthorized`          | Missing or invalid API key         |
| 400  | `Bad Request`           | Invalid date range or parameters   |
| 429  | `Rate limit exceeded`   | Too many requests                  |
| 500  | `Internal server error` | Temporary issue on the server side |
