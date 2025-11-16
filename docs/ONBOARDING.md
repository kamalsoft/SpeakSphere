# Onboarding Guide for New Developers

Welcome to the SpeakSphere team! This guide will walk you through setting up your development environment and introduce you to key project resources.

## 1. Getting Started: Environment Setup

Follow these steps to get the application running on your local machine.

### Prerequisites

- Node.js v18.x or later
- Python 3.10 or later
- Access to a MongoDB and PostgreSQL database

### Installation

1.  **Clone the repository**:

    ```sh
    git clone https://github.com/kamalsoft/SpeakSphere.git
    cd speaksphere
    ```

2.  **Install backend dependencies**:

    ```sh
    # Navigate to the server directory
    cd server
    pip install -r requirements.txt
    ```

3.  **Install frontend dependencies**:

    ```sh
    # Navigate to the client directory
    cd ../client
    npm install
    ```

4.  **Set up environment variables**:
    Create a `.env` file in the `server` directory. You can use `server/.env.example` as a template for the required variables.

### Running the Application

1.  **Start the backend server**:

    ```sh
    # From the server directory
    python manage.py runserver
    ```

2.  **Start the frontend development server**:
    ```sh
    # From the client directory
    npm run dev
    ```

### Testing WebSocket Connections

To test the real-time voice endpoint locally, you can use a command-line tool like `wscat`.

1.  **Install `wscat`**:

    ```sh
    npm install -g wscat
    ```

2.  **Connect to the server**:
    Once the backend server is running, you can connect to the voice service with the following command:
    ```sh
    wscat -c ws://localhost:8000/voice
    ```

## 2. Key Documentation

Once you have the project running, we highly recommend reading the following documents to get a deeper understanding of the project:

- **Project Structure**: Understand how the codebase is organized.
- **System Architecture**: Get a high-level overview of the services and how they interact.
- **Contribution Guidelines**: Learn about our coding standards, branch strategy, and pull request process. This is essential before you start coding.
- **Product Roadmap**: See where the project is headed and what features are planned.
