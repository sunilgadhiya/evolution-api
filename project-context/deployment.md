# Deployment Architecture

## Infrastructure
- **Cloud Provider**: Oracle Cloud (OCI) - single VM.
- **Containerization**: Docker & Docker Compose (`docker-compose.yaml`).

## Process Management
- Node.js execution via `tsx` for development, plain `node` for production.

## Environment Variables
Key variables required:
```bash
DATABASE_PROVIDER=postgresql
DATABASE_CONNECTION_URI=postgres://user:pass@host:5432/evolution
AUTHENTICATION_API_KEY=global_secret_key
CACHE_REDIS_ENABLED=true
CACHE_REDIS_URI=redis://redis:6379
SERVER_URL=http://localhost:8080
```

## Build & Deploy Commands
```bash
# Build
npm run build

# Start Production
npm run start:prod

# Docker Compose
docker-compose up -d
```
