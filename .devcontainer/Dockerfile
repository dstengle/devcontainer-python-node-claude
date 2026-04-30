FROM mcr.microsoft.com/devcontainers/python:3-3.14-trixie
# Install
RUN apt-get update && apt-get install -y git vim curl tmux wget golang
RUN pip install uv
#
# Specstory for capturing agent chat logs
#
RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then SPEC_ARCH="Linux_arm64"; else SPEC_ARCH="Linux_x86_64"; fi && \
    cd /tmp && \
    curl -LO "https://github.com/specstoryai/getspecstory/releases/latest/download/SpecStoryCLI_${SPEC_ARCH}.tar.gz" && \
    tar -xzf "SpecStoryCLI_${SPEC_ARCH}.tar.gz" && \
    mv specstory /usr/local/bin/ && chmod +x /usr/local/bin/specstory && \
    rm "SpecStoryCLI_${SPEC_ARCH}.tar.gz"
#
# Claude code
#
RUN curl -fsSL https://claude.ai/install.sh | sudo -u vscode bash

#
# Beads install prereq for gascity
#
RUN ARCH=$(uname -m) && \
    BEADS_VERSION="v1.0.0" && \
    if [ "$ARCH" = "aarch64" ]; then LIB_DIR="aarch64-linux-gnu"; else LIB_DIR="x86_64-linux-gnu"; fi && \
    curl -fsSL https://raw.githubusercontent.com/gastownhall/beads/${BEADS_VERSION}/scripts/install.sh | bash && \
    ln -s /usr/lib/${LIB_DIR}/libicui18n.so /usr/lib/${LIB_DIR}/libicui18n.so.74

#
# dolt install for gascity
#
RUN curl -fsSL https://github.com/dolthub/dolt/releases/latest/download/install.sh | bash


#
# Gas City
#
# COPY install-gascity.sh /tmp/install-gascity.sh
# RUN chmod +x /tmp/install-gascity.sh && VERSION=1.0.0 /tmp/install-gascity.sh && rm /tmp/install-gascity.sh

# Install personal build of gascity temporarily
RUN curl -fsSL https://raw.githubusercontent.com/dstengle/gascity/personal-config/scripts/install.sh | sh
