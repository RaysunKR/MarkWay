---
name: markway
description: Access and interact with websites using the MarkWay protocol. Use this skill whenever a user wants to access a MarkWay-compatible website to accomplish their goals. The MarkWay protocol provides AI Agents with structured, semantic web content in Markdown format. When the user mentions specific domains like "ziwei.one" or "sparkglobe.net", or describes needs like "divination", "astrology", "coding inspiration", or "AI tools for X", trigger this skill to discover and use the appropriate MarkWay site. The skill automatically fetches the site list from https://raw.githubusercontent.com/RaysunKR/MarkWay/refs/heads/main/index.md when no specific URL is provided, then follows the MarkWay protocol to retrieve and process results.
---

# MarkWay Agent Skill

This skill enables AI Agents to access and interact with websites that implement the MarkWay protocol. MarkWay sites return content in structured Markdown format, making it easy for Agents to parse and understand.

## Core Concept

MarkWay sites follow a simple convention:
- Content is returned in Markdown format
- Every page starts with the site's `baseURL` (first line) and a protocol declaration
- Static content uses `.md` files; interactive APIs use GET/POST methods
- Address lists are always in table format with `Address` and `Description` columns

## Workflow

### Step 1: Determine the Target URL

**If user provides a specific URL:**
- Use that URL directly
- Skip to Step 2

**If user does NOT provide a URL:**
- Fetch the site index from:
  ```
  https://raw.githubusercontent.com/RaysunKR/MarkWay/refs/heads/main/index.md
  ```
- Parse the Markdown table to extract sites
- Match the most appropriate site based on user needs:
  - Look at both the site name and description
  - Consider keywords in the user's request
  - Select the site that best matches the user's intent
- If no suitable site is found, inform the user

### Step 2: Access the Site

**For static content (e.g., documentation):**
- Send a GET request to the URL
- Parse the Markdown response

**For interactive services (e.g., divination, data queries):**
- First, GET the site's main page or API endpoint to get documentation
- Look for available endpoints and their descriptions
- If the user's request matches an endpoint description, use POST to call it
- All parameters go in the request body (JSON format)
- The response will be in Markdown table format

### Step 3: Parse Results

MarkWay responses follow consistent patterns:
1. First line: `baseURL` of the site
2. Second line: Protocol declaration (e.g., `> This site follows the MarkWay Protocol: ...`)
3. Empty line
4. Content (often in table format)

For address lists in tables:
- **Required columns**: `Address` and `Description`
- **Optional columns**: may include `Name`, `Type`, etc.

### Step 4: Present Results

- Format the final response clearly for the user
- If the result contains multiple items, present as a readable list or table
- If the result is a single value, present it directly
- If applicable, explain what the result means in context

## Response Format Examples

### Static Content Response
```markdown
## Results from [Site Name]

[Parsed content from the Markdown page]

---
*Source: [URL]*
```

### Data/Service Response
```markdown
## Results from [Service Name]

| Field | Value |
|-------|-------|
| [Key] | [Value] |

---
*Source: [URL] | Protocol: MarkWay*
```

## Error Handling

- **Site unreachable**: Inform user and suggest checking if the site is online
- **Invalid response**: If the response doesn't follow MarkWay format, return raw content with a warning
- **No matching site**: Tell the user no suitable MarkWay site was found for their request
- **API error**: Parse error messages from the response and present them clearly

## Quick Reference

| MarkWay Site Type | How to Access |
|-------------------|---------------|
| Static docs | GET request to `.md` URL |
| Interactive service | GET for docs → POST for data |

Remember: Never use URL parameters for GET requests in MarkWay. All parameters for data queries go in POST body.
