# 跨界 AI 文档维护约定

本仓库是跨界 AI 的中文 Mintlify 文档站，部署域名为 `docs.kuajieaigc.com`。

## 站点信息

- 品牌名称：跨界AI
- 品牌标语：大国重器·AI让生活更美好
- 官网与控制台：`https://www.kuajieaigc.com`
- 模型价格与当前模型 ID：`https://www.kuajieaigc.com/pricing`
- API 请求入口：`https://api.kuajieaigc.com`
- 文档站配置：`docs.json`

## 写作规则

- 面向中文开发者，用简洁、直接的步骤说明。
- 操作流程按控制台当前页面与仓库代码核实后再写。
- 不写未经核实的模型 ID、价格、支付渠道、退款政策、客服联系方式、备用域名或性能承诺。
- 示例中使用 `your-api-key-here` 和 `your-model-id` 等占位符，并说明到模型广场复制实际模型 ID。
- API 路径示例使用 `api.kuajieaigc.com`；官网、注册、价格与账户入口使用 `www.kuajieaigc.com`。
- 外部客户端设置链接到其官方文档，不把第三方产品说成跨界 AI 自有功能。
- 页面正文由 frontmatter 的 `title` 显示，不重复添加相同的首个 H1。
- 不写入、提交或展示部署密钥、API Key、访问令牌或其他凭证。

## 检查

在仓库根目录运行：

```bash
mint validate
mint broken-links
```

新页面需添加到 `docs.json` 导航。发布前检查内部链接、Logo、站点品牌、官网入口和 API 域名。
