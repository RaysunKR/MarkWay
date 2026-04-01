# MarkWay

> Empowering AI Agents to browse the web with clarity and intelligence.

## Why MarkWay?

The web was built for humans, not machines. While humans can effortlessly parse HTML, navigate complex layouts, and understand visual hierarchies, AI Agents struggle with these tasks. MarkWay bridges this gap by providing a protocol that speaks the language AI understands best: **structured, semantic content**.

## The Problem

Traditional web browsing requires AI Agents to:
- Parse complex HTML structures
- Execute JavaScript to render content
- Deal with inconsistent class names and DOM structures
- Handle anti-scraping measures and rate limits
- Extract meaningful data from visual layouts

This approach is fragile, inefficient, and computationally expensive.

## The Solution

MarkWay introduces a **Markdown-first protocol** that transforms the web experience for AI Agents:

```
Web → Markdown → Agent
```

By serving content directly in Markdown format, MarkWay enables:

- **Semantic clarity**: Content structure is explicit and unambiguous
- **Efficient parsing**: No HTML parsing overhead or DOM manipulation
- **Natural comprehension**: AI reads like humans read documentation
- **Protocol discovery**: Built-in mechanism for Agents to understand site structure

## How It Works

MarkWay operates in two modes:

### Static Mode
Content is organized as Markdown files with predictable directory structures:
- Every directory contains an `index.md` with a structured table of contents
- All links end with `.md` for consistency
- Supports relative, absolute, and external paths

### Dynamic Mode
Interactive endpoints use HTTP methods semantically:
- `GET` returns Markdown documentation (no URL parameters)
- `POST` performs data exchange via request body
- Response format negotiation via `Accept` headers

## Quick Start

For site owners:
1. Serve your content in Markdown format
2. Include `index.md` in each directory with a table listing files and their purposes
3. Root request must link to protocol documentation at `/protocol`

For AI Agent developers:
1. Detect MarkWay sites via the `X-MarkWay-Protocol` header or protocol discovery
2. Parse `index.md` tables to navigate site structure
3. Use `GET` for documentation, `POST` for data exchange

## Protocol Specification

The complete protocol specification is available in:
- [English](protocol_en.md)
- [简体中文](protocol.md)
- [繁體中文](protocol_zh_TW.md)

## Use Cases

- **API Documentation**: Human-readable docs that Agents can parse flawlessly
- **Knowledge Bases**: Structured information accessible to both humans and AI
- **Data Services**: Query endpoints with self-documenting interfaces
- **AI-Native Applications**: Build web services designed for Agent consumption

## Contributing

We welcome contributions! Please submit issues and pull requests to help improve the MarkWay protocol.

## License

MIT License

---

*MarkWay: The web, reimagined for the age of AI.*
