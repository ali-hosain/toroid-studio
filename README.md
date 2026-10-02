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

Toroid Studio is a full-featured mobile IDE for Android that brings desktop-class development tools to your phone. Unlike simple code editors, Toroid Studio includes a real Python runtime and debugger, Language Server Protocol (LSP) support, a full Git workflow, AI pair-programming, and one-tap deployment to Netlify or Vercel — all built natively for Android.

---

## ✨ Features

### 🤖 AI Pair-Programming (Claude AI)
- **AI Chat Panel** — Ask questions, explain code, fix errors with streaming responses; copy or insert code blocks straight into the editor
- **Inline Ghost-Text Completions** — Copilot-style suggestions as you type (400ms debounce, rate-limited)
- **Agentic Code Editing** — AI proposes multi-file changes and terminal commands; each one waits for your Approve/Reject (an optional, off-by-default auto-approve setting exists for projects you can easily revert)
- **Follow-up conversations** — Continue an agent run or a chat with follow-up messages; the agent remembers the earlier work
- **Searchable history** — Every chat and agent run is saved on your device; search, resume or delete them any time
- **AI Commit Message Generator** — Conventional-commit messages from your staged diff
- **AI Code Review** — Pre-commit issue detection (bugs, edge cases, style)
- **AI Test Generation** — Generate unit tests for the open file (approval-gated)
- **AI Docstring Generator** — Auto-generate docstrings/comments (approval-gated)
- **Ask your codebase** — Ask "where is X handled?" and jump to the relevant files (keyword-ranked, runs on-device)
- **BYOK Model** — Bring your own Claude API key; your code never touches our servers
- **OpenRouter (optional)** — Use OpenRouter as an alternative provider, with a live model catalog, free-model filter and clear paid-model prices

### 📝 Code Editor
- Syntax highlighting for Python, JavaScript, TypeScript, Kotlin, Java, HTML/CSS, JSON, XML, YAML, Markdown, Shell and more
- Multiple tabs with unsaved-change indicators, restored when you reopen the app
- Split-screen editing (side-by-side or top/bottom)
- Line numbers, wrap toggle, spaces-for-Tab
- One-tap **Black** formatting for Python (Prettier for JS/TS with the optional Node runtime), plus format-on-save
- **HTML preview** — tap ▶ on an `.html` file to see it with its CSS, JS and images
- 3 custom themes: **Toroid Dark**, **Toroid Midnight**, **Toroid Light**
- Font size, tab width, and editor preferences
- Run & debug: **Python today**, more languages coming soon. Other languages get full editing, highlighting, Git and AI help

### 🔍 Language Server Protocol (LSP)
- **Python** — Real diagnostics, go-to-definition, hover docs, autocomplete and **rename symbol** (via a custom Jedi/pyflakes server running on-device)
- **TypeScript/JavaScript** — via `typescript-language-server` (needs the optional Node runtime, not included in the current Play Store build)
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
- Multiple terminal sessions (tab strip), with a ^C button to stop a running command
- ANSI color support
- Working directory synced with open workspace
- Run scripts directly against project files
- **Local web server** — one command-palette tap runs `python3 -m http.server` in your project and opens it in the browser, so websites load with their CSS and JS

### 🐍 Python Runtime
- Real CPython 3.12 via Chaquopy (bionic-linked, no PRoot)
- `python3 script.py` with live output in terminal
- Full stdlib, including native modules: `json`, `math`, `datetime`, `socket`, `hashlib`, `ssl`, `sqlite3`, `urllib`, `http.server`
- In-app **pip package manager** — install pure-Python packages with a UI
- Writes to `requirements.txt` automatically

### 🟨 Node.js Runtime (Optional, coming soon)
- Planned for a future update: `node script.js` with live terminal output
- Not included in the current Play Store build, to keep the app small

### 🌿 Git & Source Control
- Clone (HTTPS + GitHub PAT, stored encrypted) or initialize a repository
- Add a remote, stage, commit, push, pull
- Branch create / switch / merge / delete (unmerged branches need an explicit force-delete)
- Stash with apply, pop and drop
- Unified diff viewer
- **Merge conflict UI** — Ours / Theirs / Base view; keep one side, both, or edit the result by hand
- Commit history labelled by branch
- Clear error messages that include GitHub's own reason (e.g. a token without write access)
- AI commit message generation
- AI pre-commit code review

### ☁️ Cloud Sync (Pro, coming soon)
- Google Drive sync for app-managed Projects
- Conflict handling: conflicting-copy fallback (never silent overwrite)
- Per-project opt-in with explicit disclosure before first sync
- Metadata sync: open tabs + cursor positions

### 🚀 Deploy
- One-tap deploy of static HTML/CSS/JS projects to **Netlify** or **Vercel**, using your own account
- Deploy status log + public live URL on success (Copy / Open), and Redeploy to the same site
- Tokens stored encrypted (never logged)

### 📦 Project Tools
- App-managed Projects with real filesystem paths (Git/terminal compatible)
- SAF folder support for plain editing; import an opened folder as a Project
- Export a project to a device folder, share it as a `.zip`, or delete it
- Project templates: Empty, Python script, Node.js script, static HTML/CSS/JS
- Global search & replace (regex, per-file grouping, Replace All)
- Command palette with fuzzy search
- Snippets manager (user-defined + Python defaults)

### 🔒 Security
- API keys and tokens stored in Android Keystore (AES-GCM, hardware-backed)
- Zero plaintext key logging — verified via logcat grep
- HTTPS-only (`usesCleartextTraffic="false"`)
- AI-driven file changes and commands require Approve/Reject by default (auto-approve is opt-in and off by default)

### 📊 Productivity
- Home screen widget (recent projects, tap-to-open)
- Productivity dashboard (commits, files edited, coding time — local only)
- First-run toolbar tour (replayable from Settings)
- Every Settings action confirms success or shows the error
- In-app feedback & bug reporting (Firebase Firestore, only when you choose to send; screenshots are never attached unless you choose to)
- In-app Help & Features guide
- Optional donations via Google Play to support development — unlocks nothing
- Accessibility: TalkBack labels, font-scale support, WCAG AA contrast, haptic feedback

---

## 🏗️ Architecture

| Layer | Technology |
|---|---|
| UI | Jetpack Compose + Material 3 |
| Editor | Sora Editor (syntax highlighting, Toroid themes) |
| DI | Hilt |
| Database | Room (workspaces, tabs, snippets, stats, chat & agent history) |
| AI | Claude API (`claude-sonnet-4-6` / `claude-haiku-4-5`) via `AiProvider` interface; optional OpenRouter |
| LSP | Custom JSON-RPC client mirroring LspClient architecture |
| Debugger | DAP client (`DapClient`) + `debugpy` via Chaquopy |
| Git | JGit 6.10 (pure Java, no shell dependency) |
| Python | Chaquopy (bionic CPython 3.12) |
| Node.js | nodejs-mobile v18 (optional build flag, not in the current Play build) |
| Billing | Google Play Billing v8 |
| Sync | Google Drive REST API (user's own account) |
| Deploy | Netlify API + Vercel API (user's own account) |
| Crash & Analytics | Firebase Crashlytics + Analytics (separate opt-out toggles) |
| Feedback | Firebase Firestore (sent only on request) |

---

## 💛 Support

Toroid Studio is built by one developer. If it helps you, you can leave an optional one-time donation in the app (**Settings → Support Toroid Studio**). Donations are handled by Google Play and unlock nothing — every feature stays free for everyone.

---

## 📲 Download

> **Coming soon to Google Play Store.**

📖 [Full User Guide](./USER_GUIDE.md)

---

## 🔐 Privacy

Toroid Studio never uploads your code to our servers and never sells your data. Your code leaves your phone only when you use a feature that sends it to a service you chose — your AI provider, your Git remote, your Google Drive, or your Netlify/Vercel account. Optional anonymous crash reports and usage analytics (Firebase) can be turned off any time in **Settings → Privacy**.

👉 [Privacy Policy](https://ali-hosain.github.io/toroid-studio/privacy-policy.html)

---

## 👨‍💻 Developer

**Ali Hosain** — Android, iOS & Web Developer from Rajshahi, Bangladesh.

- GitHub: [@ali-hosain](https://github.com/ali-hosain)
- Email: [hello@alihosain.com](mailto:hello@alihosain.com)

---

## 📄 License

© 2026 Ali Hosain. All rights reserved.

Open-source components used in this project are listed in **Settings → About → Open Source Licenses**.
