# 跨界 AI Mintlify 文档站设计

**状态：** 用户已确认完整参照参考站
**日期：** 2026-10-30

## 目标

把现有公开仓库 `superhkk/docs` 从 Mintlify starter 改造成跨界 AI 的中文用户文档站，部署到 `docs.kuajieaigc.com`，帮助用户完成开户、创建 API Key 和配置兼容客户端。

## 范围

完整对齐 `https://docs.rayinai.com/` 当前 24 个页面的导航主题和用户操作路径：介绍、注册、充值、API Key、通用 CLI、Codex、ChatGPT 桌面应用、VS Code、Claude Code、Claude Desktop、Gemini CLI、Cherry Studio、Chatbox、OpenCode、OpenClaw、JetBrains、CC-Switch、Node.js 环境、代码调用和联系支持。页面正文以跨界 AI 当前站点、账户流程和 API 配置重新编写，保持完整的主题覆盖，不逐段复制参考站原文。

涉及跨界 AI 后台实际按钮或账户策略的步骤需核实后再写。模型可用情况以跨界 AI 控制台展示为准；通用 New API 功能保留官方文档链接。

## 品牌与链接

- 产品名称：跨界 AI。
- 用户入口：首页 `https://www.kuajieaigc.com`。
- API Base URL：`https://api.kuajieaigc.com/v1`。
- 站点域名：`https://docs.kuajieaigc.com`。
- Logo：复用当前服务公开资源 `https://www.kuajieaigc.com/relay-station-kj-logo.png`，并保留深浅主题显示。
- 品牌标语：`大国重器·AI让生活更美好`。
- 通用功能说明：链接到 New API 官方文档，不复制上游完整手册。

## 架构与发布

- 继续使用独立公开仓库 `superhkk/docs`，Mintlify 配置、文档页面和品牌资源均在该仓库维护。
- Mintlify GitHub App 从 `main` 分支读取 `docs.json` 并自动发布；不会触发 New API 镜像构建或服务器 SSH 部署。
- 在当前 Codex 客户端配置远程 MCP `mintlify-admin`，地址为 `https://mcp.mintlify.com`；首次使用需完成 Mintlify 账号授权。
- Mintlify 控制台绑定 `docs.kuajieaigc.com`。若尚未配置 DNS，按控制台给出的 CNAME 目标添加记录后等待 TLS 生效。
- 当前仓库的 `index.mdx`、`quickstart.mdx`、`docs.json`、Logo、README 和全部 24 个用户文档页面将从 starter 内容替换为项目内容；`AGENTS.md` 更新为本项目术语和文档规则。

## 验收

- Mintlify 本地预览成功，`docs.json` 结构校验通过，导航页均无 404。
- 所有公开代码示例均使用 `https://api.kuajieaigc.com/v1`，不含占位域名、Key 或部署密钥。
- 站点标题、标语、Logo、首页入口和文档内部链接均指向跨界 AI。
- GitHub `main` 推送触发 Mintlify 构建；自定义域名 HTTPS 首页可访问。
- Codex 客户端能列出 Mintlify MCP 工具并完成授权。

## 未包含

- 不修改 `kuajieaicenter` API 代码、镜像构建或服务器部署流程。
- 不添加服务器 SSH、数据库、Redis 或环境变量密钥到公开文档仓库。
- 不宣称未经控制台验证的模型版本、定价或功能支持情况。
