# Architecture

## System Overview
Evolution API acts as a gateway between REST clients and WhatsApp networks, using an event-driven architecture.

```text
┌─────────────────┐       ┌─────────────────┐       ┌───────────────┐
│ Client/CRM/SaaS │ ◄───► │  Evolution API  │ ◄───► │ WhatsApp Meta │
└─────────────────┘       └─────────────────┘       └───────────────┘
                                 │   │
                  ┌──────────────┘   └──────────────┐
           ┌────────────┐                    ┌────────────┐
           │ Integrations│                    │ Events/MQ  │
           └────────────┘                    └────────────┘
```

## Technology Stack
- **Backend**: Node.js 20+, TypeScript 5+, Express 4.
- **Database**: PostgreSQL / MySQL (via Prisma ORM).
- **Cache/State**: Redis + node-cache.
- **WhatsApp Provider**: Baileys (WhatsApp Web API), WhatsApp Cloud API.

## Key Architectural Patterns
- **Multi-Tenancy**: Isolated sessions based on `instanceName`.
- **RouterBroker Pattern**: Abstracted routing logic (`src/api/routes`).
- **Thin Controllers & Fat Services**: Business logic lives in `src/api/services`.
- **JSONSchema Validation**: DTOs do not use decorators. Validation occurs dynamically using `json-schema`.

## Data Flow
1. HTTP Request `->` RouterBroker `->` JSONSchema Validator `->` Controller `->` Service `->` WAMonitoringService `->` Baileys Socket `->` WhatsApp Server.
2. WhatsApp Event `->` Baileys Socket `->` WAMonitoringService `->` EventEmitter `->` Webhook/RabbitMQ/SQS `->` Client.
