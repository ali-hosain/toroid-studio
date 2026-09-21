# Toroid Studio — AI-Powered Mobile IDE

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white"/>
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white"/>
  <img src="https://img.shields.io/badge/AI-Claude_API-D97706?style=for-the-badge&logo=anthropic&logoColor=white"/>
  <img src="https://img.shields.io/badge/Status-Coming_Soon-FF6B6B?style=for-the-badge"/>
</p>

<p align="center">
  <b>A production-grade Android IDE with native Claude AI integration.</b><br/>
  Code, debug, and deploy — entirely from your phone.
</p>

---

## 📱 What is Toroid Studio?

Toroid Studio is a full-featured mobile IDE for Android that brings desktop-class development tools to your phone. Unlike simple code editors, Toroid Studio includes a real Python debugger, Language Server Protocol (LSP) support, Git workflow, AI pair-programming, and one-tap deployment — all built natively for Android.

---

## ✨ Features

### 🤖 AI Pair-Programming (Claude AI)
- **AI Chat Panel** — Ask questions, explain code, fix errors with streaming responses
- **Inline Ghost-Text Completions** — Copilot-style suggestions as you type (400ms debounce, rate-limited)
- **Agentic Code Editing** — AI proposes multi-file changes; every mutation requires your explicit Approve/Reject
- **AI Commit Message Generator** — Conventional-commit messages from your staged diff
- **AI Code Review** — Pre-commit issue detection (bugs, edge cases, style)
- **AI Test Generation** — Generate unit tests for selected functions (approval-gated)
- **AI Docstring Generator** — Auto-generate docstrings/comments (approval-gated)
- **Semantic Codebase Search** — Ask "where is X handled?" and jump to the answer
- **BYOK Model** — Bring your own Claude API key; your code never touches our servers

### 📝 Code Editor
- Syntax highlighting for Python, JavaScript, TypeScript, Kotlin, Java, HTML/CSS, JSON, Markdown and more
- Multiple tabs with unsaved-change indicators
- Split-screen editing (side-by-side or top/bottom)
- Multi-cursor support (where available)
- Code folding, line numbers, wrap toggle
- 3 custom themes: **Forge Dark**, **Forge Midnight**, **Forge Light**
- Font size, tab width, and editor preferences

### 🔍 Language Server Protocol (LSP)
- **Python** — Real diagnostics, go-to-definition, hover docs, autocomplete (via custom Jedi/pyflakes server)
- **TypeScript/JavaScript** — Full LSP via `typescript-language-server` (requires Node runtime)
- Squiggly underlines for errors/warnings
- Tap-to-see-message diagnostics
- Back-navigation stack for go-to-definition

### 🐛 Python Debugger
- Real `debugpy` integration via Debug Adapter Protocol (DAP)
- Breakpoint gutter (tap to toggle)
- Step Over / Step Into / Step Out / Continue / Stop controls
- Variables panel (locals + globals at current frame)
- Call Stack panel

### 🖥️ Embedded Terminal
- Native PTY — runs `/system/bin/sh` in the app sandbox
- Multiple terminal sessions (tab strip)
- ANSI color support
- Working directory synced with open workspace
- Run scripts directly against project files

### 🐍 Python Runtime
- Real CPython 3.12 via Chaquopy (bionic-linked, no PRoot)
- `python3 script.py` with live output in terminal
- Full stdlib: `json`, `math`, `datetime`, `hashlib`, `ssl`, `sqlite3`, `urllib`
- In-app **pip package manager** — install pure-Python packages with a UI
- Writes to `requirements.txt` automatically

### 🟨 Node.js Runtime (Optional)
- `nodejs-mobile` v18 (arm64, opt-in to keep base APK small)
- `node script.js` with live terminal output
- `fs`, `crypto`, `require`, `https.get` all working

### 🌿 Git & Source Control
- Clone (HTTPS + GitHub PAT, stored encrypted)
- Stage, commit, push, pull
- Branch create / switch / delete
- Stash and pop
- Unified diff viewer
- **Merge conflict UI** — three-way view (Ours / Theirs / Base), hunk-level resolution
- Branch commit history graph
- AI commit message generation
- AI pre-commit code review

### ☁️ Cloud Sync (Pro)
- Google Drive sync for app-managed Projects
- Conflict handling: conflicting-copy fallback (never silent overwrite)
- Per-project opt-in with explicit disclosure before first sync
- Metadata sync: open tabs + cursor positions

### 🚀 Deploy
- One-tap Netlify deploy for static HTML/CSS/JS projects
- Deploy status log + live URL on success
- Netlify token stored encrypted (never logged)

### 📦 Project Tools
- App-managed Projects with real filesystem paths (Git/terminal compatible)
- SAF folder support for plain editing
- Project templates: Python script, Node script, static HTML/CSS/JS
- Global search & replace (regex, per-file grouping, Replace All)
- Command palette with fuzzy search
- Snippets manager (user-defined + Python defaults)

### 🔒 Security
- API keys stored in Android Keystore (AES-GCM, hardware-backed)
- Zero plaintext key logging — verified via logcat grep
- HTTPS-only (`usesCleartextTraffic="false"`)
- All AI-driven file mutations require explicit Approve/Reject before execution

### 📊 Productivity
- Home screen widget (recent projects, tap-to-open)
- Productivity dashboard (commits, files edited, coding time — local only)
- In-app feedback & bug reporting (Firebase Firestore backend, opt-in)
- Accessibility: TalkBack labels, font-scale support, WCAG AA contrast

---

## 🏗️ Architecture

| Layer | Technology |
|---|---|
| UI | Jetpack Compose + Material 3 |
| Editor | Sora Editor (syntax highlighting, Forge themes) |
| DI | Hilt |
| Database | Room (workspaces, tabs, snippets, stats) |
| AI | Claude API (`claude-sonnet-4-6` / `claude-haiku-4-5`) via `AiProvider` interface |
| LSP | Custom JSON-RPC client mirroring LspClient architecture |
| Debugger | DAP client (`DapClient`) + `debugpy` via Chaquopy |
| Git | JGit 6.10 (pure Java, no shell dependency) |
| Python | Chaquopy (bionic CPython 3.12) |
| Node.js | nodejs-mobile v18 (opt-in) |
| Billing | Google Play Billing v7 |
| Sync | Google Drive REST API (user's own account) |
| Deploy | Netlify API |
| Crash | Firebase Crashlytics (opt-out toggle) |
| Feedback | Firebase Firestore (opt-in) |

---

## 📲 Download

> **Coming soon to Google Play Store.**

📖 [Full User Guide](./USER_GUIDE.md)

---

## 🔐 Privacy

Toroid Studio does not collect, sell, or share your personal data or code.

👉 [Privacy Policy](https://ali-hosain.github.io/toroid-studio/privacy-policy.html)

---

## 👨‍💻 Developer

**Ali Hosain** — Android, iOS & Web Developer from Rajshahi, Bangladesh.

- GitHub: [@ali-hosain](https://github.com/ali-hosain)
- Email: [alihosain4c@gmail.com](mailto:alihosain4c@gmail.com)

---

## 📄 License

© 2026 Ali Hosain. All rights reserved.

Open-source components used in this project are listed in **Settings → About → Open Source Licenses**.
