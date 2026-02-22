# ClimbingTracker – Technical Architecture (React)

## 1. Stack
Frontend:
- React + TypeScript
- Routing: React Router
- Data fetching: fetch/axios (optionally React Query later)
- Forms: React Hook Form (optional)
- Charts (later): Recharts

Backend:
- Node + Express + TypeScript

Database:
- MongoDB (Mongoose)

## 2. High-Level Architecture
React Client → REST API (Express) → MongoDB

Optional:
- Auth (JWT) in Phase 2
- File storage (images) later if needed

## 3. Suggested Folder Structure

### client/
src/
  app/
    routes/
    layout/
  features/
    sessions/
      components/
      hooks/
      api/
      types.ts
    analytics/
    dashboard/
  shared/
    components/
    lib/
    types/
  main.tsx

### server/
src/
  routes/
  controllers/
  services/
  models/
  middleware/
  validators/
  index.ts

docs/

## 4. Frontend State Plan
MVP:
- Keep state local to pages/components
- Use a small `sessions` API module for CRUD
- Refetch after create/update/delete (simple + reliable)

Later (if needed):
- Introduce React Query for caching and optimistic updates

## 5. Validation Rules
Client:
- Required fields by session type (basic form validation)

Server:
- Schema + request validation (zod/joi or custom)
- Reject invalid enums, negative durations, etc.

## 6. Performance + Indexing
Typical query:
- Sessions for user (or single-user) sorted by date descending
- Filter by type, date range, boardType, tags

Indexes (MongoDB):
- userId + startTime
- userId + type + startTime
- tags (optional)

## 7. Observability (MVP)
- API request logging (basic)
- Centralized error response shape

## 8. Testing Plan
MVP:
- Server: basic controller/service tests for CRUD
- Client: basic render tests for core pages
