<!-- Navigation Menu -->
<link rel="stylesheet" href="../styles.css">
<nav class="horizontal-menu">
    <a href="../docs/getting-started.html">Getting Started</a>
    <a href="../docs/endpoints.html" class="active">Endpoints</a>
    <a href="../examples/integration-examples.html">Integration Examples</a>
    <a href="../docs/troubleshooting.html">Troubleshooting</a>
</nav> 

# API Endpoints

This section provides detailed documentation for the available API endpoints in the Real-Time Chat API.

---

## Authentication

**Endpoint:** `/auth/login`

- **Description:** Authenticate a user and return an access token.
- **Method:** `POST`
- **Request Body:**
  ```json
  {
    "username": "string",
    "password": "string"
  }
  ```
- **Response:**
  ```json
  {
    "accessToken": "string",
    "refreshToken": "string"
  }
  ```
- **Error Codes:**
  - `401`: Invalid credentials
  - `400`: Missing parameters

---

## Send Message

**Endpoint:** `/messages/send`

- **Description:** Send a new message to a specific chat.
- **Method:** `POST`
- **Request Body:**
  ```json
  {
    "chatId": "string",
    "message": "string"
  }
  ```
- **Response:**
  ```json
  {
    "messageId": "string",
    "timestamp": "string"
  }
  ```
- **Error Codes:**
  - `404`: Chat not found
  - `400`: Invalid request body

---

## Fetch Messages

**Endpoint:** `/messages`

- **Description:** Retrieve messages from a specific chat.
- **Method:** `GET`
- **Query Parameters:**
  - `chatId` (string): The ID of the chat.
  - `limit` (integer): Number of messages to fetch (optional).
- **Response:**
  ```json
  [
    {
      "messageId": "string",
      "sender": "string",
      "content": "string",
      "timestamp": "string"
    }
  ]
  ```
- **Error Codes:**
  - `404`: Chat not found
  - `400`: Missing parameters

---

## Create Chat

**Endpoint:** `/chats/create`

- **Description:** Create a new chat room.
- **Method:** `POST`
- **Request Body:**
  ```json
  {
    "name": "string",
    "participants": ["string"]
  }
  ```
- **Response:**
  ```json
  {
    "chatId": "string",
    "name": "string",
    "participants": ["string"]
  }
  ```
- **Error Codes:**
  - `400`: Invalid request body

For additional information, refer to the API Support Page.
