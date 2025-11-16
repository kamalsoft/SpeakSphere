# SpeakSphere - Technical Specification

This document provides low-level technical details about the SpeakSphere architecture and data models. It is an extension of the [System Architecture](./ARCHITECTURE.md) document.

## 1. Data Models

### 1.1. PostgreSQL (Relational Data)

**Database**: `speaksphere_main`

**`inventory_products` Table**:

| Column Name          | Data Type      | Constraints                 | Description                        |
| -------------------- | -------------- | --------------------------- | ---------------------------------- |
| `id`                 | `SERIAL`       | `PRIMARY KEY`               | Unique identifier for the product. |
| `sku`                | `VARCHAR(100)` | `UNIQUE`, `NOT NULL`        | Stock Keeping Unit.                |
| `name`               | `VARCHAR(255)` | `NOT NULL`                  | Display name of the product.       |
| `quantity`           | `INTEGER`      | `NOT NULL`, `DEFAULT 0`     | Current stock level.               |
| `warehouse_location` | `VARCHAR(100)` |                             | Location of the stock.             |
| `created_at`         | `TIMESTAMPTZ`  | `NOT NULL`, `DEFAULT NOW()` | Timestamp of record creation.      |
| `updated_at`         | `TIMESTAMPTZ`  | `NOT NULL`, `DEFAULT NOW()` | Timestamp of last update.          |

**`users` Table**: (For internal dashboard access)

| Column Name     | Data Type      | Constraints          | Description                           |
| --------------- | -------------- | -------------------- | ------------------------------------- |
| `id`            | `SERIAL`       | `PRIMARY KEY`        | Unique identifier for the user.       |
| `email`         | `VARCHAR(255)` | `UNIQUE`, `NOT NULL` | User's email for login.               |
| `password_hash` | `VARCHAR(255)` | `NOT NULL`           | Hashed password.                      |
| `role`          | `VARCHAR(50)`  | `NOT NULL`           | User role (e.g., 'admin', 'manager'). |

### 1.2. MongoDB (Conversational Data)

**Database**: `speaksphere_chat`

**`conversations` Collection**:

Each document represents a single conversation thread.

```json
{
  "_id": "conv_12345abcde", // Conversation ID
  "user_id": "user_session_xyz", // Anonymous user identifier
  "created_at": "2025-11-15T10:00:00Z",
  "messages": [
    { "sender": "user", "text": "Hello", "timestamp": "2025-11-15T10:00:05Z" },
    {
      "sender": "bot",
      "text": "Hi! How can I help you?",
      "timestamp": "2025-11-15T10:00:06Z",
      "intent": "greeting"
    }
  ]
}
```

## 2. Service Communication

- **Internal Communication**: Services will communicate with each other via RESTful APIs. For higher performance needs in the future, an event-driven approach using a message broker like RabbitMQ or Kafka could be adopted.
- **Security**: Service-to-service communication within the cluster will be secured using mutual TLS (mTLS) to ensure that only trusted services can talk to each other.
