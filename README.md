# trunk-config

Shared Trunk configuration for projects in ~/Projects.

## Usage

### Adding to a new project

Initialize Trunk in your project if not already done:

```bash
trunk init
```

Then add this plugin to your `.trunk/trunk.yaml`:

```yaml
version: 0.1
cli:
  version: 1.22.8
plugins:
  sources:
    - id: trunk
      ref: v1.6.5
      uri: https://github.com/trunk-io/plugins
    - id: pke-config
      local: /home/pke/Projects/trunk-config
```

### For remote usage (after pushing to GitHub)

```yaml
plugins:
  sources:
    - id: trunk
      ref: v1.6.5
      uri: https://github.com/trunk-io/plugins
    - id: pke-config
      ref: v1.0.0
      uri: https://github.com/USERNAME/trunk-config
```

## What's Included

### Linters (enabled by default)

| Linter | Version | Purpose |
|--------|---------|---------|
| git-diff-check | latest | Checks for conflict markers and whitespace errors |
| markdownlint | 0.42.0 | Markdown style enforcement |
| prettier | 3.4.2 | Code formatting (JS, JSON, YAML, MD, etc.) |
| shellcheck | 0.10.0 | Shell script static analysis |
| shfmt | 3.6.0 | Shell script formatting |

### Exported Configs

- `.prettierrc` - Prettier configuration
- `.markdownlint.json` - Markdownlint rules
- `.editorconfig` - Editor settings

### Pre-commit Actions

- `trunk-check-pre-commit` - Run linters on staged files
- `trunk-fmt-pre-commit` - Auto-format staged files

## Overriding Defaults

### Project-level overrides

Add settings to your project's `.trunk/trunk.yaml`:

```yaml
lint:
  enabled:
    - biome@2.3.11  # Add project-specific linters
  disabled:
    - prettier      # Disable if using biome for formatting
```

### Config file overrides

Place your own config files in `.trunk/configs/` to override the shared ones:

```
.trunk/
  configs/
    .prettierrc  # This overrides the shared .prettierrc
```

## Updating

When changes are made to this repository:

1. If using local reference: Changes apply immediately
2. If using remote reference: Update the `ref` version tag and run `trunk upgrade`

## Creating a Release (for remote usage)

```bash
git add .
git commit -m "Update configuration"
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin main --tags
```
