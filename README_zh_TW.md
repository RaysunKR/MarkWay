<div align="center">

# 🪐 MarkWay

**一種為 AI Agent 設計的 HTTP 協定標準，讓機器以更清晰、更智慧的方式瀏覽網頁。**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Protocol](https://img.shields.io/badge/Protocol-v1.0-green.svg)](protocol_zh_TW.md)
[![Sites](https://img.shields.io/badge/已採用站點-2-orange.svg)](index.md)

[English](README.md) · [简体中文](README_zh.md) · [繁體中文](README_zh_TW.md)

</div>

---

## ✨ 願景

> **網頁 → Markdown → Agent**

網際網路是為人而建的，不是為機器。MarkWay 透過提供一種 **Markdown 優先的協定**來彌合這一差距，以 AI 最理解的語言傳遞內容——結構化、語義化的資訊。告別脆弱的 HTML 解析，告別 JavaScript 渲染開銷。

```text
┌──────────┐     MarkWay      ┌──────────────┐     結構化         ┌──────────┐
│          │  ──- 協定 ──────► │              │  ──- Markdown ───► │          │
│   Web    │                   │   MarkWay    │                    │  AI      │
│  伺服器  │  ◄── Markdown ──  │   伺服器     │  ◄── 請求 ───────  │  Agent   │
│          │                   │              │                    │          │
└──────────┘                   └──────────────┘                    └──────────┘
```

---

## 🎯 為什麼選擇 MarkWay？

傳統網頁瀏覽對 AI Agent 來說困難重重：

| 挑戰 | 傳統 Web | MarkWay |
|------|----------|---------|
| **解析** | 複雜的 HTML + DOM 樹 | 純 Markdown |
| **渲染** | 需要執行 JavaScript | 靜態文字，無需 JS |
| **導航** | 不一致的類別名稱 | 結構化的 `index.md` 表格 |
| **發現** | 爬取與猜測 | 內建協定端點 |
| **頻寬** | 龐大的 HTML/CSS/JS | 最小化的文字負載 |

---

## 🚀 工作原理

MarkWay 以 **兩種模式** 運作，均直接以 Markdown 格式提供內容：

### 📄 靜態模式
適用於內容固定的文件型站點——只需提供 `.md` 檔案。

- 每個目錄包含一個 `index.md`，帶有 **結構化的目錄表格**
- 所有連結以 `.md` 結尾，保持一致性
- 支援相對路徑、絕對路徑和外部路徑

```markdown
https://docs.example.com

> This site follows the MarkWay Protocol: https://docs.example.com/protocol.md

# 文件目錄

| Address | Description |
|---------|-------------|
| ./getting-started.md | 新使用者入門指南 |
| ./api/index.md       | 包含所有端點的 API 參考 |
| ./examples/index.md  | 真實使用範例 |
```

### ⚡ 動態模式
適用於需要互動和資料交換的端點。

| 方法 | 用途 | 回應 |
|------|------|------|
| `GET` | 取得文件 | Markdown（不使用 URL 參數） |
| `POST` | 資料交換 | Markdown 或 JSON（透過 `Accept` 標頭指定） |

```bash
# 取得 API 文件
GET /api/users
# → 回傳該端點的 Markdown 文件

# 執行查詢
POST /api/users
Content-Type: application/json
{"id": 123}
# → 以 Markdown 表格或 JSON 回傳使用者資料
```

---

## 🔍 協定發現

每個 MarkWay 站點都會在根入口點宣告自身：

| 模式 | 入口點 | 協定文件 |
|------|--------|----------|
| 靜態 | `/index.md` | `{baseURL}/protocol.md` |
| 動態 | `/` | `{baseURL}/protocol` |

Agent 只需跟隨協定連結即可理解完整的站點結構——無需猜測，無需爬取。

---

## 🛠 快速開始

### 對於站點所有者

1. **提供** Markdown 格式的內容
2. **新增** `index.md` 到每個目錄，用表格列出檔案和描述
3. **連結** 從根請求到協定文件

### 對於 AI Agent 開發者

1. **偵測** MarkWay 站點，存取 `/protocol` 或 `/protocol.md`
2. **解析** `index.md` 表格以導航站點結構
3. **使用** `GET` 取得文件，`POST` 進行資料交換

### 對於 AI Agent 平台

MarkWay 提供了開箱即用的 **skill**，讓你的 Agent 自動發現並互動 MarkWay 站點：

```
skills/markway/
```

將其加入你的 Agent 技能註冊表，即可啟用即時 MarkWay 協定支援。

---

## 📋 協定規範

完整的協定規範提供三種語言版本：

| 語言 | 文件 |
|------|------|
| English | [protocol_en.md](protocol_en.md) |
| 简体中文 | [protocol.md](protocol.md) |
| 繁體中文 | [protocol_zh_TW.md](protocol_zh_TW.md) |

---

## 🌍 採用 MarkWay 的站點

| 站點 | URL | 描述 |
|------|-----|------|
| SparkGlobe | [sparkglobe.net](https://sparkglobe.net) | 啟發 AI Agent 以更好的方式產生程式碼 |
| ZIWEI.ONE | [ziwei.one](https://ziwei.one) | 紫微斗數占卜工具，支援 Agent 占卜 |

**新增你的站點** — Fork 本儲存庫，將你的站點新增到 [index.md](index.md)，然後提交 PR！

---

## 💡 使用場景

<table>
<tr>
<td width="50%">

#### 📚 API 文件
人類可讀且 Agent 可完美解析的文件——無需 OpenAPI 開銷。

</td>
<td width="50%">

#### 🧠 知識庫
人類和 AI 都可存取的結構化資訊，來自同一資料來源。

</td>
</tr>
<tr>
<td width="50%">

#### 🔄 資料服務
自文件化的查詢端點。Agent 可自動發現服務能力。

</td>
<td width="50%">

#### 🤖 AI 原生應用
從底層為 Agent 消費而設計的 Web 服務。

</td>
</tr>
</table>

---

## 🤝 參與貢獻

我們歡迎各種形式的貢獻：

- 🐛 **回報問題** — 發現 Bug？提一個 Issue。
- 💡 **提出建議** — 對協定改進的想法。
- 🔀 **提交 PR** — 程式碼貢獻和文件修復。
- 🌐 **新增站點** — 採用 MarkWay 並在索引中列出。

---

## 📄 授權條款

本專案基於 [MIT 授權條款](LICENSE) 開源。

---

<div align="center">

**MarkWay — 為 AI 時代重新構想的網路。** 🪐

</div>
