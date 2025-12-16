---
description: "Export built-in templates for customization. Creates .dt-templates directory with Handlebars templates."
argument-hint: "[--preset <preset>]"
allowed-tools: ["Read", "Write", "Bash", "Glob"]
---

# Export Templates

Export built-in Handlebars templates to `.dt-templates/` for customization.

## Steps

### 1. Select Preset

If --preset argument provided, use it. Otherwise, use AskUserQuestion:
- microservices
- monolith
- serverless
- supabase
- firebase
- nextjs-fullstack
- graphql-federation
- kubernetes
- event-sourcing
- all (export all presets)

### 2. Check Existing Templates

Check if `.dt-templates/<preset>/` exists:
- If exists, ask for confirmation to overwrite
- If --force flag, skip confirmation

### 3. Create Template Directory

```bash
mkdir -p .dt-templates/<preset>
```

### 4. Generate Template Files

Create Handlebars templates for the preset. Each preset needs:

**template.config.json**:
```json
{
  "preset": "<preset>",
  "description": "Preset description",
  "documentTypes": [...],
  "platformDocumentTypes": [...],
  "featureTemplate": "feature-file.hbs",
  "mainReadmeTemplate": "main-readme.hbs"
}
```

**Common templates**:
- module-readme.hbs
- user-flows-index.hbs
- user-flows-single.hbs
- technical-specs.hbs
- api-contracts.hbs
- database-schema.hbs
- security-specs.hbs
- testing-strategy.hbs
- error-handling.hbs
- feature-file.hbs
- main-readme.hbs
- platform-timeline.hbs

**Preset-specific templates**:
- realtime-events.hbs (microservices)
- module-interactions.hbs (monolith)
- event-sources.hbs, iam-policies.hbs (serverless)
- etc.

### 5. Display Summary

```
TEMPLATES EXPORTED

Location: .dt-templates/<preset>/
Files: X templates

Template files:
- template.config.json
- module-readme.hbs
- api-contracts.hbs
- ...

Usage:
1. Edit templates in .dt-templates/<preset>/
2. Run /dt-workspace:scaffold - custom templates auto-used
3. Only override templates you need to change
```

## Template Customization

Templates use Handlebars syntax with variables:
- `{{module.id}}`, `{{module.name}}`, `{{module.description}}`
- `{{module.features}}`, `{{module.services}}`, `{{module.databases}}`
- `{{preset}}`, `{{projectName}}`

Helpers:
- `{{capitalize text}}` - kebab-case to Title Case
- `{{add index 1}}` - arithmetic
- `{{#if}}`, `{{#each}}`, `{{#eq}}` - conditionals
