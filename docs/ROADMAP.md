# SpeakSphere - Product Roadmap

This document outlines the planned development phases for the SpeakSphere proof-of-concept and beyond.

---

### Phase 1: Core Functionality & MVP (Target: Current Quarter)

- **Objective**: Launch a Minimum Viable Product focused on the Customer Inquiry chatbot.
- **Key Deliverables**:
  - `[Epic]` Develop Chat Service MVP with basic intent recognition for common questions.
  - `[Epic]` Implement support for **English** language only.
  - `[Tech]` Set up core backend infrastructure: API Gateway, Chat Service, and MongoDB for conversations.
  - `[Feature]` Develop a basic web client with a functional chat interface.
  - `[Feature]` Establish a secure login for the (yet to be built) internal dashboard.

---

### Phase 2: Expansion of Core Features (Target: Next Quarter)

- **Objective**: Introduce appointment scheduling and expand language support.
- **Key Deliverables**:
  - `[Epic]` Develop the Appointment Scheduling service.
  - `[Feature]` Integrate with **Google Calendar API** for checking availability and booking.
  - `[Epic]` Implement multilingual support for the Chat Service, adding **Spanish** and **Hindi**.
  - `[Epic]` Develop the initial Inventory Management dashboard with **read-only** access to stock levels.
  - `[Tech]` Implement user authentication and roles for the dashboard.

---

### Phase 3: Enhancement & Scaling (Target: Quarter After Next)

- **Objective**: Achieve feature parity across all modules and prepare for broader adoption.
- **Key Deliverables**:
  - `[Feature]` Add remaining languages: **Tamil** and **French**.
  - `[Feature]` Implement full **CRUD (Create, Read, Update, Delete)** functionality for Inventory Management.
  - `[Feature]` Add automated email/SMS reminders for the Appointment Service via Twilio/SendGrid.
  - `[Tech]` Begin HIPAA compliance hardening for potential healthcare use-cases.
  - `[Feature]` Implement the user feedback mechanism for the chatbot and a pipeline to use it for model improvement.

---
