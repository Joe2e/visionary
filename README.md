# Visionary

You say what you want, loosely. It asks until it can describe, in full, what having it looks like for you, detailed enough to build from. It works out the how itself and learns how you think. It never builds.

One file: [`skills/visionary/SKILL.md`](skills/visionary/SKILL.md). It works on any host with an instructions field; see [which models follow it](#which-models-follow-it).

## Install

It keeps three plain markdown files in `~/Visionary` (on Drive, a folder named `Visionary`): `profile.md`, `ledger.md`, and one `brief-g<k>.md` per goal. You may read them. Never edit them; say the correction in chat instead.

**Claude Code**

```
/plugin marketplace add Joe2e/visionary
/plugin install visionary@visionary
```

Then let it reach the folder: add `"permissions": { "additionalDirectories": ["~/Visionary"] }` to `~/.claude/settings.json`, or approve the first write.

**Every other host**: copy the text of `SKILL.md` to where your host reads instructions (table below), and let the host reach the folder. A plain instructions box takes everything below the `---` frontmatter (under 8,000 characters). To keep the files somewhere else, change the path in its first line.

| Host | Where `SKILL.md` goes | Letting it reach the folder |
|---|---|---|
| Claude Code (CLI, VS Code, desktop) | the plugin above, or `~/.claude/skills/visionary/SKILL.md` | `permissions.additionalDirectories: ["~/Visionary"]` in `~/.claude/settings.json` |
| Cursor | Settings > Rules > User Rules (paste the body) | Settings > Agent > Security: External File Protection off, or approve the first write |
| Codex CLI / extension | `~/.codex/AGENTS.md` (paste the body) | `[sandbox_workspace_write] writable_roots = ["/Users/you/Visionary"]` in `~/.codex/config.toml` |
| GitHub Copilot (VS Code) | `~/.copilot/instructions/visionary.instructions.md` with `applyTo: "**"` frontmatter | approve the terminal write once |
| Devin / Windsurf | `~/.devin/global_rules.md` | `"Read(~/Visionary/**)"`, `"Write(~/Visionary/**)"` in `~/.config/devin/config.json` |
| Antigravity CLI | `~/.gemini/GEMINI.md` | accept the write diff, or relax the policy in `~/.gemini/antigravity-cli/settings.json` |
| Claude.ai (all plans) | a Project's instructions | connect Google Drive (Settings > Connectors); the folder is a Drive folder |
| ChatGPT web (paid plans) | a Project's instructions | connect the Google Drive app with Docs write; the files are Google Docs of the same names |
| ChatGPT desktop (Codex / Work) | `~/.codex/AGENTS.md` | open the folder as the project |
| Gemini, free | a Gem's instructions, with the Drive files added as knowledge | reads only; nothing is written, so nothing is learned between sessions |
| Gemini AI Pro / Ultra | a Spark skill, plus the Gem above for chat | the Workspace app edits the Docs in place |
| Any API | the system prompt | give the model a read and a write tool on the folder |

Verified against host documentation on 2026-09-19. Not confirmed: whether ChatGPT and Gemini Drive tools read plain markdown or need a native Google Doc, Drive writes on ChatGPT's free plan, and whether a Claude.ai connector is on by default in every new chat.

## Which models follow it

Tested in simulated sessions (rounds 5-11, 2026-09-25/26): Opus-class models follow the whole text. Sonnet 5 keeps the structure (three files, sections, closing) but misses details: register, source words, some how questions, profile marks, and sometimes a rejection. Haiku does not follow it. Known lapses even on Opus: replies a few words over the cap, a brief now and then tagging the model's inference as said, and who would disagree dropped when a route shifts slightly.

## Where a host cannot write

The conversation is the memory for that session. Nothing is written, nothing is learned, and nothing is asked of you.
