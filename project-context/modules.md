# Modules map

## Directory Structure
- `src/api/routes/`: Express route definitions (RouterBroker).
- `src/api/controllers/`: Thin HTTP adapters.
- `src/api/services/`: Core domain logic.
- `src/api/integrations/`: Third-party service clients.

## Core Modules
- **Instance**: Manages WhatsApp device pairing, QR codes, connection states.
- **Message**: Sending text, media, buttons, lists, audio.
- **Chat/Group**: Managing WhatsApp groups, participants, chat history.
- **Webhooks**: Emitting events (messages, connection updates) to external systems.
- **Integrations**: Chatwoot, Typebot, Dify, SQS, RabbitMQ.
