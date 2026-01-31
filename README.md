# trunk-pke

Shared Trunk configuration for projects in ~/Projects.

## Usage

Initialize Trunk in your project:

```bash
trunk init
```

Add this plugin to `.trunk/trunk.yaml`:

```yaml
version: 0.1
cli:
  version: 1.25.0
plugins:
  sources:
    - id: trunk
      ref: v1.7.4
      uri: https://github.com/trunk-io/plugins
    - id: trunk-pke
      local: ../trunk-pke
```

## Included

### Linters

| Linter | Version | Purpose |
|--------|---------|---------|
| biome | 2.3.11 | JavaScript/TypeScript/JSON linting and formatting |
| git-diff-check | latest | Conflict markers and whitespace errors |
| markdownlint | 0.45.0 | Markdown style enforcement |
| shellcheck | 0.11.0 | Shell script static analysis |
| shfmt | 3.6.0 | Shell script formatting |

### Exported Configs

- `biome.json` - Biome formatter/linter (tabs, single quotes, LF)
- `.markdownlint.json` - Markdownlint rules
- `.editorconfig` - Editor settings

### Pre-commit Actions

- `trunk-check-pre-commit` - Lint staged files
- `trunk-fmt-pre-commit` - Format staged files

## Overriding

Add project-specific settings to `.trunk/trunk.yaml`:

```yaml
lint:
  enabled:
    - yamllint@1.38.0  # Add linters
  disabled:
    - markdownlint     # Disable linters
```

Changes to this plugin apply immediately to all projects using the local reference.
