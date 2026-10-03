# ai-wrapper

Node.js/Express AI wrapper: agentic sessions against LLM APIs. Consumes generation jobs from RabbitMQ, publishes AI generation/usage events to Kafka.

Empty for now; generated in its own prompt. Has its own Dockerfile. Validates JWT against Keycloak JWKS. All node dependencies live in the root package.json. Message payloads come from `libs/contracts`.
