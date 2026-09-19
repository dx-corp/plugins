# Deixic plugins

This repository is the public catalog for skills that ship with Deixic Code.
The repo-level catalog is `.agents/plugins/marketplace.json`; its current plugin
is `plugins/deixic-code-skills`.

Each skill is a reviewed instruction package with its own `SKILL.md` entrypoint.
The catalog does not include Deixic staff plugins, Session History, Product Kit,
credentials, hooks, MCP servers, or applications. Installing the plugin grants
no service access and adds no authentication flow.

Validate a prepared catalog locally with:

```sh
node scripts/distribution-validation.mjs --name plugins --target .
```

The validator checks the repo catalog, plugin manifest, exact public skill
allowlist, frontmatter, paths, and license material. Add this repository through
the repo marketplace flow supported by your Codex client; the repository does
not include a custom installer.
