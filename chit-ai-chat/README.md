# Chit — AI Chat Interface

A single-file, browser-based AI chat app. No build step, no backend. Open `index.html`, point it at an LLM gateway, and chat.

**Current version:** Sprint 9 (19 client-side features)

## Screenshots

| Chat | Connection settings |
|---|---|
| ![Chat interface](docs/screenshots/chat-interface.png) | ![Connection settings](docs/screenshots/connection-settings.png) |

## How it works

```
Browser (index.html)  ──►  Your gateway (e.g. OmniRoute)  ──►  Model provider
      Chit UI              POST {base URL}/messages            (Claude, GPT, ...)
```

- Chit is **100% client-side**. It has no server of its own.
- Every message is sent to the **Gateway Base URL** you set in Settings, as `POST {baseUrl}/messages` (Anthropic-style format).
- Conversations, folders and settings are saved in the browser's `localStorage`.

## Quick start

| Step | Action |
|---|---|
| 1 | Clone the repo: `git clone https://github.com/<your-username>/chit-ai-chat.git` |
| 2 | Open `index.html` in Chrome or Edge (double-click it) |
| 3 | Click **Settings** and enter your **Gateway Base URL** (example: `http://localhost:20128/v1`) |
| 4 | Enter your **Gateway API Key** and choose the **Auth scheme** (`x-api-key` or `Bearer`) |
| 5 | Click **Test connection** |
| 6 | Add models to the **Model list** (first entry is the default), then start chatting |

> Your gateway must allow browser requests (CORS) from the page origin.

## Connection settings

| Setting | Options / notes |
|---|---|
| Credential kind | Static API key, Environment variable, Credential helper |
| Gateway base URL | Full URL of your inference endpoint |
| Gateway API key | Hidden by default, can be swapped any time |
| Auth scheme | `x-api-key` or `Authorization: Bearer` |
| Model list | Models shown in the picker; first one is the default |

## Features

| Area | Features |
|---|---|
| **Chat** | Multi-model picker, message editing, message pagination, rich text formatting, formatting options, auto-suggestions while typing |
| **Organization** | Folders (right-click, dropdown, drag & drop), favorites and pinning, auto-generated titles, search across all conversations |
| **Messages** | Copy, share link, pin important messages, thumbs up/down feedback |
| **Files** | Attach files, PDF text extraction, image analysis, OCR (Tesseract.js), URL content fetching |
| **Artifacts** | Side panel for generated code and documents, syntax highlighting, enhanced Markdown |
| **Sharing** | Link-based conversation sharing |
| **Reliability** | Offline support (service worker), error recovery, audit logging, multi-user profiles |
| **Appearance** | Dark / light theme toggle, saved user preferences |
| **Sprint 9 tools** | File editing, multi-file operations, advanced XLSX, PowerPoint creation, PDF manipulation, spreadsheet formulas, presentations, interactive widgets, visualizations, context preservation, session management, code linting, design guidance, error fixing |

## Built with

Plain HTML, CSS and JavaScript, plus these libraries loaded from CDNs:

| Purpose | Library |
|---|---|
| PDF read / create / edit | PDF.js, jsPDF, pdf-lib |
| Spreadsheets | SheetJS, Formula.js |
| Word / PowerPoint | Docxtemplater + PizZip, PptxGenJS |
| Charts | Chart.js |
| OCR | Tesseract.js |
| Code | Highlight.js, ESLint (browser bundle) |

> An internet connection is needed on first load so these libraries can download.

## Project structure

```
chit-ai-chat/
├── index.html              # the whole app
├── docs/screenshots/       # images used in this README
├── .gitignore
└── README.md
```

## Notes

- **"Do you have a backend?"** No. Chit only talks to the gateway you configure. The reply in the screenshot comes from the underlying model, not from a Chit server.
- **Security:** settings are stored in your browser's `localStorage`. Don't use a production key on a shared computer, and never commit a real key to this repo.

## Roadmap

- Split `index.html` into separate CSS / JS files
- Add a license

## Author

Built by CHIT.
