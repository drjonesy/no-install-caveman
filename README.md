![No Install Caveman Socail Card](github-social-no-install-caveman.png)

# 🗿 No Install Caveman Mode

A lightweight, plugin-free approach to reducing Claude Code output tokens by ~75% using simple markdown skill files.

> Adapted from: https://github.com/JuliusBrussee/caveman. I didn't want to install anything and so I did the obvious thought... asked claude to remake the repo in simple skills. :) Not as cool as original.

## What's Included

```
_claude/
├── README.md              ← You are here
└── skills/
    ├── caveman-mode.md    ← Terse output (lite/full/ultra intensity)
    ├── terse-commits.md   ← Compressed commit messages (Conventional Commits)
    ├── terse-reviews.md   ← One-line code review comments
    └── compress-docs.md   ← Compress prose in .md/.txt files
```

## Setting Up a New Project

### 1. Copy the `_claude` folder

Copy the entire `_claude` folder into the root of your existing project:

```bash
cp -r _claude /path/to/your-project/
```

### 2. Create a `CLAUDE.md` in your project root

Create a `CLAUDE.md` file at the root of your project with the following content:

```markdown
# Project Skills

Read and apply the following skill files before processing any request:

- [\_claude/skills/caveman-mode.md](_claude/skills/caveman-mode.md) — Terse output mode. Activated with `/caveman` or "caveman mode". Cuts ~75% of output tokens.
- [\_claude/skills/terse-commits.md](_claude/skills/terse-commits.md) — Ultra-compressed commit messages. Conventional Commits format, 50 char subjects.
- [\_claude/skills/terse-reviews.md](_claude/skills/terse-reviews.md) — One-line code review comments. Location + severity + problem + fix.
- [\_claude/skills/compress-docs.md](_claude/skills/compress-docs.md) — Compress .md/.txt files into terse format. Backs up originals.

Caveman mode is **off by default**. Activate it by saying "caveman mode" or `/caveman`. Other skills activate when relevant (commits, reviews, doc compression).
```

### 3. (Optional) Add `_claude` to `.gitignore`

If you want to keep the skill files local and out of version control:

```bash
echo "_claude/" >> .gitignore
```

## Usage

Caveman mode is **off by default**. Use these commands in your Claude Code prompt:

| Command | Effect |
|---------|--------|
| `caveman mode` | Activate terse output (default: full intensity) |
| `/caveman lite` | Activate lite — no filler, keeps grammar |
| `/caveman full` | Activate full — drops articles, fragments OK |
| `/caveman ultra` | Activate ultra — max compression, abbreviations |
| `stop caveman` | Return to normal output |
| `normal mode` | Return to normal output |

## How It Works

Claude Code automatically reads `CLAUDE.md` at the start of every session. The `CLAUDE.md` references the skill files in `_claude/skills/`, which provide the rules Claude follows for terse output, commit messages, code reviews, and doc compression.

No plugins, hooks, or external dependencies required. Works in both the terminal and IDE extensions (VS Code, JetBrains).

## Customization

- Edit `_claude/skills/caveman-mode.md` to change default intensity or add custom rules
- Remove any skill file and its reference in `CLAUDE.md` if you don't need it
- Add your own skill files to `_claude/skills/` and reference them in `CLAUDE.md`
