# khanon.js-builder
Frontend (React): Webpage to display and build through AI prompts, Khanon.js application architectures, displaying the schema in different sections.
  - Graphical schemas per tab:
    - States
    - Scenes
    - Cameras
    - Actors
    - Input Events
    - Assets

Backend:
  - Server gateway (Node.js / Express): Backend for frontend for authentication/authorization (OAuth2 / OIDC), API routing, rate limiting.
  - Server ai-wrapper (Node.js / Express): AI wrapper that runs agentic sessions against LLM APIs. Consumes generation jobs from RabbitMQ and publishes AI events to Kafka.
  - Server user-data (NestJS): User profile (MongoDB) and project data (PostgreSQL). Owns fine-grained authorization, enqueues generation jobs, validates AI results and emits architecture domain events.

All backend servers validate the JWT (Keycloak JWKS). Service-to-service calls use client credentials.

## Dependencies
- Keycloak: Identity provider (OAuth 2.0 / OIDC)
- RabbitMQ: AI generation job queue (user-data -> ai-wrapper)
- Kafka:
  - Architecture change log and domain events (user-data)
  - AI generation and usage events (ai-wrapper -> user-data)
- MongoDB: User profiles
- PostgreSQL: Project data

## Tools
- Nx monorepo
  - `libs/contracts`: shared message schemas
- Docker compose
  - Frontend
  - Backend servers
  - Keycloak server
  - RabbitMQ server
  - Kafka server
  - MongoDB server
  - PostgreSQL server
- Dockerfile within each project for their deployment (1 frontend, 3 backends)
