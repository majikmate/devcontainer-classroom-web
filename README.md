# Devcontainer Classroom Web

A [Dev Container](https://containers.dev/) image for web development in the
classroom. It gives every student the same, pre-configured development
environment.

Published image: `ghcr.io/majikmate/devcontainer-classroom-web` (linux/amd64
and linux/arm64)

- Built on [`devcontainer-base`](https://github.com/majikmate/devcontainer-base)
  (`ghcr.io/majikmate/devcontainer-base:2`, Debian 13 "trixie")
- Rebuilt and released automatically when the base image or one of its tools
  gets a new version
- AI features (Copilot, chat, agents) are turned off

## Use it in an assignment repository

Add `.devcontainer/devcontainer.json` to the assignment (template) repository:

```jsonc
{
  "name": "Classroom",
  "image": "ghcr.io/majikmate/devcontainer-classroom-web:2",
}
```

- `:2` receives all compatible updates (new tool versions, security updates).
- `:latest` is the same as `:2` today, but moves to a future major version.
- `:1` is the old Debian 12 "bookworm" image and gets no more updates.

New Codespaces use the current image. With a local Docker installation, the
image stays cached. To get the newest version, run
`docker pull ghcr.io/majikmate/devcontainer-classroom-web:2` and then **Dev
Containers: Rebuild Container**.

## Included tools

All runtimes and tools come from the base image:

- **Node.js** — newest LTS release, with npm and pnpm
- **Deno** — newest LTS release, the JavaScript/TypeScript runtime and language
  server in VS Code
- **Go** — newest release
- **Prettier** — the only formatter (see below)
- **Git** — configured for simple workflows (auto fetch, rebase on sync)

The exact versions of each release are listed in its
[release notes](https://github.com/majikmate/devcontainer-classroom-web/releases).

### Formatting

Files are formatted with Prettier when they are saved, with the **standard
Prettier style** and 2-space indentation. **Tailwind CSS classes are sorted**
into the standard order (in `class`, `className` and `@apply`) — also without a
Tailwind CSS installation in the project. The same formatting is available in
the terminal:

```bash
prettier --write .
```

A project with its own Prettier configuration file uses that file instead.

### VS Code extensions

In addition to the extensions of the base image (Go, Deno, Prettier, Markdown
preview, PlantUML, PDF viewer):

- [Live Preview](https://marketplace.visualstudio.com/items?itemName=ms-vscode.live-server)
  — preview in the external browser
- [Lorem Ipsum](https://marketplace.visualstudio.com/items?itemName=tyriar.lorem-ipsum)
  — placeholder text
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
  — autocomplete for Tailwind CSS classes
- [ES7+ React/Redux/React-Native Snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
  — snippets for React

The GitHub Pull Requests extension is removed.

### Classroom settings

- **AI features are turned off** with `chat.disableAIFeatures`. This is the
  only complete switch: it hides all AI and chat UI and disables the Copilot
  extension, which is built into VS Code. Additional settings turn off agents,
  inline suggestions and next edit suggestions.

  > Note for students: VS Code also turns off Copilot in your own (local) VS
  > Code after you have used the classroom container. To use Copilot again
  > outside the classroom, open your user settings and set
  > `chat.disableAIFeatures` to `false`.

- Extension recommendations are turned off.
- The folders `.devcontainer`, `.github` and `.vscode` are hidden.
- The user in the container is `dev`.

## Automatic releases

The workflow [`.github/workflows/release.yml`](.github/workflows/release.yml)
uses the shared workflow of `devcontainer-base` (described in its
[README](https://github.com/majikmate/devcontainer-base#automatic-releases)):

- Every hour it checks whether the inputs of the image changed: the
  `.devcontainer` folder or the digest of the base image. The base image itself
  is rebuilt when a tool gets a new version, so new tool versions reach this
  image within about two hours.
- A push to `main` with changes in `.devcontainer` releases a new version.
- Pull requests are built and tested (both architectures) without publishing.
- A tag `vX.Y.Z` releases exactly this version; the manual run ("Run
  workflow") can force a release.

Each release is built without cache, tested inside the container (Debian
release, versions, Prettier with Tailwind CSS sorting), and gets the tags
`X.Y.Z`, `X.Y`, `X` and `latest` and a GitHub release with the installed
versions.

## Customization

Edit `.devcontainer/devcontainer.json` through a pull request:

- add or remove VS Code extensions in `customizations.vscode.extensions`
- change VS Code settings in `customizations.vscode.settings`

After the merge, the new image is released automatically.

## Contributing

When you change this classroom environment:

1. Test the change in a pull request (the pull request build must pass).
2. Update this documentation.
3. Consider the effect on students.
