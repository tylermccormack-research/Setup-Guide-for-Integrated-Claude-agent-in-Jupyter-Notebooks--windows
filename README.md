# Jupyter AI + Claude Code on Windows

A short, reproducible guide for running **Claude Code through Jupyter AI in JupyterLab on Windows**.

> **Goal:** Get `@Claude` working inside JupyterLab.

## Working setup

| Package | Version |
|---|---:|
| Windows | Windows 11 |
| JupyterLab | 4.6.3 |
| jupyter-ai | 3.2.0 |
| jupyter-ai-acp-client | 0.3.0 |
| jupyter-ai-persona-manager | 0.2.0 |
| Node.js | 26.8.1 |
| npm | 12.0.2 |
| Claude Agent ACP | 0.75.1 |

## Contents

1. [Install Jupyter AI](01-installation.md)
2. [Install Claude ACP](02-claude.md)
3. [Fix the Windows ACP bug](03-windows-fix.md)
4. [Authenticate Claude](04-authentication.md)
5. [Test it](05-test.md)
6. [Troubleshooting](06-troubleshooting.md)

## The important part

On Windows, the current ACP client can hit a subprocess/asyncio pipe problem.

**Do not install the old `win32-pipe-fix-2` branch wholesale.**

Instead:

- Keep `jupyter-ai-acp-client` **0.3.0**
- Patch only `_init_agent_subprocess`
- Point Claude at the `.cmd` executable

That is the combination that worked.

## Official links

- [Jupyter AI](https://jupyter-ai.readthedocs.io/en/latest/getting-started.html)
- [Agent Client Protocol](https://github.com/agentclientprotocol/)
- [Claude Agent ACP](https://github.com/agentclientprotocol/claude-agent-acp)
- [Claude authentication](https://code.claude.com/docs/en/authentication)
- [Node.js](https://nodejs.org/)
- [Windows ACP fix branch](https://github.com/himi/jupyter-ai-acp-client/tree/win32-pipe-fix-2)
