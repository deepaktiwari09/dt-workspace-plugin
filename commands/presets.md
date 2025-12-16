---
description: "List available template presets with descriptions. Shows all supported architecture patterns."
allowed-tools: ["Read"]
---

# List Available Presets

Display all available template presets with their descriptions and use cases.

## Output

```
DT-WORKSPACE PRESETS

Available template presets for documentation generation:

┌─────────────────────┬────────────────────────────────────────────────────────┐
│ Preset              │ Description                                            │
├─────────────────────┼────────────────────────────────────────────────────────┤
│ microservices       │ NestJS microservices with Kafka, WebSocket, PostgreSQL │
│ monolith            │ Single application with layered architecture           │
│ serverless          │ AWS Lambda, API Gateway, DynamoDB                      │
│ supabase            │ Supabase with PostgreSQL, Auth, Storage, Edge Funcs    │
│ firebase            │ Firebase/Firestore with Cloud Functions                │
│ nextjs-fullstack    │ Next.js App Router with Server Components, Prisma      │
│ graphql-federation  │ Apollo Federation with subgraphs                       │
│ kubernetes          │ K8s deployments with Helm charts                       │
│ event-sourcing      │ Event-sourced architecture with CQRS                   │
└─────────────────────┴────────────────────────────────────────────────────────┘

Usage:
  /dt-workspace:init              # Select preset during init
  /dt-workspace:scaffold --preset <name>   # Override default preset

Custom presets:
  Export templates: /dt-workspace:export --preset <name>
  Edit in: .dt-templates/<preset>/
```

## Preset Details

### microservices (default)
Best for: Distributed systems, high scalability needs
Documents: Kafka events, WebSocket specs, service boundaries

### monolith
Best for: Startups, MVPs, simpler deployments
Documents: Module interactions, layered architecture, shared resources

### serverless
Best for: Event-driven, pay-per-use, auto-scaling needs
Documents: Lambda specs, IAM policies, event sources

### supabase
Best for: Rapid development, real-time apps, PostgreSQL preference
Documents: RLS policies, Edge Functions, Realtime subscriptions

### firebase
Best for: Mobile-first, real-time sync, Google ecosystem
Documents: Firestore rules, Cloud Functions, Auth flows

### nextjs-fullstack
Best for: React apps, SSR/SSG, modern web development
Documents: Server Components, Server Actions, caching strategies

### graphql-federation
Best for: Large teams, domain-driven design, unified API
Documents: Subgraph boundaries, federation directives, gateway config

### kubernetes
Best for: Container orchestration, cloud-native apps
Documents: K8s resources, Helm charts, networking, observability

### event-sourcing
Best for: Audit trails, temporal queries, complex domains
Documents: Event schemas, aggregates, projections, sagas
