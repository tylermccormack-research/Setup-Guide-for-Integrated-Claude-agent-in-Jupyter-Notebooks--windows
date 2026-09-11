# 4. Authenticate Claude

If Jupyter AI says:

```text
You're not authenticated with Claude.
```

That's good news: the Jupyter → ACP → Claude connection is working.

## 1. Open a new Anaconda Prompt

Run:

```bash
claude /login
```

## 2. Finish the browser login

Follow the prompts.

## 3. Return to JupyterLab

Try:

```text
@Claude say hello
```

You should get a Claude response.
