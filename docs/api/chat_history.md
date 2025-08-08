# GET /api/v1/chat/history

Retrieve the conversation history for a given user.

---

## 🔐 Authentication

This endpoint requires an API key in the `Authorization` header:

```makefile
Authorization: Bearer YOUR_API_KEY
```

---

## 🧾 Query Parameters

| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|----------------------------------|
| `user_id` | string | ✅        | Unique identifier of the user     |
| `limit`   | int    | ❌        | Number of messages to retrieve (default: 20) |

---

## 📤 Response

```json
{
  "conversation_id": "conv_789",
  "messages": [
    {
      "sender": "user",
      "message": "I want to return my order",
      "timestamp": "2025-06-09T10:10:00Z"
    },
    {
      "sender": "assistant",
      "message": "Sure, I can help you return your order.",
      "timestamp": "2025-06-09T10:12:00Z"
    }
  ]
}
```

| Field             | Type   | Description             |
| ----------------- | ------ | ----------------------- |
| `conversation_id` | string | ID of the conversation  |
| `messages`        | array  | List of message objects |

Each message object contains :

| Field       | Type   | Description                       |
| ----------- | ------ | --------------------------------- |
| `sender`    | string | Either "user" or "assistant"      |
| `message`   | string | The text content of the message   |
| `timestamp` | string | ISO 8601 timestamp of the message |

---

## ⚠️ Errors

| Code | Message                 | Meaning                            |
| ---- | ----------------------- | ---------------------------------- |
| 401  | `Unauthorized`          | Missing or invalid API key         |
| 400  | `Bad Request`           | Missing or invalid parameters      |
| 429  | `Rate limit exceeded`   | Too many requests                  |
| 500  | `Internal server error` | Temporary issue on the server side |
