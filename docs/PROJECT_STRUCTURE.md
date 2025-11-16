# SpeakSphere - Project Structure

This document outlines the directory structure of the SpeakSphere repository.

```
speaksphere/
├── client/               # Frontend application (React/Vue)
│   ├── public/
│   └── src/
├── server/               # Backend services (Python/Django)
│   ├── speaksphere/
│   ├── chat/             # Chat service application
│   ├── appointments/     # Appointment service application
│   ├── inventory/        # Inventory service application
│   └── manage.py
├── docs/                 # All project documentation (This is a suggestion for future organization)
├── .gitmcp.json          # Project metadata and configuration
├── .gitmcp.yml           # CI/CD pipeline and deployment configuration
├── ARCHITECTURE.md       # High-level system architecture
├── API_DOCS.md           # API specifications for services
├── CONTRIBUTING.md       # Guidelines for contributors
├── FEATURES.md           # Detailed feature specifications
├── README.md             # Main project readme
└── ... and other documentation files
```

- **`/client`**: Contains the frontend Single Page Application (SPA). All UI components, styles, and client-side logic reside here.
- **`/server`**: Contains the backend services. Following a Django-like structure, each core functionality (chat, appointments, inventory) is organized into its own "app".
- **`/docs`**: A suggested directory to centralize all Markdown-based documentation for better organization as the project grows.
- **Root Directory**: Contains top-level configuration files and primary documentation that provides an entry point to the project.
