<p align="center">
  <img src="https://github.com/TheRealSeanDonahoe/agents-md/releases/download/v0.1.0/hero.png" alt="Sean Donahoe's AGENTS.md — Smarter Operating Instructions for Coding Agents" width="100%">
</p>

**One file. Every coding agent starts behaving like a senior engineer.**

Drop it into any repo. Claude Code, Codex, Cursor, Gemini CLI, Aider, Windsurf, Copilot, and Devin all read it on their own. No plugins. No config. No setup rituals.

It just works.

---

## Install

### The easy way — hand it to your agent

Open Claude Code, Codex, Cursor, or any coding agent in your project root. Paste this:

> Install https://github.com/TheRealSeanDonahoe/agents-md into this project.
>
> 1. Fetch `https://raw.githubusercontent.com/TheRealSeanDonahoe/agents-md/main/AGENTS.md` and save it as `./AGENTS.md` at the project root. If `AGENTS.md` already exists, stop and show me the diff before overwriting.
> 2. Symlink `CLAUDE.md` and `GEMINI.md` to `AGENTS.md` so Claude Code and Gemini CLI read the same file. Use the right command for my OS (`ln -s` on macOS/Linux, `New-Item -ItemType SymbolicLink` on Windows). If symlinks fail, fall back to copying the file. If `CLAUDE.md` or `GEMINI.md` already exist with content, do not overwrite — prepend `@AGENTS.md` as the first line and leave the rest intact.
> 3. Open the new `AGENTS.md`, find section 10 (Project context), and fill in only what you can verify by reading this codebase: stack, build/test/lint commands from `package.json`, `pyproject.toml`, `Cargo.toml`, or `Makefile`, and source/test directory layout. Leave anything you can't confirm as `TODO`.
> 4. Do not touch section 11 — it stays empty by design.
> 5. When done, tell me to restart this session so the file loads.

Restart the session. You're done.

### The manual way

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/TheRealSeanDonahoe/agents-md/main/AGENTS.md
```

Codex, Cursor, Aider, Windsurf, Copilot, Devin, Amp, opencode, and RooCode read `AGENTS.md` on their own. Nothing else to do.

Claude Code and Gemini CLI look for their own filenames, so symlink:

**macOS / Linux**
```bash
ln -s AGENTS.md CLAUDE.md
ln -s AGENTS.md GEMINI.md
```

**Windows** (PowerShell, run as admin or with Developer Mode on)
```powershell
New-Item -ItemType SymbolicLink -Path CLAUDE.md -Target AGENTS.md
New-Item -ItemType SymbolicLink -Path GEMINI.md -Target AGENTS.md
```

If symlinks aren't available, copy the file instead — you'll just need to re-copy when you update `AGENTS.md`:
```powershell
Copy-Item AGENTS.md CLAUDE.md; Copy-Item AGENTS.md GEMINI.md
```

Open a session. You're done.

---

## What changes immediately

| Before | After |
| --- | --- |
| *"You're absolutely right!"* → reverts working code | Agent pushes back when you're wrong |
| 200 lines when 50 would do | Simplest diff that solves the problem |
| Reformats your whole file while fixing a typo | Every changed line traces to your request |
| Claims "done" on code that doesn't run | Writes verification first, runs it, then reports |
| Silently guesses between two interpretations | Surfaces the ambiguity, asks once |
| Ignores half your rules because the file is too long | Tight by design. ~200 lines. Rules stay loaded. |

---

## Two sections you edit. Everything else you leave alone.

**Section 10 — Project context.** Stack, commands, layout, forbidden areas. Fill the `TODO`s once. Five minutes.

**Section 11 — Project Learnings.** Starts empty. Every time the agent gets something wrong, one line gets added. The agent itself adds the line when you correct it — you don't babysit the file.

This is the section that compounds. Boris Cherny, the creator of Claude Code, runs his team's version at around 100 learnings accumulated over months. His file is a trained reflex, not a manifesto.

Sections 0–9 are the behavioral scaffold. Don't touch them unless you have a specific reason.

---

## When your AGENTS.md outgrows one file

Rare. But it happens on large codebases. Read the docs before you shard — most people don't need to:

- **Claude Code:** use `@path/to/file.md` imports inside `CLAUDE.md`, or drop topic-scoped rules into `.claude/rules/*.md` with `paths:` frontmatter so they only load when Claude touches matching files. Claude Code also writes its own memory automatically — don't reinvent it.
- **Cursor:** use `.cursor/rules/*.mdc` with path scoping for the same reason.
- **Everyone else:** one `AGENTS.md` is still the right answer.

The goal is fewer tokens loaded per session, not more files for their own sake.

---

## Why `AGENTS.md` and not `CLAUDE.md`

`AGENTS.md` is the [open cross-tool standard](https://agents.md) stewarded by the Linux Foundation's Agentic AI Foundation. Codex, Cursor, Windsurf, Copilot, Aider, Devin, Amp, opencode, and RooCode read it natively. Claude Code reads `CLAUDE.md`. Gemini CLI reads `GEMINI.md`. Symlink all three and every agent reads the same file.

One source of truth. Stop maintaining three.

---

## What it's built on

- Sean Donahoe's **IJFW** principles — *it just f\*cking works*: one install, zero ceremony, working code
- Andrej Karpathy's [four principles](https://github.com/forrestchang/andrej-karpathy-skills) on LLM coding failure modes
- Boris Cherny's public Claude Code workflow — reactive pruning, keep it tight
- [Anthropic's official Claude Code best practices](https://code.claude.com/docs/en/best-practices)
- The [AGENTS.md](https://agents.md) open standard

---

## License

MIT. Fork it, rewrite it, ship it with your own name on it. That's the point.

---

If it saved you an hour, a ⭐ on the repo is how you say thanks.
