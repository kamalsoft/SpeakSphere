# SpeakSphere - Feature Specification

This document provides a breakdown of features as planned in the [Product Roadmap](./ROADMAP.md).

---

### Phase 1: Core Functionality & MVP

The initial launch focuses on establishing the core chatbot functionality.

- **Customer Inquiry Chatbot (MVP)**: A web-based chat interface capable of handling basic user questions.
  - **Intent Recognition**: Understands 5-10 common user intents.
  - **Language Support**: Supports **English** only.
- **Secure Admin Login**: A secure login mechanism for a future internal dashboard.

---

### Phase 2: Expansion of Core Features

This phase introduces appointment scheduling and expands the application's reach.

- **Appointment Scheduling**: Users can book appointments through the chatbot.
  - **Calendar Integration**: Integrates with **Google Calendar** to check for availability and create new events.
- **Inventory Management Dashboard (Read-Only)**: A secure dashboard for internal users to view product stock levels.
  - **User Authentication**: Implements roles and permissions for dashboard access.
- **Expanded Language Support**: The chatbot will add support for **Spanish** and **Hindi**.

---

### Phase 3: Enhancement & Scaling

This phase focuses on achieving feature parity and preparing for more advanced use cases.

- **Full Inventory Management**: The dashboard will be updated to support full **CRUD (Create, Read, Update, Delete)** operations for inventory.
- **Automated Appointment Reminders**: The system will send automated email or SMS reminders for upcoming appointments using services like SendGrid or Twilio.
- **Chatbot Feedback Loop**: Users will be able to rate chatbot responses, providing data for future model improvements.
- **Full Language Support**: The remaining target languages, **Tamil** and **French**, will be added.
- **HIPAA Compliance Hardening**: The system will undergo hardening to meet security and privacy standards for potential healthcare applications.

---

### Phase 4: Next-Generation Interaction

This phase will introduce new ways for users to interact with the platform.

- **Voice Inquiries**: Users will be able to speak to the chatbot for a hands-free experience, which includes integrating Speech-to-Text (STT) and Text-to-Speech (TTS) services.
- **Live Agent Escalation**: The voice service will support transferring the user to a human agent upon request or when the AI cannot handle a query.
