---
description: "Rebuild .dt-workspace config from existing documentation. Scans output directory and reconstructs generatedPaths."
allowed-tools: ["Read", "Write", "Glob", "Bash"]
---

# Sync Configuration

Scan the output directory and rebuild `generatedPaths` in `.dt-workspace` config. Useful when:
- Config was lost or corrupted
- Documentation was manually reorganized
- Migrating from another setup

## Steps

### 1. Load Configuration

Read `.dt-workspace` config. If not found, create minimal config first.

### 2. Scan Output Directory

Scan `config.outputDirectory` (default: ./workflows) for:

```
<output>/
├── README.md
├── <platform-1>/
│   ├── timeline.md
│   └── <module-1>/
│       └── README.md
│   └── <module-2>/
│       └── README.md
├── <platform-2>/
│   └── ...
```

### 3. Detect Platforms

Find all directories in output that contain module subdirectories:
- Platform directories have `timeline.md` or module subdirectories
- Module directories have `README.md`

### 4. Extract Module Information

For each module directory:
1. Read `README.md` to extract module name
2. Use directory name as module ID
3. Record path relative to project root

### 5. Rebuild generatedPaths

```json
{
  "generatedPaths": {
    "platforms": {
      "<platform>": {
        "path": "./<output>/<platform>",
        "modules": [
          {
            "id": "<module-id>",
            "name": "<Module Name from README>",
            "path": "./<output>/<platform>/<module-id>"
          }
        ]
      }
    }
  }
}
```

### 6. Update Config

Write updated config to `.dt-workspace`:
- Preserve existing settings (projectName, sowPath, preset, etc.)
- Update generatedPaths
- Update lastGenerated timestamp

### 7. Display Summary

```
SYNC COMPLETE

Output Directory: <path>

Platforms Found: X
├── web-application (Y modules)
├── mobile-app (Z modules)
└── admin-panel (W modules)

Total Modules: N

Config updated: .dt-workspace
```

## Use Cases

1. **Lost config**: Recreate `.dt-workspace` from existing docs
2. **Manual changes**: After reorganizing documentation structure
3. **Migration**: After moving documentation to new location
4. **Verification**: Ensure config matches actual file structure
