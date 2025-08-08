# 🧪 API Playground

Use this simple interactive playground to test the `/chat/send` endpoint directly from your browser.

> 💡 This demo uses JavaScript `fetch()` to simulate API calls. Replace the placeholder API key before using.

---

## 🔧 Try the Chat API

### Message Input

#### 🧪 API Playground (Mocked)

<div class="playground-container">
  <label for="message">Message :</label><br />
  <input
    type="text"
    id="message"
    class="playground-input"
    placeholder="Write your message here"
  /><br />
  <button onclick="sendMessage()">🚀 Send Message</button>
  <pre id="output"></pre>

  <script>
    async function sendMessage() {
      const message = document.getElementById("message").value;
      const output = document.getElementById("output");

      // Simulated API response
      const mockedResponse = {
        reply: "Your return request has been received.",
        intent: "return_order",
        context: {
          order_id: "ORD-456"
        }
      };

      output.textContent = JSON.stringify(mockedResponse, null, 2);
    }
  </script>
</div>

---

## 🛑 Security Notice

This playground is for demo purposes **only**. Do not expose your real API key in production or share it in public code.

For production use :

- Always secure API keys on the server side.
- Rate-limit interactive endpoints.
- Sanitize and validate all inputs.

---

## ✅ Next Steps

- Explore more code examples
- Review error handling
- Learn how to integrate real-time webhooks
