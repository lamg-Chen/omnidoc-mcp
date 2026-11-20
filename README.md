# OmniDoc MCP server

A local MCP server that lets AI agents create, read, edit, render, translate and share **real Office and PDF files**: Word (.docx), PDF, PowerPoint (.pptx), Excel (.xlsx), plus OmniDoc's own lossless .udoc format.

It ships with the free [OmniDoc](https://omnidoc.top) desktop app for Windows, macOS and Linux. The server runs on your own computer over stdio, and no API key is needed.

> This repository holds documentation and configuration examples only. The server binary comes with the OmniDoc desktop app: [download](https://download.omnidoc.top/).

## Connect it to your AI client

**One click:** open the desktop app's **AI interface** page and install it into Claude Desktop, Trae, Qoder, WorkBuddy, Kiro and other supported clients.

**By hand** (Cursor or any other MCP client): add this to the client's MCP configuration, with `command` pointing at `OmniDocAI` in your OmniDoc install folder.

```json
{
  "mcpServers": {
    "omnidoc": {
      "command": "<install folder>/OmniDocAI.exe",
      "args": ["--mcp"]
    }
  }
}
```

## What an agent can do

| Area | Tools |
|---|---|
| Write documents and get every format | `omnidoc_create_udoc` (editable document plus HTML preview; add `exports: ["docx","pdf"]` for Word and PDF in the same call), `omnidoc_edit_udoc`, `omnidoc_export_udoc`, `omnidoc_templates`, `omnidoc_get_udoc_schema` |
| Check layout before handing over | `omnidoc_render_udoc`, `omnidoc_check_udoc`, `omnidoc_validate_document` |
| Word | `omnidoc_edit_docx` (edit an existing .docx in place: text, paragraphs, styles, comments, table cells; the rest of the file stays untouched), `omnidoc_import_docx` |
| Read PDF and Word | `omnidoc_read_document` (full text in reading order: headings, lists, tables as rows, headers and footers, footnotes; Word comments and tracked changes), `omnidoc_extract_document` |
| PDF | `omnidoc_edit_pdf`, `omnidoc_convert_pdf`, `omnidoc_pdf_to_html` (a PDF to one HTML file offline in about a second, which AI clients can preview) |
| PowerPoint | `omnidoc_create_pptx`, `omnidoc_edit_pptx`, `omnidoc_read_pptx`, `omnidoc_render_pptx`, `omnidoc_export_pptx` |
| Excel | `omnidoc_edit_sheet`, `omnidoc_read_sheet`, `omnidoc_render_sheet`, `omnidoc_export_sheet` |
| Translation (needs an OmniDoc account) | `omnidoc_translate_file` (whole file, tables and formulas kept in place; bilingual side by side or translation only; academic, legal, medical, technical, business and other styles), `omnidoc_translate_text`, `omnidoc_translation_status`, `omnidoc_translation_records` |
| Share and sign | `omnidoc_publish_file` (a document as a web page, with an access code by default), `omnidoc_request_signatures` |
| Research | `omnidoc_zotero_search`, `omnidoc_zotero_open`, `omnidoc_zotero_add_item`, `omnidoc_zotero_add_note`, `omnidoc_zotero_tag`, `omnidoc_zotero_attach_file`, `omnidoc_find_paper_pdf` |
| Desktop app and account | `omnidoc_open_in_editor`, `omnidoc_client_command` (run commands from the editors), `omnidoc_file_tools`, `omnidoc_account_status`, `omnidoc_account_files`, `omnidoc_account_download`, `omnidoc_help` |

## Example requests

- "Read report.pdf, write a two-page summary, and give me Word and PDF."
- "In contract.docx, change the payment term in clause 3 from 30 to 45 days and leave everything else as it is."
- "Translate paper.pdf into Chinese as a bilingual version and keep the formulas."
- "Make a 10-slide deck from these notes, render it, and fix anything that overflows."

## Limits

- Scanned PDFs need text recognition first for stable results.
- Translation, web publishing and signature requests need a signed-in OmniDoc account; local editing and format conversion are free.
- Check numbers and citations in anything an AI writes.

## Links

- Website: https://omnidoc.top
- Download (Windows, macOS, Linux): https://download.omnidoc.top/
- AI interface guide: https://download.omnidoc.top/ai-interface/OmniDoc-AI-Interface
- Free online document translation: https://omnidoc.top/en/free/translate/

OmniDoc is not related to similarly named projects such as omnidoc.fr, omnidoc.io or OmniDocBench.

---

## 中文简介

OmniDoc 桌面客户端（Windows、macOS、Linux，免费）自带的本机 MCP 服务：AI 可以直接新建、读取、修改、渲染、翻译和分享真正的 Word、PDF、PowerPoint、Excel 文件。服务在你自己的电脑上运行，不需要 API Key。客户端「AI 接口」页可一键接入 Claude 桌面版、Trae、Qoder、WorkBuddy、Kiro 等工具。下载：https://download.omnidoc.top/
