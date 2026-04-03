---
name: pptx-extract
description: "PPTX Extract - extract content from PowerPoint (.pptx) files to Markdown using MinerU. Use when parsing presentation slides."
homepage: https://mineru.net
metadata: {"openclaw": {"emoji": "📄", "requires": {"bins": ["mineru-open-api"], "env": ["MINERU_TOKEN"]}, "primaryEnv": "MINERU_TOKEN", "install": [{"id": "npm", "kind": "node", "package": "mineru-open-api", "bins": ["mineru-open-api"], "label": "Install via npm"}, {"id": "go", "kind": "go", "package": "github.com/opendatalab/MinerU-Ecosystem/cli/mineru-open-api", "bins": ["mineru-open-api"], "label": "Install via go install", "os": ["darwin", "linux"]}]}}
---

# Pptx Extract

Convert and extract content from .pptx using MinerU (`mineru-open-api`).

## Install

```bash
npm install -g mineru-open-api
# or via Go (macOS/Linux):
go install github.com/opendatalab/MinerU-Ecosystem/cli/mineru-open-api@latest
```

## Quick Start

```bash
# Quick extraction (no token required)
mineru-open-api flash-extract slides.pptx

# Save to directory
mineru-open-api flash-extract slides.pptx -o ./out/

# From URL
mineru-open-api flash-extract https://example.com/slides.pptx

# Specify language
mineru-open-api flash-extract slides.pptx --language en

# Precision extraction with token (tables, formulas, more formats)
mineru-open-api extract slides.pptx -o ./out/
```

## Authentication

No token needed for `flash-extract`. Token required for `extract` and `crawl`:

```bash
mineru-open-api auth            # Interactive token setup
export MINERU_TOKEN="your-token" # Or via environment variable
```

Create token at: https://mineru.net/apiManage/token

## Capabilities

- Supports local files and URLs
- `flash-extract`: quick, no token needed (max 10 MB / 20 pages, Markdown only)
- `extract`: token required, full features (tables, formulas, multi-format)
- Supported input: .pptx
- Language hint with `--language` (default: `ch`, use `en` for English)
- Page range with `--pages` (flash-extract and extract)

## Notes

- .pptx supports `flash-extract` for quick extraction without a token.
- Output goes to stdout by default; use `-o <dir>` to save to file
- Binary formats (docx) require `-o` flag (cannot stream to stdout)
- All progress/status messages go to stderr
- MinerU is an open-source project by OpenDataLab (Shanghai AI Lab): https://github.com/opendatalab/MinerU
