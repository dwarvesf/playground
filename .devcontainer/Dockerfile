# [Choice] Go version (use -bullseye variants on local arm64/Apple Silicon): 1, 1.18, 1.17, 1-bullseye, 1.18-bullseye, 1.17-bullseye, 1-buster, 1.18-buster, 1.17-buster
ARG VARIANT="1.21-bookworm"
FROM mcr.microsoft.com/vscode/devcontainers/go:${VARIANT}

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends

# Download and install Obsidian
ARG OBSIDIAN_VERSION=1.4.16
RUN curl -LO "https://github.com/obsidianmd/obsidian-releases/releases/download/v${OBSIDIAN_VERSION}/obsidian-${OBSIDIAN_VERSION}-arm64.tar.gz"
RUN tar -xvf obsidian-${OBSIDIAN_VERSION}-arm64.tar.gz \
    && cd obsidian-${OBSIDIAN_VERSION}-arm64 \
    && chmod +x obsidian \
    && sudo ln -s $(pwd)/obsidian /usr/bin/obsidian

# [Optional] Uncomment the next lines to use go get to install anything else you need
# USER vscode
# SHELL ["/bin/bash", "-lc"]

# USER root

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1
