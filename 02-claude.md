# 2. Install Claude ACP

Jupyter AI uses the **Agent Client Protocol (ACP)** to communicate with Claude.

## 1. Install Node.js

Install the current Node.js release:

https://nodejs.org/

Then restart Anaconda Prompt.

## 2. Install Claude Agent ACP

```bash
npm install -g @agentclientprotocol/claude-agent-acp
```

## 3. Check it

```bash
claude-agent-acp --version
```

You should get a version number.

## 4. Start JupyterLab

```bash
jupyter lab
```

Try:

```text
@Claude say hello
```

If you get a Windows `NotImplementedError` involving `asyncio.create_subprocess_exec`, continue to the next page.
