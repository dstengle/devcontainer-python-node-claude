FROM mcr.microsoft.com/devcontainers/python:3-3.14-trixie
# Install
RUN apt-get update && apt-get install -y git vim curl tmux wget
RUN pip install uv
RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then SPEC_ARCH="Linux_arm64"; else SPEC_ARCH="Linux_x86_64"; fi && \
    cd /tmp && \
    curl -LO "https://github.com/specstoryai/getspecstory/releases/latest/download/SpecStoryCLI_${SPEC_ARCH}.tar.gz" && \
    tar -xzf "SpecStoryCLI_${SPEC_ARCH}.tar.gz" && \
    mv specstory /usr/local/bin/ && chmod +x /usr/local/bin/specstory
RUN curl -fsSL https://claude.ai/install.sh | sudo -u vscode bash
RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then LIB_DIR="aarch64-linux-gnu"; else LIB_DIR="x86_64-linux-gnu"; fi && \
    curl -fsSL https://raw.githubusercontent.com/steveyegge/beads/main/scripts/install.sh | bash && \
    ln -s /usr/lib/${LIB_DIR}/libicui18n.so /usr/lib/${LIB_DIR}/libicui18n.so.74
RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then TEMPORAL_ARCH="arm64"; else TEMPORAL_ARCH="amd64"; fi && \
    cd /tmp && curl -L -o temporal.tar.gz "https://temporal.download/cli/archive/latest?platform=linux&arch=${TEMPORAL_ARCH}" && \
    tar -xzf temporal.tar.gz && mv temporal /usr/local/bin/ && chmod +x /usr/local/bin/temporal
