# WebDevOS

<div align="center">

**Browser-Based Development Environment — Your Web IDE in the Cloud**

[![Next.js](https://img.shields.io/badge/Next.js-16+-black?logo=next.js&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Monaco Editor](https://img.shields.io/badge/Monaco_Editor-0.52-007ACC?logo=visual-studio-code&logoColor=white)](https://microsoft.github.io/monaco-editor/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

[🇬🇧 English](#-webdevos) • [🇮🇷 فارسی](README.fa.md) • [📖 Documentation](#-documentation) • [🚀 Quick Start](#-quick-start) • [🤝 Contributing](#-contributing)

</div>

---

## 🌟 Overview

**WebDevOS** is a full-featured, browser-based Integrated Development Environment (IDE) that brings the power of VS Code to the web. Built with **Next.js 16**, **React 19**, **TypeScript**, **Tailwind CSS v4**, and **Monaco Editor**, it provides a Persian-first development experience with real-time collaboration, cloud sync, and instant preview.

### 🎯 Why WebDevOS?

| Problem | WebDevOS Solution |
|---------|-------------------|
| Need VS Code but can't install locally | **Browser-based** — runs anywhere with a browser |
| No Persian RTL code editor | **Full RTL support** — Vazirmatn, Persian comments |
| Collaboration is complex | **Real-time** — Yjs + WebRTC / WebSocket |
| Environment setup takes time | **Instant** — preconfigured templates, cloud sync |

---

## ✨ Features

### 🖥️ **Code Editor (Monaco)**
- **Full VS Code compatibility** — same engine, same shortcuts
- **Multi-language support** — TS/JS, Python, Go, Rust, CSS, HTML, JSON, Markdown
- **IntelliSense** — TypeScript, CSS, HTML language services
- **Themes** — 50+ themes (VS Code, Dracula, One Dark, Persian-optimized)
- **Vim/Emacs keybindings** — Optional extensions
- **Persian RTL** — Right-to-left editing for comments/docs

### 📁 **File System**
- **Virtual FS** — In-memory with IndexedDB persistence
- **Git integration** — Clone, commit, push, pull via isomorphic-git
- **Cloud sync** — Supabase/Firebase real-time sync
- **Workspaces** — Multi-root, project templates

### 🚀 **Terminal & Tasks**
- **xterm.js** — Full terminal emulation
- **WebAssembly runtimes** — Python (Pyodide), Node.js (WebContainer), Deno
- **Task runner** — npm scripts, custom commands
- **Persian locale** — Jalali dates, Persian numerals in output

### 🌐 **Live Preview**
- **iframe sandbox** — Secure preview with CSP
- **Hot reload** — Vite/HMR for instant updates
- **Device toolbar** — Mobile, tablet, desktop viewports
- **Network inspector** — Request/response logging

### 🤝 **Real-Time Collaboration**
- **Yjs CRDT** — Conflict-free concurrent editing
- **Awareness** — Cursors, selections, user presence
- **Comments** — Threaded code reviews
- **Voice/Video** — WebRTC integration (planned)

### 🌍 **Persian-First Experience**
| Feature | Implementation |
|---------|----------------|
| **RTL UI** | CSS logical properties, Tailwind RTL |
| **Editor RTL** | Monaco RTL support for comments |
| **Typography** | Vazirmatn UI + JetBrains Mono (code) |
| **Calendar** | Jalali dates in git history, tasks |
| **Numerals** | Persian formatting in UI (code stays Latin) |
| **Keyboard** | Persian layout awareness |

---

## 🏗️ Architecture

### Tech Stack
| Layer | Technology | Version |
|-------|------------|---------|
| **Framework** | Next.js (App Router) | 16+ |
| **Runtime** | React | 19 |
| **Language** | TypeScript | 5 (Strict) |
| **Styling** | Tailwind CSS | v4 |
| **Editor** | Monaco Editor | 0.52+ |
| **Terminal** | xterm.js + addons | 5.x |
| **Collaboration** | Yjs + y-websocket | 13.x |
| **File System** | isomorphic-git + IndexedDB | Latest |
| **Preview** | WebContainer API / iframe | Latest |
| **State** | Zustand + Jotai | Latest |
| **Testing** | Vitest + Playwright | Latest |
| **Deployment** | Vercel / Cloudflare Pages | - |

### Project Structure
```
WebDevOS/
├── public/
│   ├── workers/                # Web Workers (TS, Python, WASM)
│   ├── wasm/                   # WebAssembly binaries
│   └── themes/                 # Monaco themes
├── src/
│   ├── app/
│   │   ├── (auth)/             # Auth routes
│   │   ├── (ide)/              # IDE routes
│   │   │   ├── editor/         # Monaco editor
│   │   │   ├── terminal/       # xterm.js terminal
│   │   │   ├── explorer/       # File explorer
│   │   │   ├── git/            # Git panel
│   │   │   ├── preview/        # Live preview
│   │   │   ├── extensions/     # Extension marketplace
│   │   │   └── settings/       # User settings
│   │   ├── api/                # API routes
│   │   │   ├── sync/           # Cloud sync
│   │   │   ├── collab/         # Yjs WebSocket
│   │   │   ├── terminal/       # Terminal WebSocket
│   │   │   └── preview/        # Preview proxy
│   │   ├── globals.css         # Global styles + Tailwind v4
│   │   ├── layout.tsx          # Root layout
│   │   └── page.tsx            # Landing page
│   ├── components/
│   │   ├── ui/                 # shadcn/ui components
│   │   ├── editor/             # Monaco wrapper, tabs
│   │   ├── terminal/           # xterm wrapper
│   │   ├── explorer/           # File tree, breadcrumbs
│   │   ├── git/                # Git panel, diff view
│   │   ├── preview/            # Preview iframe, toolbar
│   │   ├── collab/             # Cursors, comments, presence
│   │   └── layout/             # Panels, resizers, tabs
│   ├── lib/
│   │   ├── monaco/             # Monaco configuration
│   │   ├── terminal/           # Terminal setup
│   │   ├── collab/             # Yjs providers
│   │   ├── fs/                 # Virtual file system
│   │   ├── git/                # Isomorphic-git wrapper
│   │   ├── preview/            # Preview sandbox
│   │   ├── persian/            # Persian utilities
│   │   └── utils/              # Shared utilities
│   ├── hooks/                  # Custom React hooks
│   ├── store/                  # Zustand/Jotai stores
│   └── types/                  # TypeScript types
├── .env.example
├── package.json
├── tsconfig.json
└── next.config.ts
```

---

## 🚀 Quick Start

### Prerequisites
- **Node.js** v26+
- **npm** 11+
- **Supabase/Firebase** for cloud sync (optional)
- **WebSocket server** for collaboration (optional)
- **Vercel/Cloudflare** for deployment

### Installation
```bash
# Clone the repository
git clone https://github.com/mohammadhossein-asadi/WebDevOS.git
cd WebDevOS

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with your credentials

# Start development server
npm run dev
```

### Environment Variables
```env
# App
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_APP_NAME="WebDevOS"

# Database (for sync, users)
DATABASE_URL=postgresql://...
# Or Supabase
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
SUPABASE_SERVICE_ROLE_KEY=...

# Auth
NEXTAUTH_SECRET=your-secret-min-32-chars
# OAuth: GitHub, GitLab, Bitbucket

# Collaboration (Yjs WebSocket)
COLLAB_WS_URL=ws://localhost:1234
# Or use y-supabase / y-firestore

# Terminal (WebContainer)
WEB_CONTAINER_URL=https://boot.webcontainer.io

# Storage (for projects)
AWS_S3_BUCKET=webdeivos-projects
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
```

---

## 🛠️ Development

### Available Commands
```bash
npm run dev          # Start dev server with Turbopack
npm run build        # Production build
npm run start        # Start production server
npm run lint         # ESLint
npm run typecheck    # TypeScript check
npm test             # Run Vitest tests
npm run test:watch   # Watch mode
npm run test:e2e     # Playwright e2e tests

# Collaboration server (separate process)
npm run collab:server
```

### Monaco Configuration
```typescript
// src/lib/monaco/config.ts
import * as monaco from 'monaco-editor';

export function configureMonaco() {
  // Persian RTL for comments
  monaco.languages.setLanguageConfiguration('typescript', {
    comments: { lineComment: '//', blockComment: ['/*', '*/'] },
    wordPattern: /(-?\d*\.\d\w*)|([^\`\~\!\@\#\%\^\&\*\(\)\-\=\+\[\{\]\}\\\|\;\:\'\"\,\.\<\>\/\?\s]+)/g,
  });

  // Custom Persian theme
  monaco.editor.defineTheme('persian-dark', {
    base: 'vs-dark',
    inherit: true,
    rules: [
      { token: 'comment', foreground: '6A9955', fontStyle: 'italic' },
      { token: 'keyword', foreground: 'C586C0' },
    ],
    colors: {
      'editor.background': '#1E1E1E',
      'editor.foreground': '#D4D4D4',
    },
  });
}
```

### Yjs Collaboration Setup
```typescript
// src/lib/collab/provider.ts
import * as Y from 'yjs';
import { WebsocketProvider } from 'y-websocket';

export function createCollabProvider(docName: string, userId: string) {
  const ydoc = new Y.Doc();
  const provider = new WebsocketProvider(
    process.env.NEXT_PUBLIC_COLLAB_WS_URL!,
    docName,
    ydoc,
    { connect: true }
  );

  // Awareness (cursors, selections)
  provider.awareness.setLocalStateField('user', {
    id: userId,
    name: 'Persian User',
    color: '#' + Math.floor(Math.random() * 16777215).toString(16),
  });

  return { ydoc, provider };
}
```

---

## 🧪 Testing
```bash
# Unit tests (editor, terminal, git, fs)
npm test

# E2E tests (full IDE workflows)
npm run test:e2e

# Collaboration tests (multi-user)
npm run test:collab
```

**Test Coverage Areas:**
- Monaco editor initialization & language services
- Terminal PTY & command execution
- Git operations (commit, push, pull, diff)
- File system CRUD + persistence
- Yjs sync & awareness
- Preview sandbox security

---

## 📚 Documentation
| Document | Description |
|----------|-------------|
| [Architecture](docs/ARCHITECTURE.md) | System design & data flow |
| [Monaco Integration](docs/MONACO.md) | Editor setup, themes, extensions |
| [Terminal](docs/TERMINAL.md) | xterm.js, WebContainer, WASM runtimes |
| [Collaboration](docs/COLLABORATION.md) | Yjs, WebSocket, awareness |
| [File System](docs/FILESYSTEM.md) | Virtual FS, IndexedDB, git |
| [Persian UX](docs/PERSIAN_UX.md) | RTL, fonts, calendar guidelines |
| [Deployment](docs/DEPLOYMENT.md) | Vercel, Cloudflare, Docker |

---

## 🚀 Deployment

### Vercel (Recommended)
```bash
npm i -g vercel
vercel --prod
```
**Configure:** WebSocket for collaboration (use separate service like Railway/Render).

### Cloudflare Pages + Workers
```bash
# wrangler.toml
[build]
command = "npm run build"
output = ".next"

# WebSocket for collaboration
[[durable_objects.bindings]]
name = "COLLAB"
class_name = "CollabRoom"

# Deploy
wrangler pages deploy .next
```

### Docker (Self-Hosted)
```dockerfile
FROM node:26-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000 1234
CMD ["sh", "-c", "npm run collab:server & npm start"]
```

---

## 🔒 Security
- **Sandboxed preview** — iframe with strict CSP, no parent access
- **Terminal isolation** — WebContainer / WASM, no host access
- **Git credentials** — Stored encrypted, never in client
- **Collaboration** — E2E encryption for awareness (planned)
- **CSP headers** — Strict script/style sources
- **Dependency scanning** — GitHub Dependabot

---

## 🤝 Contributing
We welcome contributions to make web development accessible!

### Quick Contribution Steps
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-feature`
3. Make your changes
4. Run checks: `npm run lint && npm run typecheck && npm test`
5. Commit: `git commit -m "feat: add Persian keyboard layout"`
6. Push: `git push origin feature/new-feature`
7. Open a Pull Request

### Development Guidelines
- Follow **Persian-first UX** principles
- Maintain **TypeScript strict mode** compliance
- Write **tests** for new functionality
- Keep **commits atomic** and **messages conventional**
- Optimize **bundle size** (Monaco lazy loading)

---

## 📋 Roadmap

### ✅ Phase 1 - Foundation
- [x] Next.js 16 + React 19 + TypeScript setup
- [x] Tailwind CSS v4 + Vazirmatn + RTL
- [x] Monaco Editor integration

### 🔄 Phase 2 - Core IDE
- [ ] File explorer with virtual FS
- [ ] Monaco editor with tabs, IntelliSense
- [ ] xterm.js terminal with WebContainer
- [ ] Git panel (isomorphic-git)

### 📅 Phase 3 - Preview & Sync
- [ ] Live preview with hot reload
- [ ] Cloud sync (Supabase/Firebase)
- [ ] Project templates (React, Vue, Next, Python, Go)
- [ ] Settings & themes

### 🌟 Phase 4 - Collaboration
- [ ] Yjs real-time editing
- [ ] Cursors, selections, presence
- [ ] Threaded comments
- [ ] Voice/video calls (WebRTC)

### 🚀 Phase 5 - Advanced
- [ ] Extension marketplace
- [ ] AI code assistant (local LLM)
- [ ] Mobile-responsive IDE
- [ ] Debug adapter protocol (DAP)
- [ ] Container-based runtimes (Docker)

---

## 📄 License
**MIT License** — See [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments
- **Monaco Editor** — VS Code editor by Microsoft
- **xterm.js** — Terminal emulator by SourceLair
- **Yjs** — CRDT framework by Kevin Jahns
- **WebContainer** — Browser Node.js by StackBlitz
- **isomorphic-git** — Pure JS git by William Hilton
- **Tailwind CSS** — Utility-first styling
- **Vazirmatn Font** — Persian typography by [Rastikerdar](https://github.com/rastikerdar/vazirmatn)
- **VS Code** — Inspiration for UX patterns

---

## 📞 Support & Community
- **Documentation**: [docs/](docs/)
- **Issues**: [GitHub Issues](https://github.com/mohammadhossein-asadi/WebDevOS/issues)
- **Discussions**: [GitHub Discussions](https://github.com/mohammadhossein-asadi/WebDevOS/discussions)
- **Discord**: [WebDevOS Community](https://discord.gg/webdeivos)
- **Email**: hello@webdeivos.dev

---

<div align="center">

**Built with ❤️ for developers who code in the browser**

[🇬🇧 English](README.md) • [🇮🇷 فارسی](README.fa.md) • [⭐ Star us on GitHub](https://github.com/mohammadhossein-asadi/WebDevOS)

</div>