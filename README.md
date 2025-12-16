# DT-Workspace Plugin

AI-powered workflow documentation generator for Claude Code. Generate comprehensive project documentation from Statement of Work (SOW) documents.

## Features

- **SOW Analysis**: Extract structured module definitions from requirements documents
- **Multi-Preset Support**: 9 architecture presets (microservices, serverless, monolith, etc.)
- **Complete Documentation**: API contracts, database schemas, BDD features, and more
- **AI Completion**: Fill documentation placeholders with context-aware content
- **ER Diagrams**: Generate entity-relationship diagrams in multiple formats

## Installation

### Option 1: Plugin Directory
```bash
claude --plugin-dir /path/to/dt-workspace-plugin
```

### Option 2: Copy to Project
```bash
cp -r dt-workspace-plugin/.claude-plugin your-project/
```

## Commands

| Command | Description |
|---------|-------------|
| `/dt-workspace:init` | Initialize project configuration |
| `/dt-workspace:scaffold` | Generate documentation from SOW |
| `/dt-workspace:populate` | Fill placeholders with AI content |
| `/dt-workspace:export` | Export templates for customization |
| `/dt-workspace:sync` | Rebuild config from filesystem |
| `/dt-workspace:diagram` | Generate ER diagrams |
| `/dt-workspace:clean` | Delete generated documentation |
| `/dt-workspace:presets` | List available presets |

## Quick Start

1. **Initialize project**:
   ```
   /dt-workspace:init
   ```

2. **Create SOW file** (`sow.md`) with your requirements

3. **Generate documentation**:
   ```
   /dt-workspace:scaffold
   ```

4. **Complete placeholders**:
   ```
   /dt-workspace:populate
   ```

## Available Presets

| Preset | Architecture |
|--------|--------------|
| `microservices` | NestJS with Kafka, WebSocket, PostgreSQL |
| `monolith` | Layered architecture, shared database |
| `serverless` | AWS Lambda, API Gateway, DynamoDB |
| `supabase` | Supabase with PostgreSQL, Auth, Storage |
| `firebase` | Firebase/Firestore, Cloud Functions |
| `nextjs-fullstack` | Next.js App Router, Server Components |
| `graphql-federation` | Apollo Federation with subgraphs |
| `kubernetes` | K8s deployments, Helm charts |
| `event-sourcing` | CQRS with event store |

## Generated Structure

```
workflows/
├── README.md                    # Project index
├── <platform>/
│   ├── timeline.md              # Development sequence
│   └── <module>/
│       ├── README.md            # Module overview
│       ├── user-flows/          # User journeys
│       ├── technical-specs.md   # Architecture
│       ├── api-contracts.md     # API documentation
│       ├── database-schema.md   # Data models
│       ├── security-specs.md    # Security controls
│       ├── error-handling.md    # Error codes
│       └── features/            # BDD Gherkin files
```

## Configuration

The `.dt-workspace` config file:

```json
{
  "version": "1.0.0",
  "projectName": "My Project",
  "sowPath": "./sow.md",
  "defaultPreset": "microservices",
  "outputDirectory": "./workflows",
  "generatedPaths": {
    "platforms": {}
  }
}
```

## Template Customization

Export and customize templates:

```
/dt-workspace:export --preset microservices
```

Templates saved to `.dt-templates/<preset>/` for editing.

## Agents

- **sow-analyzer**: Analyzes SOW documents and extracts modules
- **doc-completer**: Fills documentation placeholders with detailed content

## Author

Deepak Tiwari <deepaktiwari3020@gmail.com>

## License

MIT
