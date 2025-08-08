# Welcome to Chatbot API Documentation

## 🎯 What is this API for ?

Welcome to the API documentation for the E-commerce Chatbot Assistant.
This API allows you to integrate a **conversational AI assistant** into your e-commerce application.  
It can handle **customer service requests**, provide **order-related information**, and offer **personalized product recommendations** — all through natural language.

## Getting Started

### Requirements

- An API key (get one from your dashboard)
- An HTTP-capable frontend or backend

### Authentication

All endpoints require authentication via API key in the `Authorization` header :

```makefile
Authorization: Bearer YOUR_API_KEY
```

- Format: Bearer Token
- Lifetime: 24h (configurable)

### Quickstart

```bash
curl -X POST https://api.chatbot.ai/v1/chat \
  -H "Authorization: Bearer sk-123..." \
  -H "Content-Type: application/json" \
  -d '{"message": "Where is my order?"}'
```

Expected response:

```json
{ "reply": "Your order ORD-789 is on the way!" }
```

---

## API Reference

This section lists all available endpoints and their purposes.

---

### Endpoints

| Endpoint              | Method | Description                               |
|-----------------------|--------|-------------------------------------------|
| [`/api/v1/chat/send`](api/chat_send.md)        | POST   | Send a message to the chatbot assistant. |
| [`/api/v1/chat/history`](api/chat_history.md)  | GET    | Retrieve user conversation history.       |
| [`/api/v1/chat/analytics`](api/chat_analytics.md) | GET    | Get analytics on chatbot usage.            |

---

### Rate Limiting

The API enforces rate limits to ensure fair usage.  
Please refer to each endpoint’s documentation for specific limits and best practices.

---

For detailed information, click on the [endpoint links](api/chat_send.md) above.
