FROM mcr.microsoft.com/devcontainers/python:3-3.14-trixie
# Install
RUN apt-get update && apt-get install -y git vim curl tmux wget
RUN pip install uv
RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then SPEC_ARCH="Linux_arm64"; else SPEC_ARCH="Linux_x86_64"; fi && \
    cd /tmp && \
    curl -LO "https://github.com/specstoryai/getspecstory/releases/latest/download/SpecStoryCLI_${SPEC_ARCH}.tar.gz" && \
    tar -xzf "SpecStoryCLI_${SPEC_ARCH}.tar.gz" && \
    mv specstory /usr/local/bin/ && chmod +x /usr/local/bin/specstory && \
    rm "SpecStoryCLI_${SPEC_ARCH}.tar.gz"
RUN curl -fsSL https://claude.ai/install.sh | sudo -u vscode bash
RUN ARCH=$(uname -m) && \
    BEADS_VERSION="v1.0.2" && \
    if [ "$ARCH" = "aarch64" ]; then LIB_DIR="aarch64-linux-gnu"; else LIB_DIR="x86_64-linux-gnu"; fi && \
    curl -fsSL https://raw.githubusercontent.com/gastownhall/beads/${BEADS_VERSION}/scripts/install.sh | bash && \
    ln -s /usr/lib/${LIB_DIR}/libicui18n.so /usr/lib/${LIB_DIR}/libicui18n.so.74
RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then TEMPORAL_ARCH="arm64"; else TEMPORAL_ARCH="amd64"; fi && \
    cd /tmp && curl -L -o temporal.tar.gz "https://temporal.download/cli/archive/latest?platform=linux&arch=${TEMPORAL_ARCH}" && \
    tar -xzf temporal.tar.gz && mv temporal /usr/local/bin/ && chmod +x /usr/local/bin/temporal && rm /tmp/temporal.tar.gz
#  RUN apt-get update && apt-get install -y --no-install-recommends golang gccgo && \
#     rm -rf /var/lib/apt/lists/* && \
#     git clone https://github.com/gastownhall/beads.git /tmp/beads && \
#     cd /tmp/beads && \
#     make build && \
#     make install && \
#     mv bd /usr/local/bin/ && chmod +x /usr/local/bin/bd && \
#     cd / && rm -rf /tmp/beads && \
#     apt-get purge -y --no-install-recommends golang gccgo && \
#     apt-get autoremove -y && apt-get clean && rm -rf /var/lib/apt/lists/*
RUN bash install-gascity.sh   