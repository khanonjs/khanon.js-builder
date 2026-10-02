# khanon.js-builder
Fronend (React): Webpage to display and build through AI prompts, Khanon.js application architectures, displaying the schema in different sections.
  - Graphical schemas per tab:
    - States
    - Scenes
    - Cameras
    - Actors
    - Input Events
    - Assets

Backend:
  - Server queues-events (NestJS): Quesues and events
    - API 1: RabbitMQ queue system to handle client AI prompts sent to AI wrapper server.
    - API 2: Kafka architecture change log and domain events.
  - Server ai-Wrapper (Node.js / Express): AI wrapper that interacts with LLMs API as agentic sessions
  - Server user-Data (NestJS): User profile (MongoDB) and projects data (PostgreSQL)

## Features
- Authorization (OAuth 2.0 and OIDC) for both Node and NestJS servers.

## Dependencies
- RabbitMQ
- Kafka
- MongoDB
- PostgreSQL

## Tools
- Nx monorepo
- Docker compose
  - Frontend
  - RabitMQ server
  - Kafka server
  - MongoDB server
  - PostgreSQL server
  - Server 1
  - Server 2
  - Server 3
- Dockerfile within each project for their deployment (1 frontend, 3 backends)

Fronend (React): Webpage to display and build through AI prompts, Khanon.js application architectures, displaying the schema in different sections.
  - Graphical schemas per tab:
    - States
    - Scenes
    - Cameras
    - Actors
    - Input Events
    - Assets

Backend:
  - Server queues-events (NestJS): Quesues and events
    - API 1: RabbitMQ queue system to handle client AI prompts sent to AI wrapper server.
    - API 2: Kafka architecture change log and domain events.
  - Server ai-Wrapper (Node.js / Express): AI wrapper that interacts with LLMs API as agentic sessions
  - Server user-Data (NestJS): User profile (MongoDB) and projects data (PostgreSQL)

## Features
- Authorization (OAuth 2.0 and OIDC) for both Node and NestJS servers.

## Dependencies
- RabbitMQ
- Kafka
- MongoDB
- PostgreSQL

## Tools
- Nx monorepo
- Docker compose
  - Frontend
  - RabitMQ server
  - Kafka server
  - MongoDB server
  - PostgreSQL server
  - Server 1
  - Server 2
  - Server 3
- Dockerfile within each project for their deployment (1 frontend, 3 backends)
