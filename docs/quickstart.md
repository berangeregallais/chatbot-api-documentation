# 🔥 Quickstart Guide

Welcome! This guide will help you make your **first call to the AI Assistant API** in under 5 minutes.

---

## ✅ Requirements

- An **API key** (example): `api_key_1234567890abcdef`
- A tool like `curl`, Postman, or a script in Python/JavaScript

---

## 🛠️ Make a `POST /chat/send` request

### Request

```http
POST /api/v1/chat/send
Content-Type: application/json
Authorization: Bearer api_key_1234567890abcdef
```

```json
{
  "message": "I want to return my order",
  "user_id": "user_123456789",
  "context": {
    "order_id": "ORD-456",
    "purchase_date": "2025-01-15"
  }
}
```

---

### Example response

```json
{
  "reply": "Sure, I can help you return your order. Please follow this link: https://ecommerce.ai/returns/ORD-456",
  "conversation_id": "conv_789",
  "timestamp": "2025-06-09T10:12:00Z"
}
```

---

### Code Examples

#### Using cURL

```bash
curl -X POST https://api.ecommerce.ai/v1/chat/send \
  -H "Authorization: Bearer api_key_1234567890abcdef" \
  -H "Content-Type: application/json" \
  -d '{
    "message": "I want to return my order",
    "user_id": "user_123",
    "context": {
      "order_id": "ORD-456",
      "purchase_date": "2025-01-15"
    }'
```

---

#### Python (requests)

```python
import requests

url = "https://api.ecommerce.ai/v1/chat/send"
headers = {
    "Authorization": "Bearer api_key_1234567890abcdef",
    "Content-Type": "application/json"
}
payload = {
    "message": "I want to return my order",
    "user_id": "user_123",
    "context": {
        "order_id": "ORD-456",
        "purchase_date": "2025-01-15"
    }
}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

---

#### JavaScript (Fetch API)

```js
fetch("https://api.ecommerce.ai/v1/chat/send", {
  method: "POST",
  headers: {
    "Authorization": "Bearer api_key_1234567890abcdef",
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    message: "I want to return my order",
    user_id: "user_123",
    context: {
      order_id: "ORD-456",
      purchase_date: "2025-01-15"
    }
  })
})
  .then(res => res.json())
  .then(console.log);
```

---

### Results

You’ll receive a **structured reply** based on the user’s intent and context — ready to be integrated into your support system or chatbot.

> 👉 **Next:** check out the [API reference](api/chat_send.md) or explore more [code samples](examples.md).
