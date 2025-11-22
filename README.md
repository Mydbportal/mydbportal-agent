# MyDbPortal Agent.

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)

A lightweight system monitoring agent designed to run on your server, collect vital database stats and help in database installation .

## Overview

This project provides a complete solution for provisioning, monitoring, and cleaning up a server with a standard database stack (MySQL, PostgreSQL, MongoDB). It consists of two main parts:

1.  **The Agent:** A secure, lightweight server that exposes a single API endpoint to report system health.
2.  **Setup & Cleanup Scripts:** Powerful shell scripts that automate the entire server lifecycle, from initial setup to complete teardown.

## Features

- **System Monitoring:** Reports CPU usage, memory usage, and the status of key services.
- **Automated Setup:** A single script to install and configure MySQL, PostgreSQL, and MongoDB.
- **Secure by Default:** Generates strong, random passwords for all databases and protects the agent's API with a token.
- **Centralized Management:** Sends credentials and server information to a central API endpoint for easy management.
- **Clean Uninstallation:** A dedicated script to safely and completely remove all installed components.

## How It Works

1.  **Setup:** You run the `init.sh` script on a fresh server. It installs the databases, configures them for remote access, and starts the monitoring agent as a system service.
2.  **Monitoring:** The agent runs in the background, ready to receive secure requests from the MyDbPortal platform. When requested, it gathers real-time system stats and sends them back.
3.  **Cleanup:** If you decommission the server, you run the `cleanup_database_server.sh` script to wipe all related software and configurations, leaving the system clean.

## Getting Started

### Prerequisites

- A server running a Debian-based OS (e.g., Ubuntu 20.04 or later).
- `root` or `sudo` access.

### Installation

To set up your server, run the following command:

```bash
curl -sL https://raw.githubusercontent.com/bonheur15/mydbportal-agent/main/init.sh | bash
```

This will download and execute the setup script, which handles the entire installation process automatically.

## Usage

### The Agent API

The agent exposes a single endpoint to fetch system statistics.

- **Endpoint:** `GET /stats`
- **Port:** `7723` (or as configured by the `AGENT_PORT` environment variable)
- **Authentication:** Requires a bearer token in the `agent_token` header.

**Example Request:**

```bash
curl -X GET http://<your-server-ip>:7723/stats \
     -H "Content-Type: application/json" \
     -H "agent_token: your-secret-agent-token"
```

### Server Cleanup

To completely remove the agent and all database services from your server, run the cleanup script:

```bash
curl -sL https://raw.githubusercontent.com/bonheur15/mydbportal-agent/main/cleanup_database_server.sh | bash
```

**Warning:** This is a destructive operation and will permanently delete all data.

## Configuration

The agent is configured using environment variables, which are set automatically by the `init.sh` script in the `database-agent.service` file.

- `AGENT_PORT`: The port for the agent to listen on. Defaults to `7723`.
- `AGENT_TOKEN`: The secret token for authenticating API requests. Defaults to `your-secret-agent-token`.

## For Developers

### Local Development

To run the agent locally for development:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/bonheur15/mydbportal-agent.git
    cd mydbportal-agent
    ```

2.  **Install dependencies:**
    ```bash
    bun install
    ```

3.  **Run the development server:**
    ```bash
    bun run dev
    ```

The server will start with hot-reloading on `http://localhost:7723`.

### Build

To compile the agent into a standalone executable:

```bash
bun run build
```

The compiled binary will be located in `out/linux-x64`.

## Contributing

Contributions are welcome! If you have a feature request or find a bug, please open an issue on the [Contributing Guide](CONTRIBUTING.md).

## License

This project is licensed under the [MIT License](LICENSE).
