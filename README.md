# o3s - VS Code extension

VS Code extension for [o3s](https://github.com/Hansehart/o3s) — generates the project's `devcontainer.json` from inside VS Code instead of hand-editing a static file.

## Why

o3s mounts its repo root read-only into the running dev container, so `devcontainer.json` can't be edited once you're inside it — and being tracked in git meant every local tweak showed up as a diff. This extension generates it instead: pick the features you want, and it writes the file for you, before the container even exists.

## What it does

- Adds an **o3s** view to the Activity Bar.
- If no o3s project is open, offers a **Clone o3s** button that clones the repo via VS Code's built-in Git support.
- If an o3s project is open, lists the available devcontainer features (from `.devcontainer/templates/features.json`), pre-selecting whatever's already active in the current `devcontainer.json`.
- **Generate** merges your selection into the project's skeleton (`.devcontainer/templates/devcontainer.json`) and writes `.devcontainer/devcontainer.json`.

## Requirements

- The [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension.
- Works only inside the [o3s](https://github.com/Hansehart/o3s) repository (detected via a `.o3s` marker file) — it's a no-op in any other project.

## Usage

1. Open VS Code with no o3s project open, or open the o3s repo directly.
2. Click the o3s icon in the Activity Bar.
3. No project open yet? Click **Clone o3s**.
4. Project open? Pick the features you want and click **Generate**.
5. Run **Dev Containers: Rebuild and Reopen in Container** to apply it.

## Development

```bash
npm install
npm run compile   # or: npm run watch
```

Package a local build:

```bash
npx vsce package
```

Then install it via **Extensions: Install from VSIX...** in VS Code.
