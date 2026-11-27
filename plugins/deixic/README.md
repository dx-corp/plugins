# Deixic

Your Deixic workspace in Claude, Cursor, ChatGPT and Codex. The plugin adds
one remote MCP server, `https://app.deixic.com/mcp/workspace`, and the skills
and commands that use it.

## What you get

- The six tools Dex uses: `search`, `read`, `call`, `run`, `act` and
  `ask_human`. Each call runs with your own Deixic permissions, so a result
  shows what the matching Deixic page shows you.
- Skills: `security-compliance` (sends any question about the company's security
  or compliance to Deixic and Dex instead of answering from general knowledge),
  `security-questionnaire`, `change-check`, `use-deixic-tools`,
  `triage-failing-tests`, `fix-failing-test` and `answer-evidence-request`.
- Commands: `/deixic:failing`, `/deixic:fix <test>` and `/deixic:status`.

## Install

| Client | How |
| --- | --- |
| Claude Code | `claude plugin install deixic --marketplace dx-corp/plugins` |
| Cursor | Add the `dx-corp/plugins` repository as a plugin source, then install `deixic` |
| Codex | Add the `dx-corp/plugins` marketplace, then install `deixic` |
| Any MCP client | Add the server URL `https://app.deixic.com/mcp/workspace` |

## Sign in

No token goes in a config file. The first call opens Deixic sign-in in your
browser (OAuth with PKCE). You pick the organization and workspace there;
`read` with `{"read": "whoami"}` names the one this connection reads.

Sign-in grants `console:read`. Asking Dex needs `console:write` and a governed
change needs `platform:write`; your client asks you to re-authorize the first
time one is needed.

## Changes need a person

`act` previews a change and then submits the unchanged plan. A submit only
requests the change. A person approves it in Deixic, never from the agent.

## Files

- `.mcp.json`: the server, read by every client.
- `.claude-plugin/plugin.json`: Claude.
- `.cursor-plugin/plugin.json`: Cursor.
- `.codex-plugin/plugin.json`: ChatGPT and Codex.
- `skills/` and `commands/`: shared by all three.

Documentation: <https://www.deixic.com/docs>. Privacy:
<https://www.deixic.com/privacy>. Terms: <https://www.deixic.com/terms>.
