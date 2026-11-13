<!-- This is a Kanban Board file created with MD Kanban extension -->
<!-- GitHub: https://github.com/jebakumarj/md-kanban -->
<!-- VS Code Extension: Search "MD Kanban" in the extension store (ID: jeddak.md-kanban) -->

# SATMS Board

## Backlog

### Data Model

#### Database Seeding (Tables 1–7)
<!-- id: task-1794594603363-86 -->
Create a TypeScript database seed script to prepopulate mandatory tables "Tisch 1" through "Tisch 7".
- [ ] Configure seed script setup in server/package.json
- [ ] Write seed script to insert tables 1 through 7 idempotently
- [ ] Execute seed script and verify records via VS Code SQLite Viewer
Tags: `seed` `database` `prisma` `phase-2`
<!-- priority: high -->
<!-- workload: easy -->
<!-- due: 2026-11-14 -->
<!-- assignee: Mihael Plantic -->

## TODO

### Data Model

#### Prisma Schema & SQLite Implementation
<!-- id: task-1794594555521-70 -->
Translate the data model into server/prisma/schema.prisma with strict typing and correct relational mapping.
- [ ] Write Prisma schema models for Table, Product, Purchase, and LineItem
- [ ] Configure SQLite datasource and generator options
- [ ] Run initial Prisma migration (npx prisma migrate dev --name init)
- [ ] Verify server/prisma/dev.db is created and matches the schema using SQLite Viewer extension
Tags: `prisma` `sqlite` `database` `backend` `phase-2`
<!-- priority: high -->
<!-- due: 2026-11-14 -->
<!-- assignee: Mihael Plantic -->

## IN PROGRESS

## DONE

### Setup

#### Setup
<!-- id: task-1794594704626-159 -->
Project Setup
- [x] Repo initialization
- [x] folder structure
- [x] server/web scaffolded
- [x] .gitignore locked down
- [x] decisions documented
Tags: `setup` `documentation`
<!-- priority: critical -->
<!-- workload: easy -->
<!-- due: 2026-11-13 -->
<!-- assignee: Mihael Plantic -->

### Zettle Access

#### Zettle OAuth Token Exchange & Credential Validation
<!-- id: task-1794594224970-0 -->
Exchange your private Zettle API key and client ID for a temporary OAuth 2.0 bearer token using Bruno. Document token lifetime and store credentials securely.
- [x] Create POST request in Bruno for [https://oauth.zettle.com/token](https://oauth.zettle.com/token)
- [x] Configure grant_type, client_id, and assertion (API key)
- [x] Verify successful response and extract access_token
- [x] Document token expiration time (7200 seconds / 2 hours)
- [x] Set up Bruno environment variables for secure local reuse
Tags: `zettle` `auth` `api` `phase-1`
<!-- priority: high -->
<!-- workload: easy -->
<!-- due: 2026-11-14 -->
<!-- assignee: Mihael Plantic -->

### Data Model

#### Paper Data Model & Entity Relationship Mapping
<!-- id: task-1794594493569-45 -->
Sketch out core database entities (Tables, Products, Purchases, LineItems, Sessions) on paper before touching code, ensuring integer cent money handling and UTC time rules.
- [x] Sketch entity relationship diagram (ERD) on paper or in docs/
- [x] Define primary and foreign keys for Tables, Purchases, LineItems, and Products
- [x] Document data constraints (money in integer cents, timestamps stored in UTC)
Tags: `database` `architecture` `modeling` `phase-2`
<!-- workload: easy -->
<!-- due: 2026-11-14 -->
<!-- assignee: Mihael Plantic -->

### Zettle Access

#### Document Zettle Field Specs & Answer Research Questions
<!-- id: task-1794594433178-35 -->
Create docs/zettle-fields.md. Map out purchase/product schemas and document empirical answers to the five experimental questions in the build guide.
- [x] Create docs/zettle-fields.md
- [x] Document purchase object fields (purchaseUUID, timestamps, amount in cents, VAT, line items, payments, refund links)
Tags: `documentation` `zettle` `api-spec` `research` `phase-1`
<!-- priority: high -->
<!-- workload: easy -->
<!-- due: 2026-11-14 -->
<!-- assignee: Mihael Plantic -->

#### Capture and Scrub Zettle Response Fixtures
<!-- id: task-1794594304127-4 -->
Request purchase history and product library endpoints via Bruno. Save scrubbed, privacy-compliant JSON responses into the fixtures/ directory.
- [x] Pull and save fixtures/products.json
- [x] Pull and save fixtures/purchases.json
- [x] Pull and save cash and card receipt fixtures
- [x] Pull and save refund fixture and a receipt containing a "Tisch" product
- [ ] Scrub all personal data (guest/staff names) from every JSON file
Tags: `fixtures` `zettle` `json` `privacy` `phase-1`
<!-- priority: high -->
<!-- due: 2026-11-14 -->
<!-- assignee: Mihael Plantic -->
