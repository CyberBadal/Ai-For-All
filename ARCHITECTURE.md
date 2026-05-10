# AI Spend Audit | Systems Architecture (Vite + Express Edition)

## 1. Executive Summary
AI Spend Audit is a high-performance SaaS platform designed to identify inefficiencies in startup AI stacks. This document outlines the decoupled architecture using **React 19** and **Node.js 24**, ensuring a production-ready, scalable infrastructure with strict type safety and deterministic logic.

## 2. Technical Stack & Rationale

### Frontend (The UI Layer)
*   **React 19 + Vite:** Utilizing the latest React features for improved rendering and Vite for near-instant HMR (Hot Module Replacement).
*   **Wouter:** Chosen for its tiny footprint and simplicity in client-side routing, avoiding the overhead of heavier routers for a single-purpose SaaS tool.
*   **Zustand + Persistence:** Manages multi-step form state. Syncs with `localStorage` so users don't lose data on accidental refreshes.
*   **Recharts:** Implemented on the `/results` page to provide visual weight to the financial waste/savings data.
*   **React Query:** Manages the lifecycle of the audit submission and fetching shareable reports from the Express API.

### Backend (The Logic Layer)
*   **Node.js 24 + Express 5:** Leveraging the latest Node runtime and Express 5's improved error handling and native Promise support.
*   **Deterministic Audit Engine:** A proprietary logic module that processes tool costs against a centralized `PRICING_DATA.md` registry.
*   **Pino:** Structured JSON logging for production observability and debugging.
*   **PostgreSQL:** Relational storage for audit history, lead generation, and shareable public links.

## 3. Core Product Workflows

### A. The "Stateless" Audit Flow
1.  User enters data into the `React Hook Form` (validated via `Zod`).
2.  Zustand captures every keystroke to ensure persistence.
3.  On submission, the data is sent to the `/api/v1/audit` endpoint.
4.  The Express server runs the deterministic engine + calls the AI summary service.
5.  Results are returned and stored in PostgreSQL; a unique `share_id` is generated.

### B. Lead Generation & Value-Capture
The email gate is strictly "Post-Value." The UI shows the savings *first*. Once the user sees potential savings (especially if >$500/mo), the app triggers an invitation to save the report via email, which updates the record in PostgreSQL.

## 4. System Components

### The Audit Engine (`backend/src/engine/`)
The engine is decoupled from the Express routes. It follows a **Registry-Logic-Output** pattern:
1.  **Registry:** Current pricing for OpenAI, Claude, Cursor, etc.
2.  **Logic:** Set of pure functions: `calculateWaste()`, `findOptimization()`, `checkRedundancy()`.
3.  **Output:** A structured JSON object compatible with the frontend Dashboard components.

## 5. Database Schema
```sql
CREATE TABLE audits (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    stack_data JSONB NOT NULL,        -- Input: tools, seats, spend
    analysis_results JSONB NOT NULL,  -- Output: savings, recommendations
    ai_summary TEXT,                  -- Qualatative AI-generated text
    share_slug TEXT UNIQUE NOT NULL,  -- For public URLs
    lead_email TEXT,                  -- Optional: captured post-audit
    is_high_value BOOLEAN DEFAULT FALSE
);

Security & Performance
Validation: Dual-layer validation. Frontend (Zod) for UX; Backend (Zod) for data integrity.

Rate Limiting: Express-rate-limit middleware applied to the /api/v1/audit and email endpoints to prevent API abuse.

Observability: Pino logs all 4xx and 5xx errors with request context for rapid incident response.

SEO: Since this is a Vite SPA, we utilize react-helmet-async for dynamic meta tags on shareable result pages.

7. Project Structure
Plaintext
.
├── frontend/               # React 19 Client
│   ├── src/
│   │   ├── components/     # UI via shadcn/ui
│   │   ├── hooks/          # useAuditStore (Zustand), useSubmitAudit
│   │   ├── lib/            # Form schemas (Zod), formatters
│   │   └── pages/          # Landing, Audit, Results
├── backend/                # Node.js 24 Server
│   ├── src/
│   │   ├── engine/         # Deterministic Logic
│   │   ├── routes/         # API Endpoints
│   │   ├── services/       # AI (Anthropic), DB (Postgres)
│   │   └── middleware/     # Rate limiting, Logging
└── shared/                 # Shared TypeScript types/interfaces