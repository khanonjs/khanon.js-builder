# user-data

NestJS service: user profiles (MongoDB), project data (PostgreSQL), fine-grained authorization, enqueues generation jobs, validates AI results, emits architecture domain events to Kafka.

Empty for now; generated in its own prompt. Has its own Dockerfile. Validates JWT against Keycloak JWKS. All node dependencies live in the root package.json. Message payloads come from `libs/contracts`.
