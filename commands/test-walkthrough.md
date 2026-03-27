---
description: Perform a browser run through to verify features or debug issues
model: opus
---

# Browser walk through

Do a run through using **agent-browser** in headed mode to test the web app is working as expected and all core business logic is functional.

Make sure to use agent-browser.

**Important** verify with the user that they can see the browser before continuing

## Setup and verification

Run the full stack locally including the frontend, backend, and database. Capture all server and browser
logs to perform verification on features or debugging on issues.

**Important** Use subagents for reading and monitoring logs to not bloat context
**Important** Use subagents to visually inspect screenshots of the UI to verify UI changes
**Important** Avoid manually mutating the database state because this can result in undefined behaviour. Ideally make all changes to the database through the UI which will maintain a valid testing state.
**Important** After testing ask the user permission to clean up state which involves stopping the webapp servers, shutting down the local database, deleting UI screenshots, and any other ephemeral data that is not needed outside the test.

## Running the local database

This project uses **Supabase** (PostgreSQL) as the local database via Docker. All commands use `npx supabase` (or the global `supabase` CLI if installed).

### Startup sequence

1. **Stop any existing instance first** to avoid stale state:
   ```bash
   npx supabase stop
   ```
2. **Start fresh**:
   ```bash
   npx supabase start
   ```
   This spins up PostgreSQL, Auth, Storage, and other Supabase services in Docker containers. It prints connection details (API URL, DB URL, anon key, etc.) on success.
3. **Apply migrations** (if any are pending):
   ```bash
   npx prisma migrate deploy
   ```
4. **Seed the database** with test data:
   ```bash
   NODE_ENV=development npm run prisma:seed
   ```
   The seed script requires `NODE_ENV=development` — it will refuse to run otherwise. After seeding, the admin account is available: `admin@playersleague.com` / `DevPassword123!`

### Useful commands

| Command                 | Purpose                                                                   |
| ----------------------- | ------------------------------------------------------------------------- |
| `npx supabase status`   | Check running status and connection details (API URL, DB URL, Studio URL) |
| `npx supabase stop`     | Stop all local Supabase containers                                        |
| `npx supabase start`    | Start local Supabase containers                                           |
| `npx supabase db reset` | Reset DB to a clean state (re-runs all migrations + seed)                 |
| `npx prisma studio`     | Open Prisma Studio GUI to browse database tables                          |

### Common gotchas

- **Docker must be running** before `supabase start`. If it fails, check Docker Desktop is up.
- **Port conflicts**: Supabase uses ports 54321 (API), 54322 (Studio), 54323 (DB), among others. If these are occupied, `supabase start` will fail.
- **Seed requires NODE_ENV**: Running `npm run prisma:seed` without `NODE_ENV=development` will error with "Seed script may only run in development or test environments."
- **Prisma client regeneration**: If you change `prisma/schema.prisma`, run `npm run prisma:generate` before starting the dev server.

## Commonly faced speed bumps

1. The dev server may already be running. Kill port 3000 before starting fresh: `lsof -ti:3000 | xargs kill -9`
2. Supabase may already be running. Always stop and restart from a fresh instance to avoid stale state.
3. Migrations may be pending after a branch switch. Run `npx prisma migrate deploy` to apply them.
