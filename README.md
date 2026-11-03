# Deixic plugins

This repository is the public catalog for skills that ship with Deixic Code.
The repo-level catalog is `.agents/plugins/marketplace.json`. It lists the
software skills in `plugins/deixic-code-skills` and the legal workflow adapter
in `plugins/deixic-legal`.

Each skill is a reviewed instruction package with its own `SKILL.md` entrypoint.
The skills catalog excludes Deixic staff plugins, Session History, Product Kit,
and credentials. Installing a skills plugin grants no service access and adds
no authentication flow.

Validate a prepared catalog locally with:

```sh
node scripts/distribution-validation.mjs --name plugins --target .
```

The validator checks the repo catalog, plugin manifest, exact public skill
allowlist, frontmatter, paths, and license material. Add this repository through
the repo marketplace flow supported by your Codex client; the repository does
not include a custom installer.

## Legal workflows in Deixic Code

`deixic-legal` adapts Anthropic's Apache-2.0 `claude-for-legal` source at
commit `4a6c651889c97cc9140580363c73e0eb17379c2b`. Its `legal-workflows`
skill reads the packaged practice procedures and prepares drafts for attorney
review. It covers commercial, privacy, product, corporate, employment,
regulatory, AI governance, litigation, IP, law-student, and legal-clinic work.

After this package has been published to this repository, clone the catalog,
inspect the package, and install its local directory:

```sh
git clone https://github.com/dx-corp/plugins.git deixic-plugins
cat deixic-plugins/plugins/deixic-legal/.plugin/plugin.json
cat deixic-plugins/plugins/deixic-legal/skills/legal-workflows/upstream/upstream.toml
deixic-code plugins install "$PWD/deixic-plugins/plugins/deixic-legal"
deixic-code plugins info deixic-legal --json
```

The native Deixic Code installer accepts a local plugin directory or a whole
Git repository. Use the local directory shown here for this multi-plugin
repository. The `.agents` marketplace is also available to compatible Codex
clients; Deixic Code's built-in marketplace is a separate catalog.

Start a new Deixic Code session and request the `legal-workflows` skill with a
specific task and the approved workspace playbook. Preserve citations and
jurisdiction assumptions, and have a qualified attorney verify legal work
product before it is sent, filed, or relied on. Deixic supplies the adapter and
credits Anthropic for the upstream procedures.

The package retains upstream source files under the skill's `upstream/`
directory. Connector configurations, hooks, scripts, community installers,
CoCounsel examples, and managed-agent cookbooks there are inspection resources.
The plugin registers only the `legal-workflows` skill. An unavailable connector,
research subscription, scheduler, or editing tool remains an explicit limit.
Local plugin state records the installed package's integrity; replacing files
in the clone does not update the installed copy.

## Deixic for Claude Code

The `deixic` plugin connects Claude Code to your Deixic workspace through the Deixic MCP server at `https://app.deixic.com/mcp/workspace`. It reads tests with their per-resource results, controls, frameworks, vendors, risks, policies and evidence as you, with the access you have in Deixic. The first tool call opens a browser for Deixic sign-in, so you never copy a token.

```
/plugin install deixic --marketplace dx-corp/plugins
```

Commands: `/deixic:failing`, `/deixic:fix <test>`, `/deixic:status`. Skills: triage failing tests, fix a failing test with a pull request in your repository, and answer an auditor evidence request.

To use the server without the plugin:

```
claude mcp add --transport http deixic https://app.deixic.com/mcp/workspace
```
