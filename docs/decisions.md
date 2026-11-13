# SATMS – Technical & Project Decisions

## 1. Environment & Tooling Versions (Phase 0)
- **Node.js:** v26.4.0
- **Git:** 2.56.1.windows.1
- **Editor:** VS Code
- **REST Client:** Bruno

## 2. Data & Domain Conventions
- **Money:** All monetary values are stored and calculated strictly in **integer cents** (e.g., `1250` for `€12.50`). Never use floating-point numbers for currency.
- **Timestamps & Timezones:** All timestamps are stored in **UTC** in SQLite/Prisma and converted to **Europe/Berlin** only at the UI/report presentation layer.
- **Pure Business Logic:** Sessions, guest estimates, dayparts, and threshold calculations are written as pure TypeScript functions (data in, result out) with zero database or Express dependencies.
- **Privacy / Fixtures:** Real Zettle API responses saved in `fixtures/` must have guest and staff names stripped before committing.

## 3. Language & Localization
- **Codebase:** 100% **English** (file names, variables, types, database columns, comments, documentation).
- **UI / Screens:** **German** (fixed from Phase 0 since restaurant staff will use the app).

## 4. Git & Workflow Rules
- **Branching:** One branch per feature/phase (`feat/...`, `fix/...`), merged to `main` only after typechecks and tests pass.
- **Commit Style:** Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:`, `test:`). Every commit message states what works now.
- **Daily Commands (from repo root):**
  - Start server: `npm run dev:server`
  - Start web app: `npm run dev:web`
  - Run tests: `npm test`
  - Typecheck: `npm run typecheck`