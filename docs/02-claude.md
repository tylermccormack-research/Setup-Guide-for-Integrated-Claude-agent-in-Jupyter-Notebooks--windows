# 2. Install Claude ACP

Jupyter AI uses the **Agent Client Protocol (ACP)** to communicate with Claude.

## 1. Install Node.js

Check if you have Node.js installed with current release. In the anaconda prompt run:

```bash
node --version
```

I found node v26.8.1 works best, but as long as you have something similar it might be okay and you can move to next step.

If you don't have anything, you can install it here. Make sure to restart anaconda prompt installing.

https://nodejs.org/

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
