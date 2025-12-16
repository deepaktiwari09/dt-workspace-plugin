---
description: "Generate workflow documentation from SOW file. Creates organized project documentation with BDD features, API specs, database schemas."
argument-hint: "[sow-file] [--preset <preset>]"
allowed-tools: ["Read", "Write", "Glob", "Bash", "Grep"]
---

# Scaffold Workflow Documentation

Generate comprehensive workflow documentation from a Statement of Work (SOW) document.

## Prerequisites

- `.dt-workspace` config file must exist (run `/dt-workspace:init` first)
- SOW markdown file must exist

## Steps

### 1. Load Configuration

Read `.dt-workspace` config file. If not found, instruct user to run init first.

### 2. Determine Settings

- SOW file: argument > config.sowPath
- Preset: --preset argument > config.defaultPreset > "microservices"
- Output: config.outputDirectory > "./workflows"

### 3. Read and Analyze SOW

Read the SOW file and extract structured module definitions:

```json
{
  "projectName": "From SOW",
  "platforms": ["web-application", "mobile-app"],
  "modules": [
    {
      "id": "module-id",
      "name": "Module Name",
      "platform": "web-application",
      "description": "Description",
      "features": ["feature-1", "feature-2"],
      "services": ["service-name"],
      "databases": ["PostgreSQL"],
      "kafkaTopics": ["topic.name"],
      "websocketEvents": ["event.name"],
      "awsServices": ["S3"]
    }
  ]
}
```

### 4. Generate Documentation Structure

For each platform and module, create:

```
<output>/
├── README.md                    # Main index with all modules
├── <platform>/
│   ├── timeline.md              # Platform development timeline
│   └── <module-id>/
│       ├── README.md            # Module overview
│       ├── user-flows/          # User journey scenarios
│       │   ├── index.md
│       │   └── <feature>.md
│       ├── technical-specs.md
│       ├── api-contracts.md
│       ├── database-schema.md
│       ├── [preset-specific].md # realtime-events, etc.
│       ├── security-specs.md
│       ├── testing-strategy.md
│       ├── error-handling.md
│       └── features/
│           └── <feature>.feature
```

### 5. Generate Content

For each document, generate content based on preset templates with placeholders:
- Use `[To be documented]` for sections needing AI completion
- Include module context (features, services, databases)
- Follow preset-specific patterns

### 6. Update Config

Update `.dt-workspace` with generated paths:

```json
{
  "lastGenerated": "<ISO timestamp>",
  "generatedPaths": {
    "platforms": {
      "web-application": {
        "path": "./workflows/web-application",
        "modules": [
          {"id": "module-id", "name": "Module Name", "path": "./workflows/web-application/module-id"}
        ]
      }
    }
  }
}
```

### 7. Display Summary

```
GENERATION COMPLETE

Project: <name>
Preset: <preset>
Location: <output>

Modules: X
Files: Y
Directories: Z

Next steps:
1. Review generated files
2. Run /dt-workspace:populate to fill placeholders
3. Update BDD scenarios with specific test cases
```

## Preset Templates

Based on selected preset, generate appropriate documents. See skill references for preset details.
