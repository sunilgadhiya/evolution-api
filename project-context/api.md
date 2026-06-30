# API Documentation

## Base URL & Versioning
- Standard paths: `/instance`, `/message`, `/chat`, `/group`.
- No strict `/v1/` prefix in standard OSS deployment.

## Authentication
- Requires `apikey` header.
- Global API key (`AUTHENTICATION_API_KEY`) or Instance-specific API keys.

## Key Endpoints
| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/instance/create` | Creates a new WhatsApp instance |
| GET  | `/instance/connect/:instance` | Retrieves QR code or pairing code |
| POST | `/message/sendText/:instance` | Sends a text message |
| POST | `/message/sendMedia/:instance` | Sends media (image/video/document) |

## Rate Limiting & Errors
- Optional rate limits can be configured in `.env`.
- Returns standard HTTP status codes (400 for validation errors, 404 for missing instances, 401 for bad API key).
