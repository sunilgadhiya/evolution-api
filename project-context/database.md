# Database Architecture

## Engine & ORM
- **Engines Supported**: PostgreSQL, MySQL.
- **ORM**: Prisma (`@prisma/client` v6).

## Schema Overview
- Uses provider-specific schemas (`prisma/postgresql-schema.prisma`).
- Core concept is the **Instance**, which represents a single connected WhatsApp number.
- No Row-Level Security (RLS) is used by default as the project handles multitenancy via application-level `instanceName` scoping.

## Migration Strategy
- Migrations are provider-specific and managed via `npm run db:migrate:dev` / `npm run db:deploy`.
- Before running Prisma commands, the `DATABASE_PROVIDER` environment variable MUST be set.

## Sensitive Data Handling
- Credentials and tokens are stored in the database.
- Webhook endpoints and API keys are associated with specific instances.
