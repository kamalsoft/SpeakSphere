# SpeakSphere - Application Settings

This document outlines the configurable settings for the SpeakSphere application. These settings allow administrators to customize the application's behavior, manage integrations, and enable/disable features.

## 1. Feature Flags

Feature flags allow for toggling major components of the application on or off without deploying new code. These are typically managed via environment variables or a configuration service.

- `ENABLE_CUSTOMER_INQUIRIES`: (Default: `true`) Enables the customer-facing chatbot.
- `ENABLE_APPOINTMENT_SCHEDULING`: (Default: `true`) Enables the appointment scheduling functionality within the chatbot.
- `ENABLE_INVENTORY_MANAGEMENT`: (Default: `true`) Enables the internal inventory management dashboard.
- `ENABLE_HIPAA_COMPLIANCE_MODE`: (Default: `false`) Enables stricter data handling, logging, and access controls required for HIPAA. This should only be enabled in environments handling Protected Health Information (PHI).

## 2. Language Support

The application is designed to be multilingual. The list of supported languages can be configured.

- `SUPPORTED_LANGUAGES`: (Default: `en,es,hi,ta,fr`) A comma-separated list of language codes (ISO 639-1) that the chatbot will support.

## 3. Third-Party Integrations (API Keys)

These settings are essential for connecting SpeakSphere to external services. API keys and secrets must be stored securely as environment variables or in a secrets management tool.

- `GOOGLE_CALENDAR_API_KEY`: Required for the Appointment Scheduling service to interact with Google Calendar.
- `SENDGRID_API_KEY`: Required for sending email notifications (e.g., appointment reminders).
- `TWILIO_ACCOUNT_SID` & `TWILIO_AUTH_TOKEN`: Required for sending SMS notifications.

## 4. Inventory Management Settings

Specific settings for the Inventory Management module.

- `INVENTORY_LOW_STOCK_THRESHOLD`: (Default: `10`) The stock quantity at which a "low stock" alert is triggered for a product.

---
