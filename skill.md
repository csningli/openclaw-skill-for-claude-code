
---
name: claude-engineer
description: "Directs Claude Code CLI to perform expert-level engineering: repo creation, debugging, app building, and documentation."
metadata:
  version: "2.1.0"
  author: "Gemini-Assistant"
  capabilities: ["mcp-integration", "web-app-deployment", "autonomous-coding"]
---

# Core Objective
Act as a Senior AI Architect by delegating all heavy-duty coding, system design, and environment configuration to the Claude Code CLI.

# 1. Setup & Environment Rules
Before any coding task, ensure the "Tools of the Trade" are ready.
- **Install Claude Code:** If missing, run `curl -fsSL https://claude.ai/install.sh | bash`.
- **MCP Integration:** When external data is needed (e.g., Google Search, GitHub, Slack), check `claude mcp list`. If a tool is missing, use `claude mcp add [server-name]`.
- **Plugins:** For specialized logic (e.g., SEO, Frontend), use `/plugin install [plugin-name]`.

# 2. Scenario-Specific Workflows

### A. New Project & Repo Creation
- **Rule:** Never start in a messy directory. 
- **Action:** 1. `mkdir [project-name] && cd [project-name]`
  2. `git init`
  3. `claude "Initialize a [Framework] project with [Stack] and set up a basic Hello World." --yes`

### B. Extracting Implementation Ideas (Reverse Engineering)
- **Rule:** Read before you write.
- **Action:** `claude "Analyze the current architecture and summarize the logic in ARCHITECTURE.md. Do not change code." --read-only`

### C. Expert Debugging
- **Rule:** Use a "Trace-First" approach.
- **Action:** `claude "Analyze the following error log: [paste_log]. Find the root cause across the codebase, fix it, and run tests to verify." --yes`

### D. Code Review & Documentation
- **Rule:** Quality is non-negotiable.
- **Action:** - **Review:** `claude "Review the last commit for security vulnerabilities and performance bottlenecks."`
  - **Docs:** `claude "Generate JSDoc/Docstrings for all functions in /src and update README.md." --yes`

# 3. Building "Agent-Accessible" Web Apps
This is a high-priority scenario. When building apps intended for use by *other* OpenClaw agents:
- **API First:** Claude must prioritize REST or GraphQL endpoints over complex UIs.
- **Self-Documenting:** Every app must include a `/docs` or `openapi.json` so other agents can "read" how to use the app.
- **Standardized Output:** Instruct Claude to ensure all API responses are valid JSON.
- **Deployment:** Use `claude "Build the web app and deploy it to [Vercel/Netlify/Docker]. Ensure the URL is outputted clearly." --yes`

# 4. Version Control (Git)
- **Rule:** Small, semantic commits.
- **Action:** After every successful task, run `claude "Commit these changes with a conventional commit message." --yes`

# 5. Operational Constraints
- **Recursive Limit:** Stop and ask the user if Claude Code fails to solve a bug after 3 attempts.
- **Confirmation:** Use the `--yes` flag only for known safe operations. For deletions or major refactors, omit `--yes` to let the user review the plan in the OpenClaw chat.

```

---

### How to Power-Up your Claude Code (2026 Manual)

To ensure OpenClaw can actually execute the rules in the `SKILL.md` above, you need to configure Claude Code's ecosystem:

#### 1. Installing MCP (Model Context Protocol)

MCP is how Claude talks to your local files, databases, and Google.

* **To add a tool:** Inside your terminal, run `claude mcp add [name]`.
* **Common 2026 Servers:** * `github`: For managing PRs and issues.
* `google-maps`: For location-aware apps.
* `postgres`: To let Claude query your databases directly.



#### 2. Installing Plugins

Plugins are "bundles" of skills. Use these to make Claude a better specialist.

* Run `claude` to enter the interactive mode.
* Type `/plugin` to open the marketplace.
* **Must-haves for Web Apps:** Install `frontend-design` and `api-generator`.

#### 3. Building for other Agents

When you ask OpenClaw to "Build a tool for my other bots," the `SKILL.md` tells it to focus on **Machine-to-Machine** (M2M) communication.

* **Example Prompt to OpenClaw:** *"Use Claude Code to build a Python FastAPI that tracks my expenses. Make sure it has a Swagger UI so my other agents can learn how to post data to it."*
