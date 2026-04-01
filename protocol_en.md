# MarkWay

> An HTTP protocol standard designed for AI Agents, enabling machines to browse the web more intelligently.

## Introduction

MarkWay is a Markdown-based HTTP protocol extension specifically designed for AI Agents. It converts web content into structured Markdown format and returns it to Agents, significantly reducing parsing complexity and allowing AI to understand and browse web pages as naturally as humans read documents.

**Core Concept**: Web → Markdown → Agent, skipping complex HTML parsing and directly providing semantic structured content.

## Protocol Specification

The MarkWay protocol defines data exchange standards between AI Agents and servers, supporting two operating modes:

### Root Request and Protocol Discovery

Regardless of the mode used, the root request (website entry point) must specify the location of the protocol document in its response content, so that all Agents can understand how to browse MarkWay sites.

| Mode | Root Request | Protocol Document | Content Requirements |
|------|--------------|-------------------|---------------------|
| Static Mode | `/index.md` | `/protocol.md` (fixed) | README.md content of this protocol in any language |
| Dynamic Mode | `/` | `/protocol` (fixed) | README.md content of this protocol in any language |

**Notes:**
- The root request response must contain a link to the protocol document
- The protocol document contains the complete specification of this protocol (MarkWay), available in any language version
- Agents can understand how to browse the current site by accessing the protocol document

### Static Mode

Static mode is suitable for document-oriented websites with fixed content, where all resources are organized as Markdown files.

**Rules:**
- All links must end with `.md`
- Each directory must contain an `index.md` file
- All `index.md` files and Markdown content returned by GET requests must include a declaration at the beginning stating that the site uses the MarkWay protocol and provide the protocol address
  - File/subdirectory name
  - Address (supports three path types)
  - Main content
  - Description of purpose

**Path Types:**

| Type | Format Example | Description |
|------|---------------|-------------|
| Relative Path | `./getting-started.md`, `../api/index.md` | Position relative to current directory |
| Absolute Path | `/docs/guide.md`, `/api/users` | Position relative to site root |
| External Path | `https://example.com/doc.md` | Full URL pointing to external site |

Agents determine the path type and locate resources based on the address format.

**Example Directory Structure:**
```
/docs
  ├── index.md          # Directory index
  ├── getting-started.md
  ├── api/
  │     ├── index.md    # API subdirectory index
  │     └── reference.md
  └── examples/
        ├── index.md
        └── tutorial.md
```

**Example `index.md`:**
```markdown
# Documentation Directory

| Name | Address | Content | Purpose |
|------|---------|---------|---------|
| Getting Started | ./getting-started.md | Installation and basic configuration | Help new users get started |
| External Docs | https://example.com/docs.md | Third-party reference materials | Extended reading |
| API Reference | ./api/index.md | API documentation index | View all API descriptions |
| Examples | ./examples/index.md | Usage examples index | Reference real-world cases |
```

### Dynamic Mode

Dynamic mode is suitable for scenarios requiring interaction and data exchange, distinguishing operation types through HTTP request methods.

**Rules:**
- **GET Request**: Returns Markdown format API documentation, URL is an absolute static path, **URL parameters are prohibited**. Response content must include a declaration at the beginning stating that the site uses the MarkWay protocol and provide the protocol address
- **POST Request**: Executes data exchange, all parameters passed through the request body, supporting the following response formats:
  - Markdown dynamic page (default)
  - JSON / other format data (specified via `Accept` header)

**Request Examples:**
```bash
# Get API documentation (GET)
GET /api/users
# Returns: Parameter documentation for this API (Markdown)

# Execute data query (POST)
POST /api/users
Content-Type: application/json

{"id": 123}
# Returns: User data (Markdown table or JSON)
```

**Response Format Negotiation:**

| Accept Header | Response Format |
|---------------|-----------------|
| `text/markdown` | Markdown document (default) |
| `application/json` | JSON data |


## Contributing

Issues and PRs are welcome to improve the MarkWay protocol.

## About the Author

- **Author**: RaysunKR


## License

MIT License
