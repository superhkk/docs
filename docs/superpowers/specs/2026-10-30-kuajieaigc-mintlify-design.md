# 跨界 AI Mintlify 文档站设计

**状态：** 等待审阅  
**日期：** 2026-10-30

## 目标

把现有公开仓库 `superhkk/docs` 从 Mintlify starter 改造成跨界 AI 的中文用户文档站，部署到 `docs.kuajieaigc.com`，帮助用户完成开户、创建 API Key 和配置兼容客户端。

## 范围

首版采用“小步补齐”方式，沿用 `https://docs.rayinai.com/` 的用户路径与导航思路，但使用跨界 AI 自有品牌、入口和 API 地址，并以原创中文表述编写：

- 首页：说明服务用途，并提供注册、控制台和 API 接入入口。
- 快速开始：说明从账号、API Key 到首个 API 请求的步骤；涉及账户后台的文案先核实实际页面后再写。
- 客户端接入：提供通用 OpenAI 兼容配置，并优先补充 Codex、Claude Code、Gemini CLI 的必要配置。
- API 调用：提供可复制的 `curl` 示例，使用 `https://api.kuajieaigc.com/v1`。
- 常见问题与支持：回答 API 地址、Key、模型可用性等基础问题；通用 New API 功能链接到官方文档。

暂不迁移完整 New API 功能手册，也不维护静态“最新模型”名单；模型可用情况以跨界 AI 控制台展示为准。

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
- 当前仓库的 `index.mdx`、`quickstart.mdx`、`docs.json`、Logo 和 README 将从 starter 内容替换为项目内容；`AGENTS.md` 更新为本项目术语和文档规则。

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
