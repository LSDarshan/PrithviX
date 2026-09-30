# PrithviX — Evidence-First Land Record & Document Intake Platform

**PrithviX** is an evidence-first document intake, review, and audit platform designed for private land records and property source document processing. Built with high-security object storage, structured data extraction, human-in-the-loop review capabilities, and complete audit trail tracking.

---

## 🏗️ Architecture & Monorepo Structure

This project is organized as a `pnpm` workspace containing applications and shared packages:

```
prithviX/
├── artifacts/
│   ├── api-server/         # Express 5 backend API server (Port 5000)
│   ├── prithvix/           # React + Vite frontend dashboard & document review interface
│   └── mockup-sandbox/     # Isolated sandbox for UI prototyping
├── lib/
│   ├── api-client-react/   # Auto-generated React Query API hooks (via Orval)
│   ├── api-spec/           # OpenAPI 3.1 specification (openapi.yaml)
│   ├── api-zod/            # Auto-generated Zod validation schemas
│   └── db/                 # Drizzle ORM schema & PostgreSQL database layer
├── scripts/                # Build and code generation scripts
├── package.json            # Root workspace configuration
├── pnpm-workspace.yaml     # pnpm workspace definition
└── tsconfig.base.json      # Shared TypeScript base configuration
```

---

## 🛠️ Technology Stack

- **Frontend**: React 18, Vite, Tailwind CSS, Radix UI primitives, Framer Motion, Lucide Icons, Wouter router, TanStack React Query, Clerk Auth.
- **Backend API**: Node.js 24, Express 5, Pino HTTP logging, Object Storage integration.
- **Database**: PostgreSQL with Drizzle ORM.
- **API Spec & Codegen**: OpenAPI 3.1 specs compiled to React Query hooks via Orval and Zod schemas.
- **Monorepo Tooling**: `pnpm` workspaces, TypeScript 5.9, `esbuild`.

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v20 or higher)
- [pnpm](https://pnpm.io/) (`corepack enable` or `npm i -g pnpm`)
- PostgreSQL database instance

### Environment Setup

Create an `.env` file in the root or package directories with required environment variables:

```bash
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/prithvix"

# API Server
PORT=5000
NODE_ENV="development"

# Authentication (Clerk)
CLERK_SECRET_KEY="sk_test_..."
VITE_CLERK_PUBLISHABLE_KEY="pk_test_..."
```

---

## 🚀 How to Start the Application

You can start the backend API server and the frontend application independently from the root directory of the monorepo:

### 1. Start the Backend API Server (Port 5000)

```bash
pnpm --filter @workspace/api-server run dev
# Or on Windows using npx:
npx pnpm --filter @workspace/api-server run dev
```

### 2. Start the Frontend Application (Vite Dev Server)

In a separate terminal window:

```bash
pnpm --filter @workspace/prithvix run dev
# Or on Windows using npx:
npx pnpm --filter @workspace/prithvix run dev
```

### 3. Open in Browser

- **Frontend App**: Open [http://localhost:5173](http://localhost:5173) (or the URL printed in terminal)
- **API Server Health**: Open [http://localhost:5000/api/healthz](http://localhost:5000/api/healthz)

---

## 💻 Available Scripts

Run scripts from the workspace root:

| Command | Description |
|---|---|
| `pnpm --filter @workspace/api-server run dev` | Start the Express API server in dev mode |
| `pnpm --filter @workspace/prithvix run dev` | Start the React frontend dev server |
| `pnpm run build` | Typecheck and build all workspace packages |
| `pnpm run typecheck` | Run TypeScript verification across all packages |
| `pnpm --filter @workspace/api-spec run codegen` | Regenerate API hooks and Zod schemas from `openapi.yaml` |
| `pnpm --filter @workspace/db run push` | Apply Drizzle database migrations |

---

## 🔐 Core Features

1. **Document Intake & Secure Uploads**:
   - Presigned object storage upload URLs (`/api/storage/uploads/request-url`).
   - Secure private file streaming (`/api/storage/objects/*`).

2. **Evidence Audit & Review**:
   - Automated extraction of land record fields.
   - Interactive human verification interface with audit log retention.

3. **Dashboard & Metrics**:
   - Workspace summary metrics and document tracking dashboard.

---

## 📜 License

MIT License.
