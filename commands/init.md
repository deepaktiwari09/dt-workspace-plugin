---
description: "Initialize dt-workspace project configuration. Creates .dt-workspace config file with project settings."
argument-hint: "[project-name]"
allowed-tools: ["Read", "Write", "Glob", "Bash"]
---

# Initialize DT-Workspace Project

Initialize a new dt-workspace configuration for documentation generation.

## Steps

1. **Check for existing config**: Look for `.dt-workspace` file in current directory
2. **If exists**: Ask user if they want to overwrite
3. **Gather information** using AskUserQuestion:
   - Project name (default: directory name or argument)
   - SOW file path (default: ./sow.md)
   - Preset selection (microservices/monolith/serverless/supabase/firebase/nextjs-fullstack/graphql-federation/kubernetes/event-sourcing)
   - Output directory (default: ./workflows)

4. **Create .dt-workspace file**:
```json
{
  "version": "1.0.0",
  "projectName": "<from user>",
  "sowPath": "<from user>",
  "defaultPreset": "<from user>",
  "outputDirectory": "<from user>",
  "generatedAt": "<ISO timestamp>",
  "generatedPaths": {
    "platforms": {}
  }
}
```

5. **Verify SOW file exists**: Check if sowPath file exists, warn if not

6. **Display summary**:
   - Configuration created
   - Next steps: ensure SOW file exists, run scaffold command

## Output Format

```
DT-WORKSPACE INITIALIZED

Configuration: .dt-workspace
Project: <name>
SOW Path: <path>
Preset: <preset>
Output: <directory>

Next steps:
1. Ensure SOW file exists at <sowPath>
2. Run /dt-workspace:scaffold to generate documentation
```
