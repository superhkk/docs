# Kuajie AI Mintlify Documentation Migration Plan

> **For agentic workers:** Execute inline in this session; do not dispatch subagents. Work through each task and verify the listed result before continuing.

**Goal:** Replace the Mintlify starter site in `superhkk/docs` with a Chinese documentation site covering all 24 topics on `docs.rayinai.com`, branded for Kuajie AI.

**Architecture:** Keep the standalone public `superhkk/docs` repository and Mintlify `docs.json` as the site source of truth. Recreate the reference site's user journey and topic coverage with original Kuajie AI wording, current product links, and the configured Kuajie AI logo.

**Tech Stack:** Mintlify, `docs.json`, MDX/Markdown, GitHub `main` auto-deploy, Codex remote MCP.

## Global Constraints

- Public homepage: `https://www.kuajieaigc.com`.
- API base URL in examples: `https://api.kuajieaigc.com/v1`.
- Docs domain: `https://docs.kuajieaigc.com`.
- Brand name and slogan: `跨界AI` and `大国重器·AI让生活更美好`.
- Keep the full 24-topic page set represented in the reference site's `llms.txt`.
- Reword source material for Kuajie AI; do not include RayinAPI branding, URLs, keys, or placeholder tokens.
- Use current console behavior for account steps; do not guess unknown account controls or static latest model names.
- Do not place server SSH, database, Redis, or deployment secrets in this public documentation repository.

---

### Task 1: Site identity and navigation

**Files:**
- Modify: `docs.json`
- Modify: `index.mdx`
- Modify: `README.md`
- Modify: `AGENTS.md`
- Replace: `logo/light.svg`, `logo/dark.svg`, `favicon.svg`
- Add: `assets/relay-station-kj-logo.png`

- [ ] Set Mintlify name, colors, logo, favicon, navigation groups, homepage links, support link, and GitHub anchor to Kuajie AI.
- [ ] Mirror the reference site's groups for quick start, developer clients, API, environment, CC-Switch, and help; include all 24 target routes.
- [ ] Replace starter homepage and README with Chinese Kuajie AI copy and add project-specific terminology/style guidance to `AGENTS.md`.
- [ ] Verify every page listed in `docs.json` has a corresponding Markdown/MDX file and the logo asset is present.

### Task 2: Quick-start and common CLI pages

**Files:**
- Add: `quickstart/register.mdx`
- Add: `quickstart/recharge.mdx`
- Add: `quickstart/api-key.mdx`
- Add: `quickstart/cli-setup.mdx`
- Replace: `quickstart.mdx` with the registered quick-start route or remove it from navigation if redundant.

- [ ] Write original Chinese steps for account registration, balance recharge, API key creation, and CLI configuration using actual Kuajie AI UI labels where verified.
- [ ] Use the Kuajie AI homepage and API base URL in every applicable configuration example.
- [ ] Check that no unverified billing, refund, or group-switching policy is asserted.

### Task 3: Coding assistant and desktop client guides

**Files:**
- Add: `codex/introduction.mdx`, `codex/chatgpt-app.mdx`, `codex/vscode.mdx`, `codex/faq.mdx`
- Add: `claude-code/introduction.mdx`, `claude-code/faq.mdx`
- Add: `claude-desktop/introduction.mdx`, `claude-desktop/faq.mdx`
- Add: `gemini/introduction.mdx`, `gemini/faq.mdx`

- [ ] Recreate installation, environment, configuration, verification, and troubleshooting topics for Codex, ChatGPT desktop, VS Code, Claude Code, Claude Desktop, and Gemini CLI.
- [ ] Keep client-specific environment variable names, config keys, and model identifiers aligned with the reference topic and current client behavior.
- [ ] Verify all service endpoints point to `api.kuajieaigc.com` and all account links point to `www.kuajieaigc.com`.

### Task 4: Additional clients, API, and support

**Files:**
- Add: `clients/cherry-studio.mdx`, `clients/chatbox.mdx`, `clients/opencode.mdx`, `clients/openclaw.mdx`, `clients/jetbrains.mdx`
- Add: `cc-switch/usage.mdx`
- Add: `environment/setup.mdx`
- Add: `api/overview.mdx`
- Add: `help/contact.mdx`

- [ ] Cover the five additional clients, CC-Switch, Node.js environment setup, HTTP/SDK usage, and support/contact route from the reference site.
- [ ] Provide OpenAI-compatible request examples with the Kuajie AI API base URL and a clearly marked environment-variable placeholder for user-owned API keys.
- [ ] Link generic New API feature explanations to the official New API documentation.

### Task 5: MCP, validation, and publication

**Files:**
- Modify: `/Users/huokankan/.codex/config.toml` by appending the Mintlify remote server entry without changing existing settings.
- Verify: `docs.json`, all navigation routes, MDX links, and branding assets.

- [ ] Configure `[mcp_servers.mintlify-admin]` with `url = "https://mcp.mintlify.com"`; preserve the rest of the Codex config and verify TOML parsing.
- [ ] Run the Mintlify CLI local preview or validation command and fix broken routes, malformed MDX, and invalid `docs.json` fields.
- [ ] Push the validated docs-only commit to `superhkk/docs:main` so Mintlify GitHub deployment can build it.
- [ ] Verify the Mintlify deployment and `https://docs.kuajieaigc.com`; if account authentication or DNS CNAME is missing, state the exact remaining user-side step.

