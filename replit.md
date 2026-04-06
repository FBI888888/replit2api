# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Artifacts

- **API Server** (`artifacts/api-server`) — Express backend serving `/api` and `/v1` routes
  - `/v1/models` — list all available models (requires Bearer token)
  - `/v1/chat/completions` — OpenAI-compatible endpoint; routes to OpenAI or Anthropic by model prefix
  - `/v1/messages` — Anthropic Messages native format; routes to Anthropic or OpenAI by model prefix
  - Full tool call support, streaming (SSE), keepalive, and non-streaming modes
- **API Portal** (`artifacts/api-portal`) — Dark-themed React docs portal at `/` with connection details, endpoints, model list, CherryStudio setup guide, and curl example

## AI Integrations

- **OpenAI** via Replit AI Integrations (`AI_INTEGRATIONS_OPENAI_BASE_URL`, `AI_INTEGRATIONS_OPENAI_API_KEY`)
- **Anthropic** via Replit AI Integrations (`AI_INTEGRATIONS_ANTHROPIC_BASE_URL`, `AI_INTEGRATIONS_ANTHROPIC_API_KEY`)
- **PROXY_API_KEY** secret — Bearer token clients must send to use the proxy

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
