# Autarky

**Autarky** is a command line tool that helps reclaim disk space by removing `node_modules` folders that haven't been touched in a while. It crawls the current directory, shows you outdated directories and deletes the ones you confirm.

This repository contains an experimental implementation written in TypeScript using [Ink](https://github.com/vadimdemedes/ink) to render a React based terminal UI. State is managed with Redux and intensive file operations run inside child processes so the interface stays responsive.

## Usage

1. Install dependencies and build the CLI:

```bash
npm install --ignore-scripts --legacy-peer-deps
npm run build
```

2. Run the CLI from the repository root:

```bash
node build/index.js
```

Answer the prompts to select which `node_modules` folders you want to remove.

## Highlight: Interactive CLI

The most interesting part of the project is how a familiar React component tree is used to create an interactive terminal experience. Components dispatch Redux actions and receive state updates just like a web app, while child processes handle disk indexing and deletion without blocking input. See [`Interrogator/Questions.tsx`](src/ui/containers/Interrogator/Questions.tsx) for the flow of questions and background work.

## Development

Tests are written with Jest and can be run with:

```bash
npm test
```

Additional notes about the architecture and data flow can be found in [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## License

MIT
