# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status

The repository currently contains only `README.md` and `LICENSE`. No code, `package.json`, Nx config, or Docker files exist yet, so there are no build/lint/test commands to document. Everything below is the planned architecture from the README; update this file as the projects are scaffolded (especially the commands, including how to run a single test).

## Purpose

A web app to build Khanon.js application architectures through AI prompts, displaying the resulting schema in graphical tabs: States, Scenes, Cameras, Actors, Input Events, Assets.

## Planned architecture

Nx monorepo with four deployable projects (each with its own Dockerfile) plus shared libs, orchestrated locally by Docker Compose (also runs Keycloak, RabbitMQ, Kafka, MongoDB, PostgreSQL):

- **Frontend** (React): schema viewer/builder UI.
- **gateway** (Node.js/Express): backend-for-frontend. Handles OAuth2/OIDC authentication/authorization, API routing, rate limiting.
- **ai-wrapper** (Node.js/Express): runs agentic sessions against LLM APIs. Consumes generation jobs from RabbitMQ; publishes AI generation/usage events to Kafka.
- **user-data** (NestJS): owns user profiles (MongoDB) and project data (PostgreSQL). Owns fine-grained authorization, enqueues generation jobs, validates AI results, and emits architecture domain events / change log to Kafka.
- `libs/contracts`: shared message schemas (the contract for RabbitMQ jobs and Kafka events between services).

### Cross-service flow

- Generation: user-data --(RabbitMQ job)--> ai-wrapper --(Kafka AI generation/usage events)--> user-data, which validates results before persisting.
- Auth: all backend servers validate the JWT against Keycloak JWKS; service-to-service calls use client credentials.
- Message payloads between services should be defined in `libs/contracts`, not duplicated per service.
