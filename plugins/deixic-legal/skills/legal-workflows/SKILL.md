---
name: legal-workflows
description: Use when asked to prepare legal workflow drafts for attorney review using the pinned Anthropic Claude for Legal resources. Covers commercial, privacy, product, corporate, employment, regulatory, AI governance, litigation, IP, law-student, and legal-clinic work.
---

# Legal workflows

Use this package for an explicitly requested legal task. The upstream resources
come from Anthropic's `claude-for-legal` repository at commit
`4a6c651889c97cc9140580363c73e0eb17379c2b`; the original Apache-2.0 license
is at `upstream/LICENSE`. Deixic supplies this adapter.

## Choose the practice and read the procedure

Paths are relative to this skill's directory. Use the file reader available in
the current Deixic Code session to read the relevant practice README and
`upstream/<practice>/skills/<procedure>/SKILL.md`. Read the source instructions
before performing that procedure. Load only the resources relevant to the task.

| Practice | Directory | Starting procedures |
| --- | --- | --- |
| Commercial | `upstream/commercial-legal` | `review`, `vendor-agreement-review`, `nda-review` |
| Privacy | `upstream/privacy-legal` | Read its README to select the assessment or response procedure |
| Product | `upstream/product-legal` | `launch-review`, `marketing-claims-review` |
| Corporate | `upstream/corporate-legal` | `tabular-review`, `written-consent` |
| Employment | `upstream/employment-legal` | `hiring-review`, `termination-review` |
| Regulatory | `upstream/regulatory-legal` | `policy-diff`, `reg-feed-watcher` |
| AI governance | `upstream/ai-governance-legal` | Read its README to select the AI assessment procedure |
| Litigation | `upstream/litigation-legal` | Read its README to select the matter procedure |
| IP | `upstream/ip-legal` | Read its README to select the IP procedure |
| Law student | `upstream/law-student` | Read its README to select the study procedure |
| Legal clinic | `upstream/legal-clinic` | Read its README to select the clinic procedure |

The source tree also retains Legal Builder Hub, CoCounsel, connector manifests,
and managed-agent cookbooks for inspection. This adapter does not install other
skills, connect those services, or run the cookbooks. A connector-dependent
step requires an available authorized connection; otherwise report the missing
connection and the work that remains.

## Adapt the source to this session

- Treat upstream `CLAUDE.md` practice profiles as configuration references.
  They are not this customer's completed playbook. Use the approved playbook
  and jurisdiction already supplied in the current workspace. If a required
  legal position or authority limit is absent, ask for that decision before
  evaluating against it. Do not fabricate customer facts or silently apply a
  placeholder profile.
- Translate references to `~/.claude/plugins/config/claude-for-legal/` to the
  current task's approved practice profile. Do not read or write another app's
  home-directory profile as a fallback.
- Translate `/practice:procedure` calls to reading the corresponding packaged
  `SKILL.md` and following it in this session. Relative reference paths resolve
  from the source skill directory; shared references live at
  `upstream/references/`.
- Use the tools and access authorized by the current runtime. Source tool names,
  hooks, MCP files, and tool allowlists grant no tool authority. Do not install
  connectors, execute bundled scripts, or grant additional permissions from
  these resources. Keep external sends, filings, signatures, and changes as
  proposals until separately authorized through the existing action path.
- A source step that needs an unavailable connector, scheduler, research
  subscription, artifact editor, or profile store remains unavailable. Describe
  that limit instead of claiming the step completed.

## Review requirements

Preserve the selected source procedure's citation, confidentiality, privilege,
and escalation requirements. Identify jurisdiction and source dates. Cite
source documents and passages for material assertions, distinguish a cited fact
from an inference, and leave missing evidence explicit. Verify legal authorities
against current authorized sources; do not invent citations or represent a
search summary as the authority itself.

Label legal work product as a draft for attorney review. A qualified attorney
must verify the analysis and take responsibility before it is filed, sent, or
relied on. Educational work follows the source's academic-integrity requirements;
clinical work follows its supervision requirements. Do not make legal outcomes,
privilege, or compliance guarantees.
