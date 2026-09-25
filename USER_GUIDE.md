# Toroid Studio — User Guide

Toroid Studio is a code editor for Android with an AI pair-programmer, an agent
that can make multi-file changes (with your approval), a built-in terminal with
real Python and Node.js, and Git. This guide covers everything from first launch
to troubleshooting.

> **Short on time?** Read [Getting Started](#1-getting-started), then skim the
> [FAQ](#11-faq). The same feature overview is available inside the app at
> **Settings → Help & Features**.

**Contents**

1. [Getting Started](#1-getting-started)
2. [Editor](#2-editor)
3. [AI Features](#3-ai-features)
4. [Code Intelligence](#4-code-intelligence)
5. [Debugging](#5-debugging)
6. [Terminal & Runtimes](#6-terminal--runtimes)
7. [Git & Source Control](#7-git--source-control)
8. [Cloud Sync & Deploy](#8-cloud-sync--deploy)
9. [Productivity](#9-productivity)
10. [Settings & Privacy](#10-settings--privacy)
11. [FAQ](#11-faq)
12. [Troubleshooting](#12-troubleshooting)
13. [Known limitations](#13-known-limitations)

---

## 1. Getting Started

**Requirements:** an Android phone or tablet running **Android 8.0 (API 26) or
newer**. An internet connection is needed for AI features, cloning/pushing Git
repositories, installing Python packages, cloud sync and deploys — everything
else works offline (see [Can I use it offline?](#11-faq)).

### First launch

When you open the app for the first time you'll see a welcome screen explaining
the two ways to use AI:

- **Free — bring your own key (BYOK).** Everything is unlocked. You paste your
  own API key from an AI provider; it's stored encrypted on your device and used
  directly for AI calls. **You pay the provider** for what you use — Toroid
  Studio charges nothing for this.
- **Pro — managed key (coming soon).** A future option where we'd provide the
  key. It is not available to buy yet.

Tap **"I have a key — open Settings"** if you already have a key, or use the
button on the welcome screen to open Anthropic's key page. (The welcome screen
mentions Anthropic because it's the default; OpenRouter is set up in Settings,
below.) You can bring the
welcome screen back any time from **Settings → Privacy → Show the welcome screen
again**.

### Set up your AI key (BYOK)

You can use **Anthropic (Claude)** directly, or **OpenRouter**, a service that
gives access to many models (including some free ones). You need a key for
whichever provider you choose; you can save both and switch at any time.

**Option A — Anthropic**

1. Create a key at `console.anthropic.com` → Settings → API keys.
2. In the app: **Settings → AI → Provider: Anthropic (Claude)**.
3. Paste the key (it starts with `sk-ant-`) and tap **Save key**.

**Option B — OpenRouter**

1. Create a key at `openrouter.ai/keys`.
2. In the app: **Settings → AI → Provider: OpenRouter**.
3. Paste the key (it starts with `sk-or-`) and tap **Save key**.
4. Pick a model — see [Free vs paid models](#free-vs-paid-models-openrouter).

The screen confirms **"… API key saved."** once it's stored. You can remove a
key with **Remove key**. Keys are encrypted in the Android Keystore and are never
written to logs.

### Your first project

Toroid Studio works with two kinds of workspace:

| | **Toroid Project** | **Opened folder** |
|---|---|---|
| What it is | A real folder stored inside the app | A folder on your device you picked with Android's folder picker |
| Create it | **☰ → Projects → New** (choose a template) or clone from Git | **☰ → Files → Open folder** |
| Editing, search, snippets | Yes | Yes |
| Terminal, run, debug, pip, Git, Agent, Cloud Sync, Deploy | **Yes** | No — these need a real project path |

If you opened a folder and want the full toolset, use **☰ → Projects → Import
folder** to copy it into a Toroid Project.

**To make a project:** ☰ → **Projects** → **New** → name it and choose a
template — *Empty*, *Python script*, *Node.js script* or *Static web page* →
**Create**.

### A quick tour of the screen

**Top bar** (left to right): **☰** opens the side panel · file name and project
· **⚡** command palette · **💾** save (when there are unsaved changes) · **▶**
run the current file · split-editor icon · terminal icon · **⋮** more.

**⋮ menu:** Save all · Go to Definition · Back · Generate tests (AI) · Generate
docstring (AI) · Run with Debugger · Format Document · Settings. (Items appear
only when they apply to the open file.)

**Side panel (☰)** has a column of icons — each is a panel:

| Icon | Panel | Use it for |
|---|---|---|
| List | **Files** | Browse, create, open files and folders |
| 🔍 | **Search** | Find/replace across the project; ask AI about the codebase |
| Branch | **Git** | Commit, push, pull, branches, stash |
| Folder | **Projects** | Create, open, delete projects; sync and deploy icons |
| Bookmarks | **Snippets** | Reusable code snippets |
| Box | **Packages** | Python `pip` package manager |
| ✦ | **Assistant** | AI chat |
| Robot | **Agent** | AI agent for multi-file changes |
| Bug | **Debug** | Variables and call stack while debugging |

Tap **Back** to close the panel.

---

## 2. Editor

### Themes

Three built-in themes restyle both the app and the code editor:
**Toroid Dark**, **Toroid Midnight** (an even darker variant) and **Toroid
Light**. *Settings → Appearance.*

### Font size and layout

*Settings → Editor:*

- **Font size** — 8 to 32 sp.
- **Tab width** — 2 to 8 spaces.
- **Wrap long lines** — wrap instead of scrolling sideways.
- **Show line numbers** — the gutter on the left (you tap a line number to set a
  breakpoint, so keep it on if you debug).
- **Insert spaces for Tab** — insert spaces rather than a tab character.
- **Format on save** — see [Formatter](#formatter).

### Syntax highlighting

Files are highlighted according to their extension: Python, JavaScript /
TypeScript (including JSX/TSX), HTML, CSS/SCSS, JSON, Markdown, Kotlin, Java,
XML, YAML, shell, Gradle and `.properties`. Highlighting uses TextMate grammars.
A language whose grammar isn't included in your build simply opens as **plain
text** — you can still edit it; it just isn't coloured.

### Tabs

Every open file is a tab. A dot marks unsaved changes; the **×** closes a tab
(you're asked before discarding changes). Save with the **💾** button or
**⋮ → Save all**. Your open tabs are restored when you reopen the app.

### Split screen

Show two tabs at once, side by side or stacked, and drag the divider to resize
(the layout is remembered). You need **at least two open tabs**.

*Try it:* open two files, then tap the split icon in the top bar — or **⚡ →
Split Editor** / **Disable Split Editor**.

### Multi-cursor

**Not available.** The editor component Toroid Studio is built on doesn't offer
multi-cursor editing, so we can't add it yet. It will be revisited if that
changes.

---

## 3. AI Features

All AI features send only what they need to the provider **you** chose, using
**your** key — see [Is my code private?](#11-faq) for exactly what is sent.

### Chat assistant

*☰ → Assistant (✦).*

Type a question and send. The **open file and your current selection are
attached automatically** (a "Context:" line above the box shows what will be
sent). Answers stream in as they're written and support formatted text, tables
and code blocks; each code block has **Copy** and **Insert** buttons — Insert
puts it into the editor at the caret. Three **quick actions** sit above the box: **Explain this file**,
**Explain selection** and **Fix an error** (paste the error into the box first).

Tap **+** (top of the panel) to start a fresh chat, and the **stop** button to
cancel a reply that's in progress.

### Inline completions ("ghost text")

Pause while typing in a file and grey suggested code appears at the cursor with
**Accept** and **Dismiss** buttons. Suggestions are best-effort and
rate-limited (roughly one per second and a couple of dozen per minute), and any
failure — no key, offline, rate limit — is silent. Turn them off in **Settings →
AI → Inline AI completions**.

> **Tip:** if you use a free OpenRouter model, leave this off — the constant
> small requests can use up a free model's limited allowance quickly.

### Agent mode and the approval gate

*☰ → Agent (robot icon) → describe the task → **Start**.* Requires a Toroid
Project.

The agent works in a loop: it thinks, looks at your project, proposes a change,
and continues once you respond. It has four tools:

| Tool | What it does | Needs your approval? |
|---|---|---|
| `read_file` | Reads a file | No |
| `list_files` | Lists a folder | No |
| `write_file` | Creates or changes a file | **Yes** |
| `run_terminal_command` | Runs a shell command in your project | **Yes** |

**"Approval-gated" means the agent can never change your project on its own.**
Before any write or command runs, the panel shows an **"Approve this action?"**
card — a diff for a file change or the exact command — and waits. **Approve**
runs it; **Reject** skips it and the agent carries on. **Stop run** ends the
whole run. Reading files is automatic because it changes nothing.

Example task: *"add a --verbose flag to main.py and update the README"*.

Agent mode needs a model that supports **tool use**. Claude models do; some
free OpenRouter models don't (the model list marks these "no tool use").

### Commit messages and code review

*☰ → Git.*

- **Generate with AI** drafts a commit message from your **staged** changes (it
  looks at the diff and your recent commit subjects so the style matches).
- **Review changes** asks the AI to review the staged diff; findings appear with
  a severity and, where possible, are pinned to the line they refer to. Use
  **Dismiss review** to hide them.

Both only *suggest* — nothing is committed for you.

### Test and docstring generation

*Top-bar ⋮ → **Generate tests (AI)** / **Generate docstring (AI)**.*

The AI writes tests (or a docstring) for the open file and proposes it as a
file change. It goes through the same **Approve / Reject** gate as the agent, so
nothing is written until you confirm.

### Ask about your codebase

*☰ → Search → switch from **Find** to **Ask AI** → "Ask about this codebase".*

Ask in plain language (e.g. *"where is the terminal PTY handled?"*). Toroid
Studio scans your project, picks the most relevant chunks of code and gives them
to the AI, then shows the answer plus a **"Jump to"** list of the source
locations. Relevance is decided by **keyword ranking** (not by embeddings), on
your device, with nothing stored between questions — so phrase questions with
words that actually appear in your code.

### Choosing a provider

*Settings → AI → **Provider**: "Anthropic (Claude)" or "OpenRouter".*

Each provider has its own key field and its own saved key. Every AI feature —
chat, inline completions, agent, commit messages, review, tests, docstrings,
codebase questions — works with either; you don't configure them separately.

- **Anthropic:** Toroid Studio uses Claude Sonnet for the deeper tasks (chat,
  agent, tests, codebase questions) and the faster Claude Haiku for the frequent
  small ones (inline completions, commit messages, review, docstrings).
- **OpenRouter:** the **one model you choose** is used for *all* features.

### Free vs paid models (OpenRouter)

*Settings → AI → OpenRouter → **Model**.*

OpenRouter's catalogue changes often, so the list is fetched live rather than
built in.

- The **Active:** line at the top always shows the model in use, with a badge —
  **Free** or **$** (paid). Long-press the badge for a tooltip. The badge stays
  visible in either list view, so it's never unclear whether you're on a paid
  model.
- **Free Models** (default) lists models OpenRouter currently prices at $0 for
  both input and output. Free models are **rate-limited and shared with many
  other users**, so they're sometimes busy — see
  [Troubleshooting](#12-troubleshooting).
- **All Models (incl. paid)** lists everything OpenRouter offers for text, sorted
  by provider, each showing its provider, ID, context length and price:
  **`Prompt $3.00 · Completion $15.00 per 1M tokens`**. A **search box** narrows
  the list — type `claude`, `gpt` or `gemini` (several words must all match).
- Choosing a **paid** model asks you to confirm — *"This model charges per use
  via your OpenRouter account. Costs are billed directly by OpenRouter to your
  account, not through Toroid Studio. Continue?"* — **once per app session**
  (after you confirm, switching to other paid models in the same session doesn't
  ask again; it asks again after the app is restarted). Cancel leaves your model
  unchanged.
- **Custom model ID** field: type any OpenRouter ID (the `vendor/model` form,
  e.g. `anthropic/claude-sonnet-4.6`) and tap **Use this model** — useful for a
  brand-new model or a paid one not in the free list. The same confirmation
  applies to anything that isn't clearly free.
- **Refresh model list** re-fetches now. The list is otherwise cached for
  **24 hours**. If OpenRouter can't be reached you'll see *"Could not refresh
  model list, showing cached options"* (or *"…default options"* if nothing was
  ever cached) and a short built-in list — the picker is never empty.

Some entries in the free list are not general chat models (for example a
safety classifier); their names make this clear.

---

## 4. Code Intelligence

A **language server** runs on your device, so this works offline and your code
isn't sent anywhere for it.

- **Diagnostics.** Errors and warnings are underlined as you type and can be
  hovered for the message. Python uses *pyflakes*.
- **Autocomplete.** A completion list pops up as you type (Python uses *jedi*);
  tap an item to insert it.
- **Go to definition.** Put the caret on a name → **⋮ → Go to Definition**. Use
  **⋮ → Back** to return to where you were.

**Languages:** Python (`.py`, `.pyi`) works out of the box. **JavaScript /
TypeScript** (`.js`, `.jsx`, `.ts`, `.tsx`, …) needs the optional **Node.js
runtime**: turn it on in **Settings → Runtimes → Node.js**. Node is only present
in builds that bundle it, and it uses noticeably more memory while a JS/TS
project is open. Without it, JS/TS files are still highlighted and editable —
just without diagnostics and completion.

Intelligence works on files inside a Toroid Project.

---

## 5. Debugging

Debugging is available for **Python** files in a **Toroid Project**, using
Microsoft's `debugpy` running on the device.

1. **Set a breakpoint:** open a `.py` file and **tap a line number** — a red dot
   appears. Tap again to remove it.
2. **Start:** **⋮ → Run with Debugger**. The program runs until it hits a
   breakpoint.
3. **Control it** with the bar that appears: **Continue**, **Step over**,
   **Step into**, **Step out**, **Stop debugging**. The current line is
   highlighted.
4. **Inspect:** open **☰ → Debug** to see **Variables** and the **Call Stack**
   for the paused program.

If the Debug panel says *"The debugger isn't bundled for this build"*, your
build was made without the debugger; see [Troubleshooting](#12-troubleshooting).

---

## 6. Terminal & Runtimes

### The terminal

Tap the **terminal icon** in the top bar to open a shell at the bottom of the
screen. It runs real
programs inside the app's private sandbox, starting in your project's folder.

- Tap **+** (*New terminal*) to open another shell; each one is a tab along the
  top. Close one with its **×**, and hide the whole panel with the **⌄** arrow
  (*Hide terminal*). **clear** wipes the screen.
- It is a **line-based terminal with colour support**, not a full terminal
  emulator — programs that redraw the whole screen (`vim`, `htop`, `less`)
  won't display correctly, and there is no SSH.

### Python and Node.js

- **Python 3.12** is real and bundled: `python3 script.py`, `python3 -c "…"`, and
  the standard library including `ssl`/HTTPS, `sqlite3` and `hashlib`.
- **Node.js** (v18) is real but **optional and off by default**, and only in
  builds that include it: `node app.js`. Enable it in **Settings → Runtimes**.

### Running a file

The **▶ Run** button (top bar) saves the file and runs it in the terminal:
`python3` for `.py`, `node` for `.js`/`.mjs`/`.cjs`, `sh` for `.sh`. Files of
other types show *"Don't know how to run …"*. Run works on project files.

### Python packages (pip)

*☰ → Packages.* Type a package name (it's looked up on PyPI as you type) and tap
**Install**, or tap **Install requirements.txt** to install everything listed.
The panel lists what's installed for the current project.

Only **pure-Python** packages work (compiled/native ones can't run in this
environment), and installs need an internet connection.

---

## 7. Git & Source Control

*☰ → Git.* Git works on **Toroid Projects** (not on a plain opened folder).

### Clone, or start a repository

- **Clone repository** — enter an HTTPS URL (e.g.
  `https://github.com/owner/repo.git`), an optional project name and, for private
  repos, your GitHub username and a personal access token. It becomes a new
  project.
- In a project that isn't a Git repo yet, tap **Initialize repository**. You can
  also **Add remote** / **Set remote URL** for `origin`.

### Stage and commit

Changes are split into **Staged Changes** and **Changes**. Use **Stage** /
**Stage all** and **Unstage** / **Unstage all**; **Discard** throws a change
away. Tap a file to see its **diff**. Write a message (or use **Generate with
AI**) and tap **Commit**, or **Commit & Push**.

### Push and pull

The **Pull** and **Push** icons at the top of the panel talk to `origin`. They
need a **GitHub personal access token**: tap **Add GitHub token for push** or go
to **Settings → Git & GitHub**, enter the host (default `github.com`), your
username (optional) and the token. It's stored encrypted and is only sent to
that host. You can also set your commit **name and email** there.

### Branches and merging

Tap the branch name to open the **branch sheet**: switch branches, **create** a
new one, **merge** another branch into the current one, or **delete** a branch.
Deleting a branch that isn't fully merged is blocked with a warning — you'd lose
its commits — and needs an explicit **Force delete**.

### Merge conflicts

If a merge conflicts, the **conflict resolver** opens. For each conflicted file
you can **Use ours**, **Use theirs** or **Use both** (or **Resolve as deleted**
if one side deleted the file), or edit the result by hand, then **Resolve**. When all are resolved you'll see *"All conflicts resolved
— commit to finish the merge"* and a normal commit completes it. **Abort** backs
out of the merge entirely.

### Stash and history

**Stash** shelves your uncommitted work so you can switch tasks; an optional
message helps you find it later; **Apply** brings it back. **History** lists past
commits, labelled with the branch they belong to.

---

## 8. Cloud Sync & Deploy

### Cloud Sync (Pro)

Syncs a project's files to a folder called **"Toroid Projects"** in **your own
Google Drive** — never to a Toroid Studio server. It uses Google's narrow
`drive.file` permission, which only lets the app see files it created itself.

- **It is a Pro feature, and Pro can't be purchased yet**, so for now the
  Cloud Sync dialog will tell you it's unavailable. This section describes how
  it works once Pro is available.
- **Turn it on per project:** ☰ → **Projects** → tap the **☁** icon on a project
  → sign in with Google → **Enable & sync now**. The dialog first explains
  exactly what will be uploaded (everything except `.git`, `node_modules` and
  build/cache folders).
- **Sync now** re-syncs; **Disable sync** stops future uploads (files already in
  Drive stay there); **Sign out** removes the Google sign-in.
- **Conflicts:** if the same file changed in two places, nothing is overwritten —
  *both versions are kept* and you can open either one from the dialog.
- If you see *"Sign-in expired — sign in again to keep syncing"*, just sign in
  again.

### Deploy to Netlify

Publish a simple static website to **your own Netlify account**.

1. Get a Netlify **personal access token** at
   `app.netlify.com/user/applications` and save it in **Settings → Deploy**
   (encrypted on the device).
2. Open **☰ → Projects** and tap the **cloud-upload icon** on the project.
3. Tap **Deploy**. When it finishes you'll see **"Live at …"** with the URL;
   **Redeploy** publishes again.

Deploy only appears for projects that look like a **plain static site**: an
`index.html` at the top level and **no build tooling** (no `package.json`,
`composer.json` and similar). Files are uploaded as-is; there's no build step.
No Toroid Studio server is involved.

---

## 9. Productivity

### Command palette

Tap **⚡** in the top bar and type. It can open any panel, run/format/save the
file, go to definition, toggle the terminal or split view, open Settings, create
files and folders, switch between open tabs and projects, and insert snippets.
Commands that don't apply right now are greyed out.

### Snippets

*☰ → Snippets.* Tap **New snippet**, give it a **Name**, an optional **Trigger** (no
spaces) and **Language**, and type or paste the **Body** (the code). Tap a snippet to insert it at
the caret. Snippets also appear in the palette as **"Insert snippet: …"**.

### Search and replace

*☰ → Search.* Type in **Find** to search the whole project; tap a result to jump
to it. Fill **Replace with** and tap **Replace All** to change every match — you
get a **"Replace All?"** confirmation first. (The panel's **Find / Ask AI** switch
changes it into the [codebase question](#ask-about-your-codebase) feature.)

### Formatter

**⋮ → Format Document** (or **⚡ → Format Document**) formats the open file with
**Black** for Python, or **Prettier** for JavaScript/TypeScript (Prettier needs
the Node runtime). Turn on **Settings → Editor → Format on save** to do it on
every save. Files with no bundled formatter are silently skipped.

### Project templates

**☰ → Projects → New** offers **Empty**, **Python script**, **Node.js script**
and **Static web page**; the script templates come ready to Run.

### Home-screen widget

Long-press your home screen, choose Widgets, and add the Toroid Studio widget —
it lists your recent projects, and tapping one opens it.

### Productivity dashboard

*Settings → Productivity* shows your **commits**, **files edited** and **coding
time**. It's computed on the device and never sent anywhere.

---

## 10. Settings & Privacy

| Setting | What it does |
|---|---|
| **Help & Features** | Opens the in-app help screen |
| **Appearance → Theme** | Toroid Dark / Midnight / Light |
| **Editor → Font size, Tab width** | Editor text size (8–32 sp) and tab width (2–8) |
| **Wrap long lines** | Wrap instead of scrolling horizontally |
| **Show line numbers** | Show the gutter (needed to tap-set breakpoints) |
| **Insert spaces for Tab** | Tab key inserts spaces |
| **Format on save** | Auto-format supported files whenever you save |
| **Productivity** | Local stats: commits, files edited, coding time |
| **Runtimes** | Shows Python/Node status; **Node.js** toggle (if bundled); **Re-check** |
| **Subscription** | Free (BYOK) today; Pro is not available yet |
| **Cloud Sync** | Google sign-in state for sync (Pro) |
| **Privacy → Send crash reports** | Opt-out switch for crash reports |
| **Privacy → Send anonymous usage analytics** | Opt-out switch for usage analytics |
| **Show the welcome screen again** | Replays the first-run screen |
| **AI → Provider / key / model** | See [AI Features](#3-ai-features) |
| **AI → Inline AI completions** | Ghost-text suggestions on/off |
| **Git & GitHub** | Commit name/email; GitHub tokens |
| **Deploy** | Netlify access token |
| **Feedback → Send Feedback** | Report a bug, request a feature, or give feedback |
| **About** | Version, open-source licenses, Privacy Policy, **Support Toroid Studio** (optional donations), Contact Support |

About the two **Privacy** switches: they're independent, on by default, and
never include file contents, API keys or tokens. When on, crash reports
(**Firebase Crashlytics**) and anonymous usage analytics (**Firebase
Analytics**) may be collected and sent to Google's Firebase; turn a switch off
and that collection stops.

**Send Feedback** lets you pick a category, describe the issue, optionally
attach a screenshot (taken when you tap the button, before the form opens) and
shows exactly what will be sent: your text, the category, an anonymous install
ID and coarse device/app info (app version, Android version, device model,
which runtimes are on, theme). It never includes file contents, API keys or
tokens. Submissions are stored in Firebase (Google Firestore); you can still
also reach us by email at **Settings → About → Contact Support**.

### Support Toroid Studio (optional donations)

The **Support Toroid Studio** page is one tap away: use the ❤ card at the top of
**Settings**, the **⋮ menu** in the editor, or the command palette (search
"Support"). It's also linked under **Settings → About**. It is entirely
voluntary:

- **Three one-time tiers** — Small Coffee (suggested $1.99), Pizza Slice
  ($4.99) and Rocket Fuel ($9.99) — are paid through **Google Play**. You can
  donate more than once. Toroid Studio never sees your payment details.
- After a successful donation you get a thank-you message. **Nothing else
  changes**: donations don't unlock any feature and are **not** a Pro
  subscription — every feature works the same for everyone.

*In the current build the Play donation products aren't published yet, so
tapping a tier tells you in-app donations aren't available yet. They switch
on once the maintainer sets them up.*

The full legal text is in the **Privacy Policy** (Settings → About).

---

## 11. FAQ

**Is my code private?**
Your code stays on your device unless *you* use a feature that needs a service:

- **AI features** send the relevant text **directly from your phone to the AI
  provider you selected** (Anthropic or OpenRouter) using your own key — **never
  through a Toroid Studio server**. What's sent depends on the feature: the open
  file and selection for chat; the text around your cursor for inline
  completions; the staged changes for commit messages and review; the files the
  agent reads and command output for agent mode; the most relevant code chunks
  for codebase questions.
- **OpenRouter** forwards your request to whichever company hosts the model you
  picked, and *that* company's data handling applies too. Free community-hosted
  models may log prompts, so avoid sending sensitive code to them.
- **Git** talks to the remote you configured (e.g. GitHub). **pip** talks to
  PyPI. **Cloud Sync** uploads to *your* Google Drive. **Deploy** uploads to
  *your* Netlify account.
- Your **API keys and tokens** are encrypted with the Android Keystore and never
  logged.
- Toroid Studio has no accounts and no servers that receive your code. The
  Privacy Policy has the details.

**What does "approval-gated" mean?**
Anything that would *change* your project — writing a file, running a command,
or applying AI-generated tests/docstrings — is shown to you first as a diff or
command, and only happens after you tap **Approve**. **Reject** skips it. The
agent can read your files without asking (that changes nothing), but it cannot
write or run anything without your say-so.

**How much does AI cost?**
Toroid Studio itself is free; you pay your AI provider for usage. Cost depends on
the model and how much text is sent and received. Prices are per **million
tokens** (a token is roughly ¾ of a word), quoted separately for text you send
("prompt") and text you get back ("completion"). Example arithmetic: on a model
priced at $3 / $15 per 1M tokens, a request with a 2,000-token prompt and a
500-token reply costs 2,000 × $3 ÷ 1M + 500 × $15 ÷ 1M ≈ **$0.0135**. To keep
costs down: use a cheaper model, turn off **Inline AI completions**, start a new
chat when you change topic (long chats resend their history), and prefer
selections over whole files. **OpenRouter's free models cost $0** but are
rate-limited. Check your provider's dashboard for real usage; Toroid Studio
doesn't track spend.

**Can I use it offline?**
Mostly yes. **Offline:** editing, syntax highlighting, code intelligence
(diagnostics, autocomplete, go-to-definition), the terminal with Python/Node,
the debugger, search and replace, snippets, formatting, and local Git (stage,
commit, branch, merge, stash, history). **Needs internet:** all AI features,
cloning/pushing/pulling, `pip install`, Cloud Sync, Deploy, and refreshing
OpenRouter's model list (the last list is cached for 24 hours).

**Which AI provider should I choose?**
Anthropic gives you Claude directly with a single account. OpenRouter gives you
one key for many models and has free options, which is handy for trying things
or keeping costs at zero — but free models are often busy, and some don't
support the tool use that agent mode needs.

**Why is Cloud Sync not working?**
It's a Pro feature and Pro isn't purchasable yet. See
[Sync issues](#sync-issues).

**Does it work on tablets and Chromebooks?**
It runs on Android 8.0+ generally. Native components (Python) are built for
64-bit ARM and, optionally, x86-64 (emulators/ChromeOS).

**Why can't I run/commit/debug in my opened folder?**
Those need a real project folder. Use **☰ → Projects → Import folder** to copy it
into a Toroid Project. See [Your first project](#your-first-project).

**Where do I report a bug or suggest a feature?**
**Settings → Feedback → Send Feedback**, or **Settings → About → Contact
Support**.

---

## 12. Troubleshooting

### AI not responding

Start with the message shown in red in the chat — it tells you which case you're
in.

| Message | What it means | What to do |
|---|---|---|
| *No API key set. Add one in Settings → AI.* | No key saved for the **selected provider** | Settings → AI → check the provider chip at the top, paste that provider's key, **Save key** |
| *The API key was rejected. Check it in Settings → AI.* | The provider refused the key (typo, revoked, or wrong provider) | Re-create the key, paste it under the right provider |
| *Rate limit reached for this free model. Try again in a moment, or switch models/providers in Settings.* | OpenRouter's free model is at its limit or the shared pool is busy | Wait a minute, pick a **different free model**, use a paid model, or switch to Anthropic |
| *Upstream error from …: Service temporarily overloaded* | The company hosting that model is overloaded | Retry shortly or choose another model |
| *Unable to resolve host …* / *Network error* | No internet or DNS problem | Check Wi-Fi/mobile data and try again |
| *OpenRouter reports insufficient credits…* | A paid model and your OpenRouter balance is empty | Add credits at openrouter.ai, or pick a free model |
| *OpenRouter has no available endpoint for model "…"* | The model ID doesn't exist (typo or retired) | Pick from the list, or **Refresh model list** |

Other things to check:

- **Right provider selected?** Each provider has its own key. Settings → AI
  shows which is active.
- **Chat box disabled / says to add a key?** No key for the selected provider.
- **Agent mode fails or does nothing** on OpenRouter: the chosen model may not
  support tool use — pick one **not** marked "no tool use", or use Anthropic.
- **Inline completions never appear:** they need a key, a network connection and
  **Settings → AI → Inline AI completions** on; they're rate-limited and fail
  silently by design.
- **Free models keep failing:** free capacity is shared and fluctuates. Try
  another model from the list, try later, or switch provider.
- **Model list is stale or shows the short default list:** tap **Refresh model
  list** with a working connection.

### Sync issues

- **"Cloud Sync is a Pro feature" / can't enable:** Pro isn't available to buy
  yet, so sync can't be enabled for now.
- **Sign-in fails or shows an error:** Google sign-in must be set up for the
  build you installed; a build without it can't sign in (a "developer error"
  is the usual sign). Builds distributed to the public will have this configured.
  Also make sure the phone has a Google account and a network connection.
- **"Sign-in expired — sign in again to keep syncing":** open the ☁ dialog and
  sign in again.
- **"Both versions were kept":** a conflict — the same file changed on two
  devices. Open both copies from the dialog and keep the one you want.
- **Files missing in Drive:** `.git`, `node_modules` and build/cache folders are
  deliberately not synced. Only the **"Toroid Projects"** folder is used.

### Git problems

- **"Source control works on Toroid Projects":** you opened a plain folder.
  Import it (**☰ → Projects → Import folder**) or clone into a new project.
- **Push/pull is rejected or asks for auth:** save a personal access token under
  **Settings → Git & GitHub** for the right host (and tick the `repo` scope for
  private repositories).
- **"no remote":** add one with **Add remote** in the Git panel.
- **Merge stopped on conflicts:** resolve each file in the conflict screen, then
  commit — or **Abort**.

### Terminal, run and packages

- **`python3: not found` / runtime missing:** Settings → Runtimes shows whether
  Python is available; tap **Re-check**. Builds made without the runtime files
  don't include it.
- **`node` not available:** Node.js is optional and only in builds that bundle
  it; turn it on in **Settings → Runtimes**.
- **`pip install` fails:** only **pure-Python** packages work; anything with
  compiled extensions can't be installed. Also check your connection.
- **A program looks garbled** (`vim`, `htop`, `less`): the terminal isn't a full
  terminal emulator; use non-interactive commands.
- **▶ says "Don't know how to run":** Run supports `.py`, `.js`, `.mjs`, `.cjs`
  and `.sh`.

### Other common problems

- **Debug panel says the debugger isn't bundled:** your build was made without
  it. Use a build that includes the debugger (see the repository's
  `scripts/fetch-runtimes.sh`).
- **No syntax colours:** that language's grammar isn't in your build; the file
  still edits fine as plain text.
- **No JS/TS diagnostics:** enable **Node.js** in Settings → Runtimes (if your
  build has it).
- **Format Document does nothing:** the file type has no bundled formatter
  (Black = Python, Prettier = JS/TS with Node).
- **Deploy icon missing:** the project isn't a plain static site (needs a
  top-level `index.html` and no `package.json` or similar).
- **Something crashed or looks wrong:** please tell us — **Settings → Feedback →
  Send Feedback** or **Settings → About → Contact Support**, with the steps to
  reproduce.

---

## 13. Known limitations

- **Multi-cursor editing** isn't available (editor component limitation).
- The terminal is **line-based**, not a full terminal emulator (no `vim`/`htop`,
  no SSH).
- Python packages must be **pure-Python**.
- **Debugging** is Python-only.
- **JavaScript/TypeScript** intelligence needs the optional Node runtime, which
  only some builds include.
- **Cloud Sync** requires Pro, which isn't available yet.
- **Codebase questions** use keyword ranking, not embeddings.
- AI quality, speed and availability depend on the provider and model you choose,
  and free models can be busy.
