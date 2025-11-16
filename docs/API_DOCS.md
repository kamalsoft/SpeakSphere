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

### 2. Initiate Agent Handoff

- **Endpoint**: `POST /handoff`
- **Description**: (Internal Service-to-Service) Initiates a transfer of a live voice call from the AI to a human agent queue. This is typically called by the Chat Service when it detects a handoff intent.

#### Request Body

```json
{
  "conversation_id": "conv_12345abcde",
  "target_queue": "support"
}
```

| Field             | Type   | Required | Description                                                                                |
| ----------------- | ------ | -------- | ------------------------------------------------------------------------------------------ |
| `conversation_id` | string | Yes      | The ID of the active conversation to be transferred.                                       |
| `target_queue`    | string | No       | The specific agent queue to transfer to (e.g., 'sales', 'support'). Defaults to 'general'. |

#### Success Response (202 Accepted)

The server accepts the request and has initiated the handoff process asynchronously.

---

### 3. Submit Feedback

- **Endpoint**: `POST /feedback`
- **Description**: Submits user feedback on a specific chatbot message.

#### Request Body

```json
{
  "conversation_id": "conv_12345abcde",
  "message_id": "msg_67890fghij",
  "rating": 5,
  "comment": "This was very helpful!"
}
```

| Field             | Type    | Required | Description                                                              |
| ----------------- | ------- | -------- | ------------------------------------------------------------------------ |
| `conversation_id` | string  | Yes      | The ID of the conversation containing the message being rated.           |
| `message_id`      | string  | Yes      | The unique identifier for the specific bot message that was rated.       |
| `rating`          | integer | Yes      | The rating given by the user (e.g., 1 for thumbs down, 5 for thumbs up). |
| `comment`         | string  | No       | An optional free-text comment from the user.                             |

#### Success Response (201 Created)

```json
{
  "status": "success",
  "message": "Feedback submitted successfully."
}
```

#### Error Responses

- `400 Bad Request`: The request body is missing required fields or is improperly formatted.

## WebSocket Endpoints

For real-time, bidirectional communication like voice inquiries, the API provides a WebSocket endpoint.

### 1. Voice Inquiry Stream

- **Endpoint**: `WS /voice`
- **Description**: Establishes a persistent connection for streaming audio from the client to the server and receiving audio responses back.

#### Communication Flow

1.  **Client Connects**: The client establishes a WebSocket connection to the `/voice` endpoint.
2.  **Client Sends Audio**: The client streams raw audio data (e.g., PCM audio chunks) in binary frames.
3.  **Server Responds**: The server can send back multiple message types:
    - **Interim Transcript**: (Optional) A preliminary text transcript of the user's speech as it is being processed.
      ```json
      { "type": "interim_transcript", "text": "Hello what are your..." }
      ```
    - **Final Transcript**: The final, corrected text transcript after the user has finished speaking.
      ```json
      {
        "type": "final_transcript",
        "text": "Hello, what are your store hours?"
      }
      ```
    - **Audio Response**: A binary frame containing the audio data (e.g., MP3 or WAV) of the chatbot's spoken response. The client is responsible for playing this audio.
