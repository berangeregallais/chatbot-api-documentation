# API Usage Examples

Here are code examples to help you quickly integrate the E-commerce Chatbot API into your applications.

---

## 💬 Send a Chat Message

### ▶️ JavaScript (Fetch)

```javascript
fetch("https://api.ecommerce.com/api/v1/chat/send", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_API_KEY"
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
  .then(response => response.json())
  .then(data => console.log(data));
```

---

### 🐍 Python (requests)

```py
import requests

url = "https://api.ecommerce.com/api/v1/chat/send"
headers = {
    "Authorization": "Bearer YOUR_API_KEY",
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

### 💻 cURL

```bash
curl -X POST https://api.ecommerce.com/api/v1/chat/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
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

## 📜 Retrieve Chat History (Python)

```py
import requests

params = {
    "user_id": "user_123",
    "limit": 5
}
headers = {"Authorization": "Bearer YOUR_API_KEY"}

response = requests.get("https://api.ecommerce.com/api/v1/chat/history", params=params, headers=headers)
print(response.json())
```

---

## 📈 Get Analytics (JavaScript)

```js
fetch("https://api.ecommerce.com/api/v1/chat/analytics", {
  headers: {
    "Authorization": "Bearer YOUR_API_KEY"
  }
})
  .then(res => res.json())
  .then(data => console.log(data));
```

---

For more integration help, refer to the [Quickstart Guide](quickstart.md) or the [API reference](api/chat_send.md).
