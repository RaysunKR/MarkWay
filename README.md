<div align="center">

# 🪐 MarkWay

**An HTTP protocol standard that empowers AI Agents to browse the web with clarity and intelligence.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Protocol](https://img.shields.io/badge/Protocol-v1.0-green.svg)](protocol_en.md)
[![Sites](https://img.shields.io/badge/Adopted_Sites-2-orange.svg)](index.md)

[English](README.md) · [简体中文](README_zh.md) · [繁體中文](README_zh_TW.md)

</div>

---

## ✨ The Vision

> **Web → Markdown → Agent**

The web was built for humans, not machines. MarkWay bridges the gap by providing a **Markdown-first protocol** that speaks the language AI understands best — structured, semantic content. No more fragile HTML parsing. No more JavaScript rendering overhead.

```text
┌──────────┐     MarkWay      ┌──────────────┐     Structured      ┌──────────┐
│          │  ──- Protocol ──► │              │  ──- Markdown ────► │          │
│   Web    │                   │   MarkWay    │                     │  AI      │
│  Server  │  ◄── Markdown ──  │   Server     │  ◄── Requests ───  │  Agent   │
│          │                   │              │                     │          │
└──────────┘                   └──────────────┘                     └──────────┘
```

---

## 🎯 Why MarkWay?

Traditional web browsing for AI Agents is painful:

| Challenge | Traditional Web | MarkWay |
|-----------|----------------|---------|
| **Parsing** | Complex HTML + DOM tree | Pure Markdown |
| **Rendering** | JavaScript execution needed | Static text, no JS |
| **Navigation** | Inconsistent class names | Structured `index.md` tables |
| **Discovery** | Crawling & guessing | Built-in protocol endpoint |
| **Bandwidth** | Bloated HTML/CSS/JS | Minimal text payload |

---

## 🚀 How It Works

MarkWay operates in **two modes**, both serving content directly as Markdown:

### 📄 Static Mode
For document-oriented sites with fixed content — just serve `.md` files.

- Every directory contains an `index.md` with a **structured table of contents**
- All links end with `.md` for consistency
- Supports relative, absolute, and external paths

```markdown
https://docs.example.com

> This site follows the MarkWay Protocol: https://docs.example.com/protocol.md

# Documentation Directory

| Address | Description |
|---------|-------------|
| ./getting-started.md | Getting Started guide for new users |
| ./api/index.md       | API Reference with all endpoints |
| ./examples/index.md  | Real-world usage examples |
```

### ⚡ Dynamic Mode
For interactive endpoints requiring data exchange.

| Method | Purpose | Response |
|--------|---------|----------|
| `GET` | Retrieve documentation | Markdown (no URL params) |
| `POST` | Data exchange | Markdown or JSON via `Accept` header |

```bash
# Get API documentation
GET /api/users
# → Returns Markdown docs for this endpoint

# Execute a query
POST /api/users
Content-Type: application/json
{"id": 123}
# → Returns user data as Markdown table or JSON
```

---

## 🔍 Protocol Discovery

Every MarkWay site announces itself at the root entry point:

| Mode | Entry Point | Protocol Document |
|------|-------------|-------------------|
| Static | `/index.md` | `{baseURL}/protocol.md` |
| Dynamic | `/` | `{baseURL}/protocol` |

Agents simply follow the protocol link to understand the full site structure — no guesswork, no crawling.

---

## 🛠 Quick Start

### For Site Owners

1. **Serve** your content as Markdown files
2. **Add** an `index.md` to each directory with a table listing files and descriptions
3. **Link** to the protocol document from the root request

### For AI Agent Developers

1. **Detect** MarkWay sites via `/protocol` or `/protocol.md`
2. **Parse** `index.md` tables to navigate the site structure
3. **Use** `GET` for docs, `POST` for data exchange

### For AI Agent Platforms

MarkWay ships a ready-to-use **skill** that lets your agents automatically discover and interact with MarkWay sites:

```
skills/markway/
```

Include it in your agent's skill registry to enable instant MarkWay protocol support.

---

## 📋 Protocol Specification

The complete specification is available in three languages:

| Language | Document |
|----------|----------|
| English | [protocol_en.md](protocol_en.md) |
| 简体中文 | [protocol.md](protocol.md) |
| 繁體中文 | [protocol_zh_TW.md](protocol_zh_TW.md) |

---

## 🌍 Sites Using MarkWay

| Site | URL | Description |
|------|-----|-------------|
| SparkGlobe | [SparkGlobe](https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master/index.md) | An AI Agent skill navigator built on the MarkWay protocol |
| ZIWEI.ONE | [ziwei.one](https://ziwei.one) | Purple Star Astrology divination tool for Agents |

**Add your site** — Fork the repo, add your site to [index.md](index.md), and submit a PR!

---

## 💡 Use Cases

<table>
<tr>
<td width="50%">

#### 📚 API Documentation
Human-readable docs that AI Agents parse flawlessly — no OpenAPI overhead.

</td>
<td width="50%">

#### 🧠 Knowledge Bases
Structured information accessible to both humans and AI, from the same source.

</td>
</tr>
<tr>
<td width="50%">

#### 🔄 Data Services
Self-documenting query endpoints. Agents discover capabilities automatically.

</td>
<td width="50%">

#### 🤖 AI-Native Apps
Build web services designed from the ground up for Agent consumption.

</td>
</tr>
</table>

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

- 🐛 **Report issues** — Found a bug? Open an issue.
- 💡 **Propose ideas** — Suggestions for protocol improvements.
- 🔀 **Submit PRs** — Code contributions and documentation fixes.
- 🌐 **Add your site** — Adopt MarkWay and list it in the index.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

<div align="center">

**MarkWay — The web, reimagined for the age of AI.** 🪐

</div>
