# SpeakSphere - Chat Service API Documentation

This document provides technical details for interacting with the SpeakSphere Chat Service API. This service powers the customer inquiry chatbot.

## Base URL

All API endpoints are relative to the following base URL, accessed via the API Gateway:

```
/api/v1
```

## Authentication

For most client-side implementations, requests must include a valid API key sent in the `X-API-Key` header.

`X-API-Key: YOUR_API_KEY`

---

## Endpoints

### 1. Submit a Message

This is the primary endpoint for communicating with the chatbot. It accepts a user's message and returns the AI's response.

- **Endpoint**: `POST /chat`
- **Description**: Sends a message to the chatbot as part of a new or existing conversation.

#### Request Body

```json
{
  "conversation_id": "conv_12345abcde",
  "message": "Hello, what are your store hours?",
  "language": "en"
}
```

| Field             | Type   | Required | Description                                                                                             |
| ----------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------- |
| `conversation_id` | string | No       | The ID of the ongoing conversation. If omitted, a new conversation will be started.                     |
| `message`         | string | Yes      | The text content of the user's message.                                                                 |
| `language`        | string | No       | The ISO 639-1 code for the language of the message. If omitted, the API will attempt to auto-detect it. |

#### Success Response (200 OK)

```json
{
  "conversation_id": "conv_12345abcde",
  "response": "Our store is open from 9 AM to 6 PM, Monday to Friday.",
  "intent": "query_store_hours",
  "entities": []
}
```

| Field             | Type   | Description                                                                 |
| ----------------- | ------ | --------------------------------------------------------------------------- |
| `conversation_id` | string | The unique identifier for the conversation session.                         |
| `response`        | string | The chatbot's text response to the user's message.                          |
| `intent`          | string | The classified intent of the user's message (e.g., `schedule_appointment`). |
| `entities`        | array  | An array of objects representing entities extracted from the message.       |

#### Error Responses

- `400 Bad Request`: The request body is missing required fields or is improperly formatted.
  ```json
  {
    "error": "Bad Request",
    "message": "The 'message' field is required."
  }
  ```
- `401 Unauthorized`: The `X-API-Key` header is missing or invalid.
- `500 Internal Server Error`: An unexpected error occurred on the server (e.g., NLP model failure).

---
