# Template Presets Reference

## Microservices Preset

**Architecture**: NestJS microservices with Kafka, WebSocket, PostgreSQL, MongoDB, AWS

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview with features and technical components |
| user-flows/ | Detailed user journey scenarios (split by feature) |
| technical-specs.md | NestJS microservices architecture and specifications |
| api-contracts.md | Complete API endpoint specifications with OpenAPI format |
| database-schema.md | Database models, migrations, and relationships |
| realtime-events.md | Kafka topics, WebSocket events, and event schemas |
| security-specs.md | Authentication, authorization, and security controls |
| testing-strategy.md | Unit, integration, and E2E testing approach |
| error-handling.md | Error codes, handling strategies, and monitoring |
| features/*.feature | BDD Gherkin feature files |
| timeline.md | Platform-level development timeline |

---

## Monolith Preset

**Architecture**: Single application with layered architecture (Presentation/Business/Data)

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Layered architecture specifications |
| api-contracts.md | API documentation |
| database-schema.md | Shared database models |
| module-interactions.md | Internal module communication patterns |
| security-specs.md | Security controls |
| testing-strategy.md | Testing approach |
| error-handling.md | Error handling |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## Serverless Preset

**Architecture**: AWS Lambda, API Gateway, DynamoDB, S3, SQS, EventBridge

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Lambda function specifications |
| api-contracts.md | API Gateway endpoints |
| database-schema.md | DynamoDB table designs |
| event-sources.md | S3, SQS, EventBridge, DynamoDB Stream triggers |
| iam-policies.md | Lambda IAM roles and policies |
| security-specs.md | Security controls |
| testing-strategy.md | Testing approach (including local testing) |
| error-handling.md | Error handling with cold start considerations |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## Supabase Preset

**Architecture**: Supabase with PostgreSQL, Auth, Storage, Edge Functions

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Supabase architecture |
| api-contracts.md | REST API and RPC functions |
| database-schema.md | PostgreSQL with RLS policies |
| auth-flows.md | Supabase Auth integration |
| storage-specs.md | Supabase Storage buckets |
| realtime-specs.md | Supabase Realtime subscriptions |
| edge-functions.md | Deno Edge Functions |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## Firebase Preset

**Architecture**: Firebase/Firestore with Cloud Functions, Auth, Storage

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Firebase architecture |
| api-contracts.md | Callable functions and REST endpoints |
| database-schema.md | Firestore collections and security rules |
| auth-flows.md | Firebase Auth integration |
| storage-specs.md | Cloud Storage rules |
| cloud-functions.md | Cloud Functions specifications |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## Next.js Fullstack Preset

**Architecture**: Next.js App Router with Server Components, Server Actions, Prisma

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Next.js architecture (RSC, Server Actions) |
| api-contracts.md | Route handlers and Server Actions |
| database-schema.md | Prisma schema |
| component-specs.md | React component specifications |
| state-management.md | Client/server state patterns |
| caching-strategy.md | Next.js caching and revalidation |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## GraphQL Federation Preset

**Architecture**: Apollo Federation with subgraphs, gateway, and distributed schema

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Federation architecture |
| schema-specs.md | GraphQL schema with federation directives |
| resolver-specs.md | Resolver implementations |
| database-schema.md | Database models |
| subgraph-specs.md | Subgraph boundaries and entities |
| gateway-specs.md | Gateway configuration |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## Kubernetes Preset

**Architecture**: Kubernetes deployments with Helm charts, services, ingress

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | Service architecture |
| api-contracts.md | API documentation |
| database-schema.md | Database models |
| k8s-resources.md | Deployment, Service, ConfigMap, Secret specs |
| helm-charts.md | Helm chart structure and values |
| networking.md | Ingress, Service Mesh configurations |
| observability.md | Logging, metrics, tracing |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |

---

## Event Sourcing Preset

**Architecture**: Event-sourced architecture with CQRS, event store, projections

**Documents Generated**:
| Document | Description |
|----------|-------------|
| README.md | Module overview |
| user-flows/ | User journey scenarios |
| technical-specs.md | CQRS/ES architecture |
| api-contracts.md | Command and Query APIs |
| event-schema.md | Domain events and versioning |
| aggregate-specs.md | Aggregate root specifications |
| projection-specs.md | Read model projections |
| saga-specs.md | Process managers and sagas |
| event-store.md | Event store configuration |
| features/*.feature | BDD feature files |
| timeline.md | Development timeline |
