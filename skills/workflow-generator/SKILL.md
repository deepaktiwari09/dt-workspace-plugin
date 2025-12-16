---
description: "Use this skill when user asks to generate workflow documentation, analyze SOW files, create project structure from requirements, scaffold documentation, or work with dt-workspace features. Triggers on: 'generate documentation', 'analyze SOW', 'scaffold project', 'create workflow docs', 'dt-workspace', 'from SOW file', 'module documentation'."
---

# Workflow Documentation Generator

Generate comprehensive workflow documentation from Statement of Work (SOW) documents. This skill enables creating organized project documentation including BDD feature files, API contracts, database schemas, and technical specifications.

## Core Workflow

### 1. Initialize Project Configuration

Before generating documentation, create a `.dt-workspace` config file:

```json
{
  "version": "1.0.0",
  "projectName": "Project Name",
  "sowPath": "./sow.md",
  "defaultPreset": "microservices",
  "outputDirectory": "./workflows",
  "generatedAt": "ISO timestamp",
  "generatedPaths": {
    "platforms": {}
  }
}
```

### 2. Analyze SOW Document

Extract structured module definitions from SOW markdown. Return JSON with:

```json
{
  "projectName": "From SOW",
  "platforms": ["web-application", "mobile-app", "admin-panel"],
  "modules": [
    {
      "id": "kebab-case-id",
      "name": "Human Readable Name",
      "platform": "web-application",
      "description": "Module purpose",
      "features": ["feature-1", "feature-2"],
      "services": ["service-name"],
      "databases": ["PostgreSQL (purpose)"],
      "kafkaTopics": ["topic.name"],
      "websocketEvents": ["event.name"],
      "awsServices": ["S3", "Lambda"]
    }
  ]
}
```

### 3. Generate Documentation Structure

Create organized output:

```
workflows/
├── README.md                    # Main index
├── <platform>/
│   ├── timeline.md              # Development sequence
│   └── <module-id>/
│       ├── README.md            # Module overview
│       ├── user-flows/          # User journey scenarios
│       ├── technical-specs.md   # Architecture specs
│       ├── api-contracts.md     # API documentation
│       ├── database-schema.md   # Data models
│       ├── realtime-events.md   # Events (microservices)
│       ├── security-specs.md    # Security controls
│       ├── testing-strategy.md  # Test approach
│       ├── error-handling.md    # Error codes
│       └── features/            # BDD Gherkin files
│           └── <feature>.feature
```

## Available Presets

Select preset based on architecture:

| Preset | Use Case |
|--------|----------|
| `microservices` | NestJS microservices with Kafka, WebSocket, PostgreSQL |
| `monolith` | Single application with layered architecture |
| `serverless` | AWS Lambda, API Gateway, DynamoDB |
| `supabase` | Supabase backend with PostgreSQL, Auth, Storage |
| `firebase` | Firebase/Firestore with Cloud Functions |
| `nextjs-fullstack` | Next.js with App Router, Server Actions |
| `graphql-federation` | Apollo Federation with subgraphs |
| `kubernetes` | K8s deployments with Helm charts |
| `event-sourcing` | Event-sourced architecture with CQRS |

## SOW Analysis Prompt

Use this prompt to analyze SOW documents:

```
Analyze this Statement of Work (SOW) to extract structured module definitions.

For each module, extract:
- Module ID (kebab-case)
- Module name (title case)
- Description (1-2 sentences)
- Features list
- Technical components:
  * Backend services
  * Databases (type and purpose)
  * Message queues (Kafka/RabbitMQ topics)
  * Real-time events (WebSocket/SSE)
  * Cloud services (AWS/GCP/Azure)

Return ONLY valid JSON with structure:
{
  "projectName": "string",
  "platforms": ["string"],
  "modules": [{
    "id": "string",
    "name": "string",
    "platform": "string",
    "description": "string",
    "features": ["string"],
    "services": ["string"],
    "databases": ["string"],
    "kafkaTopics": ["string"],
    "websocketEvents": ["string"],
    "awsServices": ["string"]
  }]
}

Be comprehensive but don't invent features not in the SOW.
```

## Document Templates

Each preset generates specific documents. See `references/presets.md` for details.

### Common Documents (All Presets)
- **README.md** - Module overview with features
- **user-flows/** - User journey scenarios (split by feature)
- **technical-specs.md** - Architecture specifications
- **api-contracts.md** - REST/GraphQL API documentation
- **database-schema.md** - Data models and relationships
- **error-handling.md** - Error codes and handling

### Preset-Specific Documents
- **realtime-events.md** (microservices) - Kafka/WebSocket events
- **module-interactions.md** (monolith) - Internal module communication
- **event-sources.md** (serverless) - Lambda triggers
- **iam-policies.md** (serverless) - IAM roles and permissions

## Placeholder Pattern

Generated docs use placeholders for AI completion:

```markdown
[To be documented]
[API endpoints to be documented]
[Schema to be documented here]
```

Use the populate command to fill these with AI-generated content.

## Reference Files

- `references/presets.md` - Detailed preset configurations
- `references/sow-format.md` - SOW document format guide
- `references/templates.md` - Template customization guide
