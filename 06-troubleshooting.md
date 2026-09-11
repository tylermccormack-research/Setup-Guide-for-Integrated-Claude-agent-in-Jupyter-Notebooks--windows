# 6. Troubleshooting

## `NotImplementedError`

You probably still have the Windows subprocess problem.

Check that you:

1. Patched `_init_agent_subprocess`
2. Ran `py_compile`
3. Restarted JupyterLab

## `ClientSideConnection requires asyncio StreamWriter/StreamReader`

The simple `subprocess.Popen` workaround is not enough.

Use the **bridge patch** in this guide instead.

## Claude is not authenticated

Run:

```bash
claude /login
```

Then retry:

```text
@Claude say hello
```

## `claude-agent-acp` cannot be found

Use the absolute path in `claude.py`:

```python
executable = [r"C:\Users\YOUR_NAME\miniconda3\claude-agent-acp.cmd"]
```

## Check versions

```bash
jupyter lab --version
pip show jupyter-ai
pip show jupyter-ai-acp-client
pip show jupyter-ai-persona-manager
node --version
npm --version
claude-agent-acp --version
```

## Important

If something breaks after an update, compare your versions with the known-working setup in the README.
