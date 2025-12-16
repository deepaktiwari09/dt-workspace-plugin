---
description: "Delete generated documentation and reset config. Removes output directory and clears generatedPaths."
argument-hint: "[--force]"
allowed-tools: ["Read", "Write", "Bash", "Glob"]
---

# Clean Generated Documentation

Delete all generated documentation and reset the configuration.

## Steps

### 1. Load Configuration

Read `.dt-workspace` config to get output directory and generated paths.

### 2. Show What Will Be Deleted

Display summary of what will be removed:
```
Files to be deleted:
- <output>/README.md
- <output>/web-application/ (X modules, Y files)
- <output>/mobile-app/ (Z modules, W files)

Total: N files in M directories
```

### 3. Confirm Deletion

Unless --force flag is provided, ask for confirmation:
- "This will permanently delete all generated documentation. Continue? (y/N)"

### 4. Delete Files

Remove the output directory and all contents:
```bash
rm -rf <outputDirectory>
```

### 5. Update Configuration

Reset generatedPaths in `.dt-workspace`:
```json
{
  "generatedPaths": {
    "platforms": {}
  },
  "lastGenerated": null
}
```

### 6. Display Summary

```
CLEAN COMPLETE

Deleted: <output>/
Files removed: X
Directories removed: Y

Config updated: .dt-workspace
- generatedPaths cleared
- lastGenerated reset

To regenerate:
1. Ensure SOW file exists
2. Run /dt-workspace:scaffold
```

## Safety Features

- Requires explicit confirmation (unless --force)
- Only deletes configured output directory
- Preserves .dt-workspace config file
- Preserves .dt-templates custom templates
- Preserves SOW file

## Use Cases

1. **Fresh start**: Regenerate all documentation from scratch
2. **Preset change**: Clean before switching to different preset
3. **SOW update**: After major SOW changes, regenerate everything
4. **Cleanup**: Remove generated docs from version control
