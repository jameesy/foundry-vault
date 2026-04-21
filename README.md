![Foundry](docs/header.png)

# Foundry

A personal knowledge vault maintained by Claude. You collect sources. Claude compiles them into a wiki of concepts, connections, and open questions.

Based on [Andrej Karpathy's LLM wiki pattern](https://x.com/karpathy/status/2039805659525644595): raw source documents go in, an LLM incrementally compiles them into concept articles with backlinks, and the wiki becomes a rich substrate for Q&A and further research.

## Quick start

1. **Clone this repo** and open it in [Obsidian](https://obsidian.md)
2. **Install Claude Code** — [claude.ai/code](https://claude.ai/code) (or your preferred agent!)
3. **Drop something into `inbox/`** — a URL, a web clipping (via [Obsidian Web Clipper](https://obsidian.md/clipper)), a PDF, or pasted text
4. **Run `/foundry-ingest`** — Claude processes everything in the inbox into clean source notes
5. **Run `/foundry-compile`** — Claude scans for un-compiled sources and builds concept articles when themes recur across 2+ sources
6. **Run `/foundry-ask`** followed by a question — Claude researches your question across the vault and writes a report

That's it. Drop, ingest, compile. The vault grows itself.

## How it works

### Three layers

| Directory | Purpose | Who writes |
|---|---|---|
| `inbox/` | Staging for unprocessed drops | You |
| `sources/` | One atomic note per article, paper, or transcript | Claude |
| `wiki/` | Concept articles, people pages, query reports, index, and log | Claude |

### The contract

You curate what goes in. Claude writes and maintains the derived layer. The separation matters — your taste decides what's worth keeping; Claude does the synthesis work that humans can't sustain at scale.

### The 2-source rule

Claude won't create a concept article from a single source. Themes are logged as **candidates** in `wiki/_meta/index.md` until a second independent source confirms the pattern. This prevents the wiki from filling up with speculative one-offs.

### What compounds

- **Sources** build the raw material
- **Concepts** crystallise when themes recur
- **Queries** (`/foundry-ask`) produce research reports that get filed back into the wiki — so questions add up over time
- **Research threads** emerge as clusters of 3+ concepts sharing keywords

## The four commands

| Command | What it does |
|---|---|
| `/foundry-ingest` | Process inbox into source notes |
| `/foundry-compile` | Build or extend concept articles from un-compiled sources |
| `/foundry-ask` | Research a question across the vault |
| `/foundry-lint` | Health-check: stats, orphans, keyword drift |

## Companion vault (optional)

If you already keep personal notes (a commonplace, Zettelkasten, or notes folder), you can point Claude at it as a read-only companion. Claude will cross-reference your notes when compiling but never write into them. See `CLAUDE.md` for setup.

## Customisation

- **Areas**: Edit the `#area/` taxonomy in `CLAUDE.md` to match your interests
- **Keywords**: Managed in `wiki/_meta/index.md` — add new ones as your reading grows
- **Obsidian theme**: The `.obsidian/` config is included with a clean setup. Swap themes or plugins as you like
- **Voice**: Concept articles are written as sharp foundations for *your* writing, not finished essays. Adjust the voice instructions in `CLAUDE.md` if you want a different tone

## What's included

This template ships with two example sources and one example concept to show the structure:

- `sources/LLM Knowledge Bases (Karpathy).md` — the post that inspired this vault pattern
- `sources/What Matters in the Age of AI Is Taste.md` — on taste as the human differentiator in AI-augmented work
- `wiki/Two-layer knowledge systems.md` — a concept article compiled from both sources
- `wiki/Andrej Karpathy.md` — an example people page

Delete these and clear `wiki/_meta/index.md` once you've seen how they work, or keep them as seeds for your own vault.

## Schema

Everything Claude needs to know is in `CLAUDE.md`. That file is the single source of truth for how the vault operates. Read it if you want to understand or modify the rules.

---

Built with [Claude Code](https://claude.ai/code) and [Obsidian](https://obsidian.md).
