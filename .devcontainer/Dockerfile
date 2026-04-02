FROM mcr.microsoft.com/devcontainers/python:3-3.14-trixie
# Install 
RUN apt-get update && apt-get install -y git vim curl tmux wget
RUN pip install uv
RUN cd /tmp && \
curl -LO https://github.com/specstoryai/getspecstory/releases/latest/download/SpecStoryCLI_Linux_x86_64.tar.gz && \
tar -xzf SpecStoryCLI_Linux_x86_64.tar.gz && \
mv specstory /usr/local/bin/ && chmod +x /usr/local/bin/specstory
RUN curl -fsSL https://claude.ai/install.sh | sudo -u vscode bash
RUN curl -fsSL https://raw.githubusercontent.com/steveyegge/beads/main/scripts/install.sh | bash && ln -s /usr/lib/x86_64-linux-gnu/libicui18n.so /usr/lib/x86_64-linux-gnu/libicui18n.so.74