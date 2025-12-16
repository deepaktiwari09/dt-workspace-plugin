---
description: "Fill documentation placeholders with AI-generated content. Completes [To be documented] sections in generated files."
argument-hint: "[--platform <platform>] [--module <module>]"
allowed-tools: ["Read", "Write", "Glob", "Grep"]
---

# Populate Documentation Placeholders

Fill `[To be documented]` placeholders in generated documentation with detailed, context-aware content.

## Prerequisites

- `.dt-workspace` config with `generatedPaths`
- Generated documentation (run `/dt-workspace:scaffold` first)

## Steps

### 1. Load Configuration

Read `.dt-workspace` and validate `generatedPaths.platforms` exists.

### 2. Select Target

If arguments provided, use them. Otherwise, use AskUserQuestion:

1. **Select Platform**: List available platforms from config
2. **Select Module**: List modules in selected platform
3. **Select Files**: Checkbox for which files to complete:
   - user-flows/*.md
   - technical-specs.md
   - api-contracts.md
   - database-schema.md
   - realtime-events.md (if exists)
   - security-specs.md
   - error-handling.md

### 3. Read Context

For each selected file:
1. Read SOW file (config.sowPath)
2. Read module README.md for context
3. Read current file content

### 4. Detect Placeholders

Look for patterns:
- `[To be documented]`
- `[...to be documented...]`
- `[...to be filled...]`
- Any `[text]` indicating incomplete content (not markdown links)

### 5. Fill Placeholders

For each file with placeholders:

1. **Create backup**: `<file>.backup`
2. **Generate content**: Replace placeholders with detailed content based on:
   - SOW requirements
   - Module context (features, services, databases)
   - File type (API contracts need endpoints, database-schema needs tables)
   - Preset patterns
3. **Write updated file**

### 6. Display Summary

```
COMPLETION SUMMARY

Platform: <platform>
Module: <module>

✓ Processed: X files
○ Skipped: Y files (no placeholders)
✗ Errors: Z files

Backup files created with .backup extension
Module location: <path>

Next steps:
1. Review completed documentation
2. Remove .backup files if satisfied
3. Commit changes
```

## Placeholder Filling Guidelines

### API Contracts
- Generate realistic REST endpoints
- Include request/response schemas
- Add authentication requirements
- Document error responses

### Database Schema
- Create table definitions with columns
- Add relationships and foreign keys
- Include indexes and constraints
- Document migrations

### Technical Specs
- Architecture diagrams (mermaid)
- Service interactions
- Data flow descriptions
- Technology choices

### User Flows
- Step-by-step user journeys
- Decision points
- Error scenarios
- Success criteria
