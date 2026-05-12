# 飞书 CLI 安装指南

以下步骤面向 AI Agent，部分步骤需要用户在浏览器中配合完成。

## 环境要求

开始安装之前，请确保环境中已安装：

- Node.js（npm/npx）
- Go v1.23+ 和 Python 3（仅源码构建需要）

## 第 1 步 安装

```shell
# 安装 CLI
npm install -g @larksuite/cli

# 安装 CLI SKILL（必需）
npx skills add larksuite/cli -y -g
``` 

## 第 2 步 配置应用凭证

Agent 运行以下命令，并让用户协助完成授权。

```shell
lark-cli config init
```

## 第 3 步 登录

Agent 运行以下命令，并提取授权链接发给用户。

```shell
lark-cli auth login
```

## 第 4 步 验证

```shell
lark-cli auth status
```

## 第 5 步 新增全局配置的飞书 steering

新增一个 ~/.kiro/steering/feishu.md 的全局 steering 写入以下内容

```
---
inclusion: always
---

# 飞书文档阅读规则

当用户提供飞书文档链接（匹配 `*.feishu.cn/*` 或 `*.larksuite.com/*`）并要求阅读时：

1. **不要使用 web_fetch**——飞书文档几乎都需要认证，web_fetch 无法获取内容。
2. **使用 lark-doc skill**——从 URL 中提取 document token，通过飞书 Open API 获取文档内容。
3. URL 中的 token 通常是路径最后一段，例如 `https://my.feishu.cn/wiki/CsDrwMUMgil8GFk5M1Gccz7Snze` 中的 `CsDrwMUMgil8GFk5M1Gccz7Snze`。
```


更多命令和能力指南，可参考 [飞书 CLI：给 Agent 一双操作飞书的手](https://open.larkoffice.com/document/mcp_open_tools/feishu-cli-let-ai-actually-do-your-work-in-feishu.md)。
