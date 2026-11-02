# AGENTS.md

## Project Overview

Full Podman Desktop extension template with separate backend, frontend, and
shared packages. This template demonstrates a production-style setup for RPC
communication between a Svelte webview and extension backend.

- **Tech stack**: TypeScript, Node.js 24, Svelte 5, Tailwind CSS, pnpm workspaces, Vite
- **Packages**: `packages/backend`, `packages/frontend`, `packages/shared`
- **Extension API**: `@podman-desktop/api`

## Quick Start

```sh
nvm use
corepack enable
pnpm install --frozen-lockfile
pnpm build
```

## Essential Commands

```sh
pnpm build          # build frontend + backend
pnpm watch          # watch frontend + backend
pnpm lint:check
pnpm lint:fix
pnpm format:check
pnpm format:fix
pnpm typecheck
pnpm test
```

## Single-File Verification

```sh
pnpm exec eslint path/to/file.ts
pnpm exec tsc --noEmit -p packages/backend/tsconfig.json
pnpm exec tsc --noEmit -p packages/frontend/tsconfig.json
pnpm exec tsc --noEmit -p packages/shared/tsconfig.json
pnpm test:backend
pnpm test:frontend
pnpm test:shared
```

## Skills

Task-specific guidance lives in `.agents/skills/`:

- `extension-development` - backend/frontend/shared change flow
- `svelte-ui-design` - Svelte 5 component and state guidance
- `unit-testing` - backend/frontend/shared test strategy

## Architecture

Webview (frontend) <-> shared contract <-> backend extension

- `packages/backend`: extension activation and Podman Desktop API integrations.
- `packages/frontend`: Svelte webview UI.
- `packages/shared`: shared interfaces and RPC/message contracts.

## Pattern References

- New backend API method: update `packages/shared/src/HelloWorldApi.ts` and `packages/backend/src/api-impl.ts`
- New frontend integration: update `packages/frontend/src/api/client.ts` and consuming Svelte component
- New shared model/message: place in `packages/shared/src`
