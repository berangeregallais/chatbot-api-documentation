# POST /api/v1/chat/send

Send a user message to the AI assistant and receive a response based on their context.

---

## 🔐 Authentication

This endpoint requires an API key in the `Authorization` header:

```makefile
Authorization: Bearer YOUR_API_KEY
```

---

## 🧾 Request Body

```json
{
  "message": "I want to return my order",
  "user_id": "user_123",
  "context": {
    "order_id": "ORD-456",
    "purchase_date": "2025-01-15"
  }
}
```

| Field     | Type   | Required | Description                          |
| --------- | ------ | -------- | ------------------------------------ |
| `message` | string | ✅        | The user's input message             |
| `user_id` | string | ✅        | Unique user ID                       |
| `context` | object | ❌        | Optional metadata (e.g., order info) |

### Context object fields

| Field          | Type   | Required | Description                         |
|----------------|--------|----------|-------------------------------------|
| `order_id`     | string | ❌        | Unique identifier of the order       |
| `purchase_date`| string | ❌        | Date of the purchase (YYYY-MM-DD)   |

---

## 📤 Response

```json
{
  "reply": "Sure, I can help you return your order.",
  "conversation_id": "conv_789",
  "timestamp": "2025-06-09T10:12:00Z"
}
```

| Field             | Type   | Description                        |
| ----------------- | ------ | ---------------------------------- |
| `reply`           | string | AI-generated response              |
| `conversation_id` | string | ID to track the conversation       |
| `timestamp`       | string | ISO 8601 timestamp of the response |

---

## ⚠️ Errors

| Code | Message                 | Meaning                            |
| ---- | ----------------------- | ---------------------------------- |
| 401  | `Unauthorized`          | Missing or invalid API key         |
| 429  | `Rate limit exceeded`   | Too many requests                  |
| 500  | `Internal server error` | Temporary issue on the server side |
