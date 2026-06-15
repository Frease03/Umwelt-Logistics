# Umwelt-Logistics
Umwelt Logistics is an open-source-first logistics platform built as a learning project for understanding how modern applications work end to end.
The goal is to explore:

- microservice design
- infrastructure provisioning
- GitOps deployment
- observability and operations
- resilient distributed systems
- practical AI features in a production app
- full-stack development with `Node.js` and `React`

## Project Vision

This project will model common logistics workflows such as:

- creating shipments
- assigning vehicles and drivers
- tracking package movement
- handling delivery events
- notifying customers and operators
- producing billing and reporting data

The system is intentionally designed to grow in stages so it can be used as a practical learning path instead of a large, hard-to-maintain platform from day one.

## Learning Goals

This app is meant to teach how real-world systems are built and operated.

You should expect to learn:

- how to define service boundaries
- how APIs and events work together
- how each service owns its own data
- how infrastructure is provisioned with code
- how GitOps keeps deployments reproducible
- how to observe failures and debug distributed systems

## Guiding Principles

- Use open-source tools wherever possible.
- Keep the first version small and understandable.
- Add microservices gradually, not all at once.
- Prefer clear boundaries over premature optimization.
- Build for learning, but keep the architecture realistic.

## Proposed Architecture

### Core services

The initial version can start with a small set of services:

- `auth-service`
- `shipment-service`
- `fleet-service`
- `tracking-service`
- `notification-service`
- `billing-service`

### Frontend

- `web-app` built with `React`
- shared UI components for dashboards, shipment views, and operator tooling

### AI services

The project will also include an AI layer to explore how intelligent features are added to a real system:

- `chatbot-service` for customer support, dispatch help, and operator assistance
- `ai-assistant-service` for internal and customer-facing assistance
- `route-optimization-service` for delivery and fleet suggestions
- `document-processing-service` for invoices, manifests, and shipment documents
- `forecasting-service` for demand, delays, and capacity planning

### Supporting platform services

- API gateway
- message broker
- container registry
- observability stack
- secrets management
- GitOps controller
- model serving or inference runtime
- vector database for semantic search if needed

### Communication model

- REST for external and synchronous requests
- events for internal workflows and asynchronous processing
- idempotent handlers for reliability
- retries, dead-letter queues, and outbox patterns where needed

## Open-Source Stack

The plan is to keep the platform centered on open-source software.

- `Node.js` for backend services
- `React` for the frontend
- `Kubernetes` for orchestration
- `OpenTofu` or `Terraform` for infrastructure as code
- `Argo CD` for GitOps
- `Helm` or `Kustomize` for Kubernetes packaging
- `PostgreSQL` for transactional data
- `Kafka`, `RabbitMQ`, or `NATS` for messaging
- `Prometheus` and `Grafana` for metrics and dashboards
- `Loki` for logs
- `Tempo` or `Jaeger` for tracing
- `Keycloak` for identity and access
- `cert-manager` for TLS certificates
- `NGINX Ingress` or `Traefik` for ingress
- `Ollama`, `vLLM`, or `Text Generation Inference` for model serving
- `pgvector`, `Qdrant`, or `Milvus` for embeddings and semantic retrieval
- `LangChain` or `LlamaIndex` for orchestration if needed

## Infrastructure Plan

The infrastructure should be provisioned in code and deployed in layers.

### Layer 1: Foundation

- network
- compute cluster
- container registry
- DNS
- TLS

### Layer 2: Platform

- ingress controller
- GitOps controller
- monitoring
- logging
- tracing
- secrets management

### Layer 3: Application services

- service deployments
- service-specific databases
- message broker topics or queues
- config maps and secrets

### Layer 4: AI capabilities

- model inference endpoint
- prompt and tool routing
- embeddings storage
- document extraction pipeline
- evaluation and feedback loop

## GitOps Flow

The deployment process should follow a simple and auditable path:

1. Developer updates application code.
2. CI runs tests, builds images, and scans artifacts.
3. CI publishes the container image.
4. CI updates the GitOps manifest repository.
5. Argo CD detects the change and syncs the cluster.
6. Kubernetes rolls out the new version.

This approach keeps deployment history in Git and makes rollbacks easier to reason about.

## Repository Structure

```text
repo/
  apps/
    auth-service/
    shipment-service/
    fleet-service/
    tracking-service/
    notification-service/
    billing-service/
  infra/
    opentofu/
  deploy/
    base/
    dev/
    staging/
    prod/
  platform/
    argocd/
    monitoring/
    ingress/
    security/
```

## Phased Roadmap

### Phase 1: Foundation

- choose the primary backend language
- create the repo structure
- define service boundaries
- provision the base infrastructure
- install the GitOps controller
- set up logging and monitoring

### Phase 2: First Services

- build the auth service
- build the shipment service
- build the tracking service
- build the React web app
- add database ownership per service
- connect services with events

### Phase 3: Platform Maturity

- add fleet, notification, and billing services
- add dashboards and alerting
- improve deployment automation
- add retries, queues, and dead-letter handling

### Phase 4: AI Features

- add an AI assistant for operations support
- add a chatbot for customer and internal support
- add document understanding for logistics paperwork
- add forecasting for demand and delays
- add route and dispatch recommendations
- log prompt usage, outputs, and feedback for evaluation

### Phase 5: Hardening

- add backups and disaster recovery
- add autoscaling
- improve security controls
- add tracing and operational runbooks
- document service contracts and workflow diagrams

## Success Criteria

The project is in a good place when:

- each service can be developed and deployed independently
- infrastructure can be recreated from code
- deployments happen through GitOps
- logs, metrics, and traces are available
- core logistics workflows can run end to end
