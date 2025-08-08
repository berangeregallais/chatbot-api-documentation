# Webhooks

Webhooks allow your system to receive real-time updates from the E-commerce Chatbot API when key events occur — such as new messages, analytics thresholds, or user interactions.

---

## 🔔 How It Works

1. You register a publicly accessible HTTPS endpoint.
2. Our system sends a POST request to that URL when events occur.
3. You validate the signature and process the payload.

---

## 📬 Example Payload

```json
{
  "event": "chat.message.sent",
  "timestamp": "2025-06-10T14:23:00Z",
  "data": {
    "message_id": "msg_789",
    "user_id": "user_123",
    "text": "I need help with my order",
    "intent": "return_order"
  }
}
```

---

## 🧾 Supported Events

| Event Name               | Description                                    |
| ------------------------ | ---------------------------------------------- |
| `chat.message.sent`      | A user message has been processed by the AI    |
| `chat.feedback.received` | A user gave feedback on the chatbot's response |
| `chat.alert.triggered`   | Anomaly detected (e.g. inappropriate request)  |

---

## 🔐 Signature Validation

Each webhook request includes an `-Signature` header :

```makefile
X-Signature: sha256=ab12c3d4ef567...
```

To verify :

1. Compute an HMAC-SHA256 hash of the raw request body using your webhook secret.
2. Compare it to the value in the X-Signature header.
3. If they match, the payload is authentic.

---

## ⚠️ Error Handling & Retries

- We retry failed webhooks up to 3 times, with exponential backoff.
- A `2xx` HTTP response acknowledges successful delivery.
- A `4xx` or `5xx` response triggers a retry.

---

## 📘 Tips

- Always respond quickly (under 3 seconds).
- Use a queue or background worker to process data.
- Keep webhook secrets safe and rotate periodically.

---

## 🛠️ Registering Your Webhook

To register a webhook endpoint, go to the developer dashboard and provide :

- Public HTTPS URL
- Events to subscribe to
- Secret for signing requests
