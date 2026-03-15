
# 📖 OpenClaw Skill: Claude Engineer Bridge

An advanced, autonomous orchestration layer for **OpenClaw** that leverages **Claude Code** (Anthropic's CLI) as its primary engineering engine.

This skill transforms your OpenClaw agent into a **Senior Full-Stack AI Engineer** capable of building, debugging, and deploying web applications and Agent-to-Agent (A2A) APIs while you are away from your terminal.

---

## 🚀 Capabilities

| Feature | Description |
| --- | --- |
| **Autonomous Scaffolding** | Initialize repositories, git environments, and boilerplate stacks (React, FastAPI, etc.) |
| **Deep Debugging** | Multi-file analysis and automated test-driven bug fixing using Claude Code's native reasoning. |
| **A2A Architecture** | Specifically designed to build web apps and APIs that *other* OpenClaw agents can interact with. |
| **MCP Management** | Commands to install/configure Model Context Protocol servers for expanded tool access. |
| **CI/CD Integration** | Automated commits, PR descriptions, and deployment triggers. |

---

## 🛠 Prerequisites

Before installing this skill, ensure your environment is set up:

1. **OpenClaw** (v2.0+) installed and running.
2. **Claude Code CLI** installed:
```bash
curl -fsSL https://claude.ai/install.sh | bash

```


3. **Authentication:** Ensure you have run `claude login` and are successfully authenticated on the host machine.

---

## 📦 Installation

1. **Clone this repository** into your OpenClaw skills directory:
```bash
mkdir -p ~/.openclaw/skills/claude-engineer
git clone https://github.com/YOUR_USERNAME/openclaw-claude-engineer.git ~/.openclaw/skills/claude-engineer

```


2. **Enable the Skill** in your `~/.openclaw/openclaw.json`:
```json
"skills": {
  "entries": {
    "claude-engineer": { "enabled": true }
  }
}

```


3. **Restart your Gateway:**
```bash
openclaw gateway restart

```



---

## 🤖 Usage Scenarios

You can trigger this skill via your OpenClaw interface (Telegram, WhatsApp, or CLI):

### 1. Building an Agent-Friendly Web App

> *"Hey, use Claude Code to build a FastAPI service for my grocery list. Make sure it has a Swagger UI so my other agents can read and write to it."*

### 2. Deep Debugging

> *"I'm getting a 500 error on the /auth endpoint. Have Claude Code find the bug, fix it, and verify with a curl test."*

### 3. Documentation & Review

> *"Analyze the current repo, generate a README.md and ARCHITECTURE.md, and then do a security audit of the environment variables."*

---

## 🛡 Security & Safety

* **Non-Interactive Mode:** This skill utilizes the `--yes` flag for efficiency. It is recommended to run OpenClaw in a **sandboxed environment** or a dedicated VPS.
* **Read-Only First:** For complex refactors, the skill is programmed to run an initial `--read-only` scan to explain its plan before modifying files.
* **Recursive Protection:** The agent will pause and request manual intervention if Claude Code fails to resolve a loop within 3 attempts.

---

## 🤝 Contributing

In 2026, the best skills are community-driven! If you have optimized the prompt logic for specific frameworks or better MCP handling, please:

1. Fork the repo.
2. Create your feature branch.
3. Submit a Pull Request.

---

## 📄 License

MIT License - Feel free to use and modify for your own autonomous workflows.

