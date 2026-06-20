# DocuGenius.usa

> Local document-to-Markdown converter that lets AI coding tools read your business documents directly.

[![Version](https://img.shields.io/badge/version-2.5.8-blue)](https://github.com/brucevanfdm/DocuGenius/releases)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

DocuGenius.usa is a ported VSCode extension that converts Word, Excel, PowerPoint and PDF files into structured Markdown, so AI coding tools such as Trae AI, CodeBuddy and Cursor can natively understand your product docs, data tables and technical material.

## Quick Start

### Installation

**Option 1: Extension Marketplace (recommended)**

Search for `DocuGenius` in the VSCode / Trae / CodeBuddy extension marketplace and click install.

**Option 2: Manual install**

1. Download the latest `.vsix`: [GitHub Releases](https://github.com/brucevanfdm/DocuGenius/releases/latest)
2. In your editor, choose "Install from VSIX"

### Usage

**Convert a single file**

Right-click a document → select `[DocuGenius] Convert to Markdown` → output lands in the `DocuGenius/` directory.

**Batch conversion**

Right-click a folder → select `[DocuGenius] Process All Files in Folder`.

Once conversion is done, just reference the generated Markdown files directly in your AI chat window.

## Supported Formats

| Format | Extension | Result |
|--------|-----------|--------|
| Word | `.docx` | Preserves text hierarchy, extracts images to `images/` |
| Excel | `.xlsx` | Converts to structured Markdown tables |
| PowerPoint | `.pptx` | Extracts text and images page by page |
| PDF | `.pdf` | High-quality text extraction |

## Features

- **Fully local processing** — documents never leave your machine, keeping sensitive data safer
- **No quantity limits** — not bound by the file count/size caps of cloud knowledge bases
- **AI-native format** — outputs structured Markdown that suits any AI coding tool
- **Batch conversion** — process an entire folder in a single click

## Typical Use Cases

- **Product material creation**: spin up new proposals quickly from historical PRDs (Product Requirements Documents)
- **Data analysis**: hand Excel metrics tables to AI and let it generate conclusions
- **Competitive research**: batch-convert competitor PDFs into structured comparison reports
- **Requirements management**: extract feature lists and verify parameter details from product docs

## Before & After

Before:

```
project/
├── product-requirements.docx   # AI can't read it directly
├── user-data.xlsx              # structure is hard for AI to parse
└── technical-doc.pdf           # needs manual copy-paste
```

After:

```
project/
├── source-documents/
│   ├── product-requirements.docx
│   ├── user-data.xlsx
│   └── technical-doc.pdf
└── DocuGenius/                 # knowledge base AI can reference directly
    ├── product-requirements.md
    ├── user-data.md
    ├── technical-doc.md
    └── images/
        ├── product-requirements/
        └── technical-doc/
```

## System Requirements

- **macOS**: works out of the box (Intel / Apple Silicon)
  - Release builds bundle a universal macOS binary supporting both Intel and Apple Silicon
  - No separate Rosetta 2 install required
- **Windows**: requires Python 3.6+ installed beforehand
  - On first conversion, DocuGenius prompts you to install a **shared local runtime**
  - This runtime installs only in the extension's own storage directory and is reused across all workspaces
  - It won't create a separate `.venv` in each project directory, nor install dependencies into the current workspace

## Windows Runtime Notes

On Windows, DocuGenius uses your system Python for a **one-time bootstrap** only:

1. Detect whether a usable Python is present on the machine
2. Create a shared runtime in the extension's global storage directory
3. Install `python-docx`, `openpyxl`, `python-pptx` and `pdfplumber` into that shared runtime
4. All subsequent workspaces reuse this runtime for conversion

If you need to manage the runtime manually, use these Command Palette commands:

- `DocuGenius: Install Shared Runtime`
- `DocuGenius: Repair Shared Runtime`
- `DocuGenius: Show Runtime Status`

## FAQ

**Q: How is this different from Claude Project / ChatGPT Project?**

A: DocuGenius is a local conversion approach with no file count or size limits, and full support for Excel table conversion. The resulting Markdown works in any AI coding tool — lower cost, safer data.

**Q: Is my document data safe?**

A: Conversion runs entirely locally and nothing is uploaded to any server. Calling a cloud LLM when you later use AI chat is simply the normal AI-tool workflow.

**Q: Does it support previewing Office and PDF files?**

A: No. DocuGenius focuses on conversion. To preview original files inside your IDE, pair it with an Office Viewer-style extension.

**Q: Will Windows install a copy of the dependencies for every project?**

A: No. DocuGenius now installs the Windows runtime into the extension's own shared directory; all workspaces share a single copy, so your project directories stay clean.

## Author

- X: [@bruc3van](https://x.com/bruc3van)
- GitHub: [@bruc3van](https://github.com/bruc3van)
