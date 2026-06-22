# wow-addon-trunk-configs

Shared [Trunk] plugin for McTalian's WoW addon repositories.

This plugin centralizes **linter versions, config files, and common ignore patterns** so each addon
repo doesn't need to maintain them independently. Simply source it in any addon's `.trunk/trunk.yaml`:

```yaml
plugins:
  sources:
    - id: trunk
      ref: v1.10.2
      uri: https://github.com/trunk-io/plugins
    - id: wbt-configs
      ref: v0.1.0
      uri: https://github.com/McTalian-WoW-Addons/wow-addon-trunk-configs
```

## What's included

- **Pinned linter versions** — actionlint, bandit, black, checkov, isort, markdownlint,
  osv-scanner, oxipng, pinact, prettier, ruff, shellcheck, shfmt, stylua, taplo,
  trufflehog, yamllint, and git-diff-check
- **Common ignore paths** — markdownlint in docs/instructions/prompts dirs, stylua in locale files
- **Exported configs** — `.markdownlint.yaml`, `.yamllint.yaml`, `stylua.toml`, `ruff.toml`,
  `.isort.cfg` — automatically available to all sourcing repos

Configs can be overridden per-repo by adding a file with the same name to `.trunk/configs/`.

## Releasing

Tag the repo to publish a new version of the plugin:

```bash
git tag v0.1.0 && git push origin v0.1.0
```

Update the `ref` in each addon repo's `trunk.yaml` to pick up the latest configs.

[Trunk]: https://docs.trunk.io
