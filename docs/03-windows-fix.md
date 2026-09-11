# 3. Fix the Windows ACP Bug

## What is happening?

Windows + Jupyter's event loop can prevent the ACP client from creating the subprocess pipes it needs.

The symptom is usually:

```text
NotImplementedError
```

around:

```text
asyncio.create_subprocess_exec()
```

## Do NOT do this

Do **not** install the old `win32-pipe-fix-2` branch as the whole package.

It is based on an older `jupyter-ai-acp-client` release and conflicts with current Jupyter AI.

## Step 1 — Back up the file

```bash
copy "C:\Users\YOUR_NAME\miniconda3\Lib\site-packages\jupyter_ai_acp_client\base_acp_persona.py" "C:\Users\YOUR_NAME\miniconda3\Lib\site-packages\jupyter_ai_acp_client\base_acp_persona_BACKUP.py"
```

Replace `YOUR_NAME` with your Windows username.

## Step 2 — Install the Windows bridge fix

Run this as **one command**:

```bash
python -c "import urllib.request; url='https://raw.githubusercontent.com/himi/jupyter-ai-acp-client/win32-pipe-fix-2/jupyter_ai_acp_client/base_acp_persona.py'; remote=urllib.request.urlopen(url).read().decode(); start=remote.index('    async def _init_agent_subprocess('); end=remote.index('    @auto_emit_event("acp_server_init")',start); method=remote[start:end]; p=r'C:\Users\YOUR_NAME\miniconda3\Lib\site-packages\jupyter_ai_acp_client\base_acp_persona.py'; local=open(p,encoding='utf-8').read(); lstart=local.index('    async def _init_agent_subprocess('); lend=local.index('    @auto_emit_event("acp_server_init")',lstart); open(p,'w',encoding='utf-8').write(local[:lstart]+method+local[lend:]); print('Windows ACP bridge installed.')"
```

Again, replace `YOUR_NAME`.

You should see:

```text
Windows ACP bridge installed.
```

## Step 3 — Check Python syntax

```bash
python -m py_compile "C:\Users\YOUR_NAME\miniconda3\Lib\site-packages\jupyter_ai_acp_client\base_acp_persona.py"
```

**No output = success.**

## Step 4 — Point Claude to the Windows `.cmd`

Open:

```text
C:\Users\YOUR_NAME\miniconda3\Lib\site-packages\jupyter_ai_acp_client\acp_personas\claude.py
```

Find:

```python
executable = ["claude-agent-acp"]
```

Change it to:

```python
executable = [r"C:\Users\YOUR_NAME\miniconda3\claude-agent-acp.cmd"]
```

Save the file.

## Step 5 — Restart JupyterLab

Close JupyterLab completely.

Then:

```bash
jupyter lab
```

Try:

```text
@Claude say hello
```

If the Windows error is gone but Claude says you are not authenticated, **the fix worked**. Continue to authentication.
