# openclaw-workspace

## Development Setup (Dev Container)

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (macOS/Windows) or [Docker Engine](https://docs.docker.com/engine/install/) (Linux) installed and running
- [VS Code](https://code.visualstudio.com/) with the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension

### Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/openclaw/openclaw-workspace.git
   cd openclaw-workspace
   ```
2. Open the folder in VS Code
3. Click the `><` icon in the bottom-left corner and select **Reopen in Container** (or open the Command Palette with `Ctrl+Shift+P` / `Cmd+Shift+P` → "Dev Containers: Reopen in Container")
4. Wait for the container to build (first time takes a few minutes)
5. VS Code will reconnect inside the container with all tools pre-configured

### First-Time Setup

Run the onboarding wizard inside the devcontainer terminal. This configures credentials, channels, and gateway settings:

```bash
openclaw onboard
```

### Starting the Gateway

1. Start the gateway:
   ```bash
   openclaw gateway --port 18789
   ```
2. Open a second terminal and get the dashboard URL with your auth token:
   ```bash
   openclaw dashboard
   ```
3. Open the URL in your browser — VS Code automatically forwards port 18789 to localhost:
   ```
   http://localhost:18789/#token=<your-token>
   ```

### Verifying the Setup

```bash
# Check gateway health
openclaw health

# Full status overview
openclaw status

# Diagnose issues
openclaw doctor
```

### What's Included

The devcontainer uses the [official OpenClaw image](https://github.com/openclaw/openclaw/pkgs/container/openclaw) (`ghcr.io/openclaw/openclaw:latest`) with additional dev tools:

- **OpenClaw CLI** — pre-installed with all dependencies (Node.js 22, Bun, pnpm)
- **Docker CLI** — for sandbox support
- **GitHub CLI** — for PR and issue workflows
- Dev tools: git, zsh, vim, jq, build-essential

### Ports

| Port  | Description            |
|-------|------------------------|
| 18789 | OpenClaw Gateway       |
| 1455  | OpenClaw Auth Callback |

### Alternative: Docker Compose

You can also run the dev environment without VS Code:

```bash
docker compose -f .devcontainer/docker-compose.yml up -d
docker compose -f .devcontainer/docker-compose.yml exec devcontainer zsh
```

### References

- [OpenClaw Docker Docs](https://docs.openclaw.ai/install/docker)
- [OpenClaw CLI Reference](https://docs.openclaw.ai/cli)
- [OpenClaw Troubleshooting](https://docs.openclaw.ai/troubleshooting)
