# Order-Microservice
## Summary
Minimal NestJS-based Order microservice scaffold intended for the Seltra.io Senior Backend Engineer take-home task.
It implements:
- REST endpoints: `POST /orders`, `GET /orders`, `GET /orders/:id`
- PostgreSQL persistence (TypeORM entity example)
- Basic JWT auth guard stub
- Redis-based job queue (bullmq) skeleton for reminders
- WebSocket notifications (socket.io gateway skeleton)
- Docker + docker-compose for local dev
- README with setup & assumptions

## Assumptions & decisions
- This scaffold focuses on structure and integration points; it's **not** a production-ready full implementation.
- Uses TypeORM for familiarity; replaceable with Prisma or Sequelize.
- BullMQ is suggested for background jobs; a simple processor skeleton is included.
- JWT auth is stubbed; in production, integrate with Identity Service / OAuth.
- WebSocket notifications use a Socket.IO gateway example.

## Setup (local)
1. Install dependencies:
   ```bash
   npm install
   ```
2. Start Docker services (Postgres + Redis):
   ```bash
   docker-compose up -d
   ```
3. Set env variables (or use docker-compose):
   - DATABASE_URL (e.g. postgres://seltra:seltra@localhost:5432/seltra)
   - REDIS_URL (e.g. redis://localhost:6379)
   - JWT_SECRET
4. Run in dev mode:
   ```bash
   npm run start:dev
   ```

## API Endpoints
- `POST /orders` — create an order (requires Authorization: Bearer <token>)
- `GET /orders` — list orders (supports simple pagination query params)
- `GET /orders/:id` — get order by id

## How to run tests
- Tests are placeholders; run `npm test` for lint/test harness in real implementation.

## What to improve with +4 hours
- Complete auth integration with passport-jwt and roles.
- Add migrations and seed scripts with TypeORM or migrate tool.
- Implement real job processing, reminders, and integration tests.
- Add e2e tests (Supertest + Jest) and CI pipeline.
- Add metrics & health endpoints.

