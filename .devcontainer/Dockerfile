# OpenClaw Development Container
# Based on the official OpenClaw image
FROM ghcr.io/openclaw/openclaw:latest

LABEL maintainer="openclaw-workspace"

USER root

# Avoid prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install dev tools not included in the official image
RUN apt-get update && apt-get install -y --no-install-recommends \
    sudo \
    zsh \
    vim \
    jq \
    build-essential \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Docker CLI (for sandbox support)
RUN install -m 0755 -d /etc/apt/keyrings \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg \
    && chmod a+r /etc/apt/keyrings/docker.gpg \
    && printf 'deb [arch=%s signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable\n' \
       "$(dpkg --print-architecture)" > /etc/apt/sources.list.d/docker.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends docker-ce-cli docker-compose-plugin \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create non-root user with sudo access
ARG USERNAME=node
RUN echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Set up workspace directory
RUN mkdir -p /home/$USERNAME/.openclaw/workspace \
    && chown -R $USERNAME:$USERNAME /home/$USERNAME

USER $USERNAME
WORKDIR /workspace

ENV DEBIAN_FRONTEND=dialog
