# Architecture Decisions

| Date | Decision | Rationale | Trade-offs |
|---|---|---|---|
| Initial | Dual DB Support (PostgreSQL/MySQL) | Maximize open-source adoption by supporting the two most popular relational DBs. | Requires parallel Prisma schemas and `runWithProvider.js` scripts, adding maintenance overhead. |
| Initial | JSONSchema for Validation | Avoids the overhead and decorator magic of `class-validator` / `class-transformer`. | DTOs are plain classes, requiring manual schema definitions. |
| V2 | RouterBroker Pattern | Standardizes route declaration, validation, and error handling. | Steep learning curve for new contributors compared to standard Express routers. |
