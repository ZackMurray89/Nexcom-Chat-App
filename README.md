# Nexcom Chat App

A full‑stack chat application built with **Next.js**, **Express.js (WebSocket server)**, and a modern TypeScript monorepo powered by [Turborepo](https://turbo.build/).

---

## 🚀 Tech Stack

- **Frameworks & Runtime**
  - [Next.js](https://nextjs.org/) (frontend)
  - [Express.js](https://expressjs.com/) (backend, WebSockets)
  - [TypeScript](https://www.typescriptlang.org/)

- **Styling & UI**
  - [TailwindCSS](https://tailwindcss.com/)
  - [shadcn/ui](https://ui.shadcn.com/)

- **Database**
  - [Postgres v17](https://www.postgresql.org/) via Docker (local dev)
  - [Neon DB](https://neon.tech/) (production)
  - [Drizzle ORM](https://orm.drizzle.team/)

- **Auth & Validation**
  - [Clerk](https://clerk.dev/) (authentication)
  - [Zod](https://zod.dev/) (schema validation)
  - [@t3-oss/env](https://github.com/t3-oss/env) (typed env validation)

- **Tooling**
  - [Turborepo](https://turbo.build/) (monorepo build system)
  - [pnpm](https://pnpm.io/) (workspaces, package manager)
  - [ESLint (flat config)](https://eslint.org/docs/latest/use/configure/configuration-files-new)
  - [Prettier](https://prettier.io/)
  - [Docker Compose](https://docs.docker.com/compose/) (for local Postgres)

---

## 📂 Monorepo Structure

```bash
apps/
  web/        # Next.js frontend
  server/     # Express WebSocket backend

packages/
  config/     # Shared ESLint, Prettier, TS configs
  db/         # Drizzle schemas + migrations
  ui/         # Shared UI (shadcn components)

.env          # Local env vars (not committed)
.env.example  # Example env file (safe to commit)
docker-compose.yml
pnpm-workspace.yaml
turbo.json
tsconfig.json   # Solution project
```

---

## 🛠️ Getting Started

### 1. Clone & Install

```bash
git clone <this-repo>
cd nexcom-chat-app
pnpm install
```

### 2. Set Up Environment

Copy the example env file:

```bash
cp .env.example .env
```

App‑specific local envs go in:

- `apps/web/.env.local`
- `apps/server/.env.local`

These will be type‑safe loaded by `@t3-oss/env`.

### 3. Start Postgres (Docker)

```bash
docker compose up -d
```

### 4. Run Dev Servers

Run everything in parallel:

```bash
pnpm dev
```

Or run a single app:

```bash
pnpm run dev:web
pnpm run dev:server
```

---

## ⚙️ Useful Scripts

- **`pnpm dev`** → Run all apps in parallel (Next.js + server)
- **`pnpm dev:web`** → Run frontend only
- **`pnpm dev:server`** → Run backend only
- **`pnpm build`** → Build all apps/packages
- **`pnpm typecheck`** → TypeScript project references check
- **`pnpm lint`** → Lint all packages
- **`pnpm format`** → Format codebase with Prettier
- **`pnpm format:check`** → Check formatting
- **`pnpm test`** → Run all tests
- **`pnpm clean`** → Clean builds & node_modules

---

## 🧰 Development Notes

- **Node version**: `22.19.0` (`.nvmrc` provided)
- **Package Manager**: `pnpm` (`packageManager` field pinned in package.json)
- **Database**: Local Postgres runs via Docker (configurable in `.env`)

---

## 📜 License

This project is licensed under the [MIT License](./LICENSE).
