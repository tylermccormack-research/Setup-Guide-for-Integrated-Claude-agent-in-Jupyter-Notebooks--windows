# Known Working Versions

This is the configuration that was successfully tested.

| Component | Version |
|---|---:|
| JupyterLab | 4.6.3 |
| jupyter-ai | 3.2.0 |
| jupyter-ai-acp-client | 0.3.0 |
| jupyter-ai-persona-manager | 0.2.0 |
| Node.js | 26.8.1 |
| npm | 12.0.2 |
| @agentclientprotocol/claude-agent-acp | 0.75.1 |

## Important

The Windows bridge came from the `win32-pipe-fix-2` development branch, but **only `_init_agent_subprocess` was transplanted**.

The entire old branch should not replace the current `jupyter-ai-acp-client` installation.
