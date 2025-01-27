<p>Simplifying API Integration Through Clear and User-Friendly Documentation</p>
___

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Getting Started - Real-Time Chat API Documentation</title>
    <link rel="stylesheet" href="../styles.css"><!-- Navigation Menu -->
   <nav class="horizontal-menu">
    <a href="index.html" >Introduction</a>  
    <a href="../docs/getting-started.html">Getting Started</a>
    <a href="../docs/endpoints.html">Endpoints</a>
    <a href="../examples/integration-examples.html" class="active">Integration Examples</a>
    <a href="../docs/troubleshooting.html">Troubleshooting</a>
</nav> 
<link rel="stylesheet" href="../styles.css">
# Integration Examples

This section provides real-world examples to demonstrate how developers can use the Real-Time Chat API in their projects.

---

## Example 1: Sending a Message to a Chat

This example shows how to authenticate, create a chat, and send a message.

### Step 1: Authenticate and Get an Access Token
Use the `/auth/login` endpoint to authenticate and obtain an access token:
```javascript
const axios = require('axios');

async function authenticate() {
  const response = await axios.post('https://api.example.com/auth/login', {
    username: 'user@example.com',
    password: 'password123'
  });

  console.log('Access Token:', response.data.accessToken);
  return response.data.accessToken;
}
```

---

### Step 2: Create a Chat
Once authenticated, use the `/chats/create` endpoint to create a new chat room:
```javascript
async function createChat(accessToken) {
  const response = await axios.post(
    'https://api.example.com/chats/create',
    {
      name: 'Project Discussion',
      participants: ['user1@example.com', 'user2@example.com']
    },
    {
      headers: { Authorization: `Bearer ${accessToken}` }
    }
  );

  console.log('Chat ID:', response.data.chatId);
  return response.data.chatId;
}
```

---

### Step 3: Send a Message
Use the `/messages/send` endpoint to send a message to the created chat:
```javascript
async function sendMessage(accessToken, chatId) {
  const response = await axios.post(
    'https://api.example.com/messages/send',
    {
      chatId: chatId,
      message: 'Hello, team! Let’s discuss the project here.'
    },
    {
      headers: { Authorization: `Bearer ${accessToken}` }
    }
  );

  console.log('Message ID:', response.data.messageId);
}
```

---

### Complete Flow
Here’s the complete flow in one script:
```javascript
(async function main() {
  const accessToken = await authenticate();
  const chatId = await createChat(accessToken);
  await sendMessage(accessToken, chatId);
})();
```

---

## Example 2: Fetching Chat Messages

Retrieve messages from a specific chat using the `/messages` endpoint:
```javascript
async function fetchMessages(accessToken, chatId) {
  const response = await axios.get('https://api.example.com/messages', {
    params: { chatId: chatId, limit: 10 },
    headers: { Authorization: `Bearer ${accessToken}` }
  });

  console.log('Messages:', response.data);
}

(async function main() {
  const accessToken = await authenticate();
  const chatId = 'existing-chat-id';
  await fetchMessages(accessToken, chatId);
})();
```

---

These examples demonstrate how to integrate the API into a real-world project. For more detailed guidance, refer to the [Endpoints Documentation](../docs/endpoints.md).
