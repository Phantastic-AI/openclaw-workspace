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

### What's Included

- **Node.js 22** (Debian Bookworm) — matches OpenClaw's runtime
- **Bun** and **pnpm** — OpenClaw's build tools
- **Docker CLI** — for sandbox support
- **GitHub CLI** — for PR and issue workflows
- Common dev tools: git, zsh, vim, jq, build-essential

### Ports

| Port  | Description              |
|-------|--------------------------|
| 18789 | OpenClaw Gateway         |
| 1455  | OpenClaw Auth Callback   |

### Alternative: Docker Compose

You can also run the dev environment without VS Code:

```bash
docker compose -f .devcontainer/docker-compose.yml up -d
docker compose -f .devcontainer/docker-compose.yml exec devcontainer zsh
```
