# LeasePilot AI 🧾🤖
**AI Lease Abstraction SaaS** — Upload commercial lease PDFs, extract structured terms, review with your team, and export to Excel/CSV. Built for multi-tenant security (RLS), auditability, and billing.

## Why this exists
Lease abstraction is manual, slow, and error-prone. LeasePilot AI turns unstructured leases into structured, reviewable data with a clean workflow:
1) Upload lease → 2) Automated extraction → 3) Human review → 4) Export + audit trail

---

## Tech Stack (Elite, practical)
### Frontend (v0-ready)
- **Next.js (App Router) + TypeScript**
- **shadcn/ui** (v0 generates compatible UI)
- **Server Actions / Route Handlers**

### Data/Auth/Storage
- **Supabase**: Postgres + Auth + Storage + Realtime
- **Row Level Security (RLS)** for true multi-tenant isolation

### Payments
- **Stripe**: Checkout + Customer Portal + Webhooks
- Entitlements stored in Postgres (org-level plans)

### AI Worker
- **FastAPI** worker service for document processing:
  - PDF text extraction + chunking
  - term extraction (LLM / rules)
  - optional embeddings (pgvector)

### Jobs
- Async job dispatch via a webhook/queue pattern (Trigger.dev or QStash-ready)

---

## Core Features
- ✅ Team workspaces (orgs + roles)
- ✅ Secure lease PDF uploads (Supabase Storage)
- ✅ Document processing pipeline (async)
- ✅ Extracted terms + confidence + review workflow
- ✅ Stripe billing (subscription plans + webhooks)
- ✅ Audit logs (who changed what, when)
- ✅ Exports (CSV / XLSX)

---

## Architecture (high-level)
**Next.js** handles UI + API routes (Stripe webhooks, document creation).  
**Supabase** stores users/orgs/docs/terms and enforces access with **RLS**.  
**FastAPI Worker** fetches uploads from Storage, processes documents, and writes results back to Postgres.

---

## Local Development
### Prereqs
- Node 20+
- pnpm
- Python 3.11+
- Docker (optional but recommended)
- Supabase project (local or hosted)

### 1) Install
```bash
pnpm install
