<div align="center">

# 🪐 MarkWay

**一种为 AI Agent 设计的 HTTP 协议标准，让机器以更清晰、更智能的方式浏览网页。**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Protocol](https://img.shields.io/badge/Protocol-v1.0-green.svg)](protocol.md)
[![Sites](https://img.shields.io/badge/已采用站点-2-orange.svg)](index.md)

[English](README.md) · [简体中文](README_zh.md) · [繁體中文](README_zh_TW.md)

</div>

---

## ✨ 愿景

> **网页 → Markdown → Agent**

互联网是为人而建的，不是为机器。MarkWay 通过提供一种 **Markdown 优先的协议**来弥合这一差距，以 AI 最理解的语言传递内容——结构化、语义化的信息。告别脆弱的 HTML 解析，告别 JavaScript 渲染开销。

```text
┌──────────┐     MarkWay      ┌──────────────┐     结构化         ┌──────────┐
│          │  ──- 协议 ──────► │              │  ──- Markdown ───► │          │
│   Web    │                   │   MarkWay    │                    │  AI      │
│  服务器  │  ◄── Markdown ──  │   服务器     │  ◄── 请求 ───────  │  Agent   │
│          │                   │              │                    │          │
└──────────┘                   └──────────────┘                    └──────────┘
```

---

## 🎯 为什么选择 MarkWay？

传统网页浏览对 AI Agent 来说困难重重：

| 挑战 | 传统 Web | MarkWay |
|------|----------|---------|
| **解析** | 复杂的 HTML + DOM 树 | 纯 Markdown |
| **渲染** | 需要执行 JavaScript | 静态文本，无需 JS |
| **导航** | 不一致的类名 | 结构化的 `index.md` 表格 |
| **发现** | 爬取与猜测 | 内置协议端点 |
| **带宽** | 臃肿的 HTML/CSS/JS | 最小化的文本负载 |

---

## 🚀 工作原理

MarkWay 以 **两种模式** 运行，均直接以 Markdown 格式提供内容：

### 📄 静态模式
适用于内容固定的文档型站点——只需提供 `.md` 文件。

- 每个目录包含一个 `index.md`，带有 **结构化的目录表格**
- 所有链接以 `.md` 结尾，保持一致性
- 支持相对路径、绝对路径和外部路径

```markdown
https://docs.example.com

> This site follows the MarkWay Protocol: https://docs.example.com/protocol.md

# 文档目录

| Address | Description |
|---------|-------------|
| ./getting-started.md | 新用户入门指南 |
| ./api/index.md       | 包含所有端点的 API 参考 |
| ./examples/index.md  | 真实使用示例 |
```

### ⚡ 动态模式
适用于需要交互和数据交换的端点。

| 方法 | 用途 | 响应 |
|------|------|------|
| `GET` | 获取文档 | Markdown（不使用 URL 参数） |
| `POST` | 数据交换 | Markdown 或 JSON（通过 `Accept` 头指定） |

```bash
# 获取 API 文档
GET /api/users
# → 返回该端点的 Markdown 文档

# 执行查询
POST /api/users
Content-Type: application/json
{"id": 123}
# → 以 Markdown 表格或 JSON 返回用户数据
```

---

## 🔍 协议发现

每个 MarkWay 站点都会在根入口点声明自身：

| 模式 | 入口点 | 协议文档 |
|------|--------|----------|
| 静态 | `/index.md` | `{baseURL}/protocol.md` |
| 动态 | `/` | `{baseURL}/protocol` |

Agent 只需跟随协议链接即可理解完整的站点结构——无需猜测，无需爬取。

---

## 🛠 快速开始

### 对于站点所有者

1. **提供** Markdown 格式的内容
2. **添加** `index.md` 到每个目录，用表格列出文件和描述
3. **链接** 从根请求到协议文档

### 对于 AI Agent 开发者

1. **检测** MarkWay 站点，访问 `/protocol` 或 `/protocol.md`
2. **解析** `index.md` 表格以导航站点结构
3. **使用** `GET` 获取文档，`POST` 进行数据交换

### 对于 AI Agent 平台

MarkWay 提供了开箱即用的 **skill**，让你的 Agent 自动发现并交互 MarkWay 站点：

```
skills/markway/
```

将其加入你的 Agent 技能注册表，即可启用即时 MarkWay 协议支持。

---

## 📋 协议规范

完整的协议规范提供三种语言版本：

| 语言 | 文档 |
|------|------|
| English | [protocol_en.md](protocol_en.md) |
| 简体中文 | [protocol.md](protocol.md) |
| 繁體中文 | [protocol_zh_TW.md](protocol_zh_TW.md) |

---

## 🌍 采用 MarkWay 的站点

| 站点 | URL | 描述 |
|------|-----|------|
| SparkGlobe | [sparkglobe.net](https://sparkglobe.net) | 启发 AI Agent 以更好的方式生成代码 |
| ZIWEI.ONE | [ziwei.one](https://ziwei.one) | 紫微斗数占卜工具，支持 Agent 占卜 |

**添加你的站点** — Fork 本仓库，将你的站点添加到 [index.md](index.md)，然后提交 PR！

---

## 💡 使用场景

<table>
<tr>
<td width="50%">

#### 📚 API 文档
人类可读且 Agent 可完美解析的文档——无需 OpenAPI 开销。

</td>
<td width="50%">

#### 🧠 知识库
人类和 AI 都可访问的结构化信息，来自同一数据源。

</td>
</tr>
<tr>
<td width="50%">

#### 🔄 数据服务
自文档化的查询端点。Agent 可自动发现服务能力。

</td>
<td width="50%">

#### 🤖 AI 原生应用
从底层为 Agent 消费而设计的 Web 服务。

</td>
</tr>
</table>

---

## 🤝 参与贡献

我们欢迎各种形式的贡献：

- 🐛 **报告问题** — 发现 Bug？提一个 Issue。
- 💡 **提出建议** — 对协议改进的想法。
- 🔀 **提交 PR** — 代码贡献和文档修复。
- 🌐 **添加站点** — 采用 MarkWay 并在索引中列出。

---

## 📄 许可证

本项目基于 [MIT 许可证](LICENSE) 开源。

---

<div align="center">

**MarkWay — 为 AI 时代重新构想的网络。** 🪐

</div>
