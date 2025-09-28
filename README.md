# Devcontainer Classroom Web

A [Dev Container](https://containers.dev/) configuration for web development
classroom environments. This setup provides a consistent development environment
with pre-configured tools for web development, specifically designed for
educational use.

**Features:**

- Based on Debian Bookworm
- Optimized for web development education
- Pre-configured VS Code settings for classroom use

## Included Tools & Languages

This development container includes the following pre-installed tools and
languages optimized for web development education:

### Languages & Runtimes

- **Go** - Latest version with proper formatting and linting
- **Node.js** - LTS version with pnpm and nvm for package management
- **Deno** - Modern TypeScript/JavaScript runtime

### Development Tools

- **Git** - Configured with classroom-optimized settings for smooth workflows
- **VS Code Extensions**:
  - GitHub Markdown Preview
  - Deno support
  - Live Server for web development
  - Lorem Ipsum generator

### Classroom-Optimized Configuration

- AI features (Copilot) disabled by default
- Automatic git stashing and rebasing for smooth starter repo updates
- Smart commit and sync workflows
- Consistent formatting and linting rules
- Hidden configuration folders for cleaner student experience

## Getting Started

### Prerequisites

- [Docker](https://www.docker.com/get-started) installed on your system
- [VS Code](https://code.visualstudio.com/) with the
  [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

### Using This Dev Container

1. **Clone or use as template**: Clone this repository or use it as a GitHub
   template for your classroom project

2. **Open in VS Code**: Open the project folder in VS Code

3. **Reopen in Container**: When prompted, click "Reopen in Container" or use
   the command palette (`Ctrl+Shift+P` / `Cmd+Shift+P`) and select "Dev
   Containers: Reopen in Container"

4. **Wait for setup**: The container will build automatically (first time may
   take a few minutes)

### For Instructors

This configuration is designed to provide students with a consistent development
environment. Key benefits:

- No need for students to install development tools locally
- Consistent environment across different operating systems
- Pre-configured git workflows for classroom assignments
- Disabled AI assistance to encourage learning fundamentals

### Customization

You can modify the development container by editing files in the `.devcontainer`
folder:

- `devcontainer.json` - Main configuration file
- `Dockerfile` - Custom container setup
- `devcontainer-lock.json` - Locked feature versions (managed automatically)

## Version Management

Feature versions in `devcontainer.json` are locked by `devcontainer-lock.json`
to ensure consistency across environments.

To manage feature versions, install the devcontainer CLI:

```bash
npm install -g @devcontainers/cli
```

To check for potential upgrades to the latest feature versions:

```bash
devcontainer outdated --workspace-folder .
```

To upgrade to the latest feature versions:

```bash
devcontainer upgrade --workspace-folder .
```

## Contributing

When contributing to this classroom environment:

1. Test changes thoroughly in a development container
2. Update documentation as needed
3. Consider the impact on student experience
4. Ensure consistency across different platforms
