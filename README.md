# claude-plugins

The official [Claude Code](https://docs.anthropic.com/claude/docs/claude-code) plugin marketplace catalog for the **AkaLab-Tech** organization.

This repository contains a single file ([`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json)) that lists every plugin AkaLab-Tech publishes. Each plugin lives in its own repository; this catalog just points users at them.

## Install

In a Claude Code session, register the marketplace once:

```
/plugin marketplace add AkaLab-Tech/claude-plugins
```

Then install whichever plugins you want:

```
/plugin install atelier@akalab-tech
/plugin install claude-roadmap-tools@akalab-tech
```

Subsequent additions to this catalog become available with `/plugin marketplace update akalab-tech`.

## Catalog

| Plugin | Repository | What it does |
| :--- | :--- | :--- |
| `atelier` | [AkaLab-Tech/atelier](https://github.com/AkaLab-Tech/atelier) | AI-operated workstation for autonomous software delivery |
| `claude-roadmap-tools` | [AkaLab-Tech/claude-roadmap-tools](https://github.com/AkaLab-Tech/claude-roadmap-tools) | `ROADMAP / IN_PROGRESS / HISTORY` tracking flow with `/create-roadmap` and `/migrate-roadmap` |
| `coolify-integration` | [AkaLab-Tech/coolify-integration](https://github.com/AkaLab-Tech/coolify-integration) | Coolify VPS deployment integration for atelier agents (validate, deploy, manage apps) |

## Add a new plugin to the catalog (maintainers)

1. Publish the plugin in its own repository under `AkaLab-Tech/<plugin-name>`, with a `.claude-plugin/plugin.json` manifest at its root. The plugin repository must **not** contain its own `.claude-plugin/marketplace.json` — this catalog is the single source of truth for the `akalab-tech` marketplace.
2. Open a PR against this repository adding a new entry to the `plugins` array in [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json):
   ```json
   {
     "name": "<plugin-name>",
     "source": {
       "source": "github",
       "repo": "AkaLab-Tech/<plugin-name>"
     },
     "description": "...",
     "homepage": "https://github.com/AkaLab-Tech/<plugin-name>",
     "repository": "https://github.com/AkaLab-Tech/<plugin-name>",
     "category": "...",
     "tags": ["..."]
   }
   ```
3. Run `claude plugin validate .` locally to confirm the manifest still parses.
4. After merge, users get the new plugin with `/plugin marketplace update akalab-tech` followed by `/plugin install <plugin-name>@akalab-tech`.

## Design rationale

A single shared marketplace per organization (rather than one marketplace per plugin) is the pattern recommended by the [Claude Code marketplace docs](https://code.claude.com/docs/en/plugin-marketplaces). It means:

- Users add one marketplace and get all current and future AkaLab-Tech plugins.
- Each plugin keeps its own repository, release cadence, and version history.
- Plugin entries reference their source repository remotely via the `github` source type, so this catalog stays a tiny JSON file with no plugin content of its own.

## License

MIT — see [LICENSE](LICENSE).
