# devcontainer-python-node-claude

A reusable development container (devcontainer) with Python 3.12, Node.js, and additional tools pre-installed. This container is built and published to GitHub Container Registry (ghcr.io) for easy reuse across projects.

## Features

This devcontainer includes:

- Python 3.12 (Bullseye)
- Node.js
- Poetry (Python dependency management)
- GitHub CLI
- Docker-outside-of-Docker support
- Pack CLI (Buildpacks)
- SQLite

## How It's Built and Published

This devcontainer is automatically built and published to GitHub Container Registry using GitHub Actions. The workflow:

1. Triggers on pushes to the main branch, tag creation, and pull requests
2. Uses the devcontainer CLI to build the container
3. Publishes the container to GitHub Container Registry (ghcr.io)

## How to Use

### In a GitHub Codespace or VS Code

1. Create a `.devcontainer/devcontainer.json` file in your project with:

```json
{
  "image": "ghcr.io/YOUR-USERNAME/devcontainer-python-node-claude:latest",
  "forwardPorts": [],
  "customizations": {
    "vscode": {
      "extensions": [
        // Add your preferred extensions here
      ]
    }
  }
}
```

Replace `YOUR-USERNAME` with your GitHub username.

### Available Tags

The container is published with several tags for flexible versioning:

- `latest`: The most recent build from the main branch
- `vX.Y.Z`: Specific version (when tagged with a semantic version)
- `vX.Y`: Major.Minor version
- `vX`: Major version only
- `main`: Latest build from the main branch
- `sha-XXXXXXX`: Specific commit SHA

## Development

To modify this devcontainer:

1. Update the `devcontainer.json` file with your desired changes
2. Push to the main branch or create a pull request
3. The GitHub Actions workflow will automatically build and publish the updated container
