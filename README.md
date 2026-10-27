# MEMORA AI — Personal Memory Management System

MEMORA AI is an offline-first, intelligent desktop workspace designed to help users organize, search, explore, and manage their digital information from a single interface.

Instead of manually navigating through countless folders and files, MEMORA creates a searchable local index of files and provides a unified workspace for discovering information, viewing documents, and interacting with locally running AI models.

**Your files. Your computer. Your AI. No cloud required.**

## Key Features

- **Intelligent File Management:** Index folders and supported drives to create a unified view of digital information.
- **Local Search:** Search files by name, path, and supported file contents.
- **Content-Based Discovery:** Search extracted text from supported documents, including PDF, DOCX, XLSX, XLS, and CSV files.
- **Visual Memory Exploration:** Explore indexed information through a visual memory graph, timeline, and insights interface.
- **Built-in File Preview:** Preview supported documents, images, audio, video, and text/code files inside the application.
- **Local AI Integration:** Supports a local AI architecture using `llama.cpp` for packaged inference and Ollama as a development fallback.
- **Offline-First Architecture:** Designed to work without cloud APIs or mandatory online services.
- **Desktop Experience:** Built with Electron to provide a native desktop workspace.
- **Keyboard Shortcuts:** Quickly access the search workspace using `Ctrl + Space`.
- **Privacy-Focused Design:** File indexing is performed locally, and original files remain in their existing locations.

## How MEMORA Works

1. **Import:** Select a folder or supported drive to index.
2. **Index:** MEMORA collects file metadata and indexes supported content locally.
3. **Search:** Find information using filenames, paths, or extracted document text.
4. **Explore:** Navigate indexed information through the application's visual interfaces.
5. **Preview:** Open supported files inside MEMORA or use the operating system's default application.
6. **Local AI:** Connect the application to a configured local inference runtime for AI-powered functionality.

MEMORA indexes information rather than copying entire drives. Generated and system-heavy directories are excluded from indexing to reduce unnecessary processing.

## Technology Stack

| Technology | Purpose |
|---|---|
| React | User interface |
| TypeScript | Type safety and application logic |
| Vite | Development server and frontend build |
| Electron | Desktop application runtime |
| Node.js | Desktop-side operations and integration |
| llama.cpp | Local AI inference for configured packaged builds |
| Ollama | Optional local AI runtime during development |
| PDF Parse | PDF text extraction |
| Mammoth | DOCX text extraction |
| XLSX | Spreadsheet processing |
| Framer Motion | Interface animations |
| Lucide React | Icons |

## Project Structure

```text
MEMORA_AI/
├── electron/
│   ├── main.cjs
│   ├── offline-ai.cjs
│   └── preload.cjs
├── models/
│   ├── manifest.json
│   └── README.md
├── scripts/
│   └── verify-offline.ps1
├── src/
│   ├── components/
│   ├── data/
│   ├── lib/
│   ├── App.tsx
│   ├── index.css
│   └── main.tsx
├── index.html
├── package.json
├── package-lock.json
├── tsconfig.json
├── vite.config.js
└── README.md
```

## Getting Started

### Prerequisites

Install the following before running MEMORA:

- Node.js and npm
- A compatible Windows environment for the intended desktop build
- Optional: Ollama and a downloaded local model for AI functionality during development

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/MEMORA_AI.git
cd MEMORA_AI
```

Replace `YOUR_USERNAME` with your GitHub username and `MEMORA_AI` with your repository name.

### 2. Install Dependencies

```bash
npm install
```

### 3. Run the Application

```bash
npm run dev
```

This command starts the Vite development server and launches Electron.

To run only the web development server:

```bash
npm run dev:web
```

### 4. Build the Frontend

```bash
npm run build
```

The production frontend files are generated in the `dist/` directory.

### 5. Check TypeScript

```bash
npm run typecheck
```

### 6. Package for Windows

```bash
npm run package:win
```

The Windows installer and portable application artifacts are written to the `release/` directory, subject to successful packaging and the required build environment.

## Configuring Local AI

MEMORA supports a local AI integration based on `llama.cpp`.

For a packaged build, the expected model configuration uses:

```text
models/
├── manifest.json
├── Qwen3-4B-Q4_K_M.gguf
└── runtime/
    └── win-x64/
        └── llama-server.exe
```

Configure `models/manifest.json` with `bundled: true` only after the model and runtime have been installed at the expected paths and verified.

During development, MEMORA can use an available Ollama instance running locally at `127.0.0.1:11434`.

**Note:** The repository configuration does not include the model weights or the `llama-server.exe` runtime. Local AI inference therefore requires additional setup. A fresh clone should not be assumed to provide a ready-to-use AI experience.

Check the model and runtime licenses before redistributing them.

## Privacy and Offline Operation

MEMORA is designed around local-first information management.

- File metadata and indexed content are handled locally.
- The application does not require cloud AI API keys.
- Local AI inference can run through a supported local runtime.
- Original files are not copied merely for indexing.
- Destructive file operations should require explicit user confirmation.
- The packaged application is designed to restrict non-local HTTP/HTTPS requests.

Offline operation should be tested on the actual packaged build with network connectivity disabled. Local AI availability depends on the required runtime and model being correctly configured.

## Project Objective

The goal of MEMORA AI is to make personal digital information easier to retrieve, understand, and manage.

As the number of documents, projects, downloads, and other digital resources grows, traditional folder-based navigation becomes increasingly inefficient. MEMORA addresses this challenge by combining local indexing, content search, visual exploration, document previews, and optional local AI into one desktop workspace.

The long-term vision is to create a personal digital memory layer that helps users rediscover information they already have instead of repeatedly searching for it manually.

## Future Scope

Potential areas for further development include:

- Semantic search across documents.
- AI-generated summaries of indexed content.
- Context-aware retrieval across projects and files.
- Improved duplicate detection and organization.
- Advanced relationships between files in the memory graph.
- Support for additional document formats and richer metadata extraction.
- Configurable local AI models and inference settings.

These are potential extensions and should not be considered implemented features unless verified in the relevant release.

## Development and Contributions

Contributions, suggestions, and bug reports are welcome.

When reporting a bug, include the operating system, steps to reproduce the issue, expected behavior, and any relevant error messages. Avoid sharing private documents, credentials, or sensitive file contents.

## License

No repository-wide open-source license is specified in the supplied project configuration. Add a `LICENSE` file before publishing the project under an open-source license. Third-party dependencies and AI model/runtime components may have separate license requirements.

---

**MEMORA AI — Making your digital information searchable, connected, and easier to remember.**
