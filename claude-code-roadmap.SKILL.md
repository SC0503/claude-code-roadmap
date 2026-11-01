---
name: claude-code-roadmap
description: "Complete Claude Code from-zero roadmap with security analysis, costs, 8 steps, first moves, and official resource links. Use when the user asks for Claude Code setup path, roadmap, learning order, CLAUDE.md, skills, MCP, subagents, hooks, or scheduled tasks."
type: knowledge
lifecycle: active
---

# Claude Code Roadmap From Zero

Structured extraction of the official-resource roadmap (The Tech Plate Guides / Notion). Verified 2026-11-01. All links official; no phishing or malicious payloads.

## Security Analysis & Warnings

Document is safe. Domains limited to academy.claude.com, code.claude.com, developers.notion.com, github.com/anthropics/skills, claude.ai, mcp.notion.com.

**Caution (standard Claude Code surfaces):**
- Hooks (Step 7): Execute shell from `~/.claude/settings.json`. Official starter is desktop notification. Review before adding any hook.
- MCP (Step 6): `claude mcp add --transport http notion https://mcp.notion.com/mcp` is official Notion command. Grants workspace access after OAuth. Scope carefully (`--scope user` / `--scope project`).
- Plugins (Step 5): `/plugin marketplace add anthropics/skills` then `/plugin install example-skills@anthropic-agent-skills` targets official Anthropic repo. Plugins may include hooks/MCP.
- No destructive commands present.

## Prerequisites and Cost

| Item | Detail |
|------|--------|
| Claude Code access | Paid plan required. Pro $20/mo or $17/mo ($200/year). Free plan excludes it. |
| Courses & docs | All free. Cost is only the Claude subscription. |
| Cloud scheduled tasks | Need GitHub repo; Anthropic servers; max 1/hour; paid plan. |
| Desktop scheduled tasks | No GitHub; runs only while app open + computer awake; one catch-up on wake. |
| OS | macOS 13+ or Windows 10 1809+ for terminal. Desktop: Mac/Windows (Linux beta). |

## Steps 1–8

| # | Step | Start with | Length | First move / Command |
|---|------|------------|--------|----------------------|
| 1 | Set it up | Claude Code 101 | 12 lessons, 1.5 hr | Open course → lesson “Installing Claude Code”. Desktop alternative: download app → Code tab → Open folder. Terminal: Cmd+Space → Terminal → follow guide step 2. |
| 2 | Plan mode | Lesson 5 of Claude Code 101 | 8 min | Shift+Tab until plan mode. Ask “how the project works”. Ctrl+G to edit plan. `/plan` for single prompt. |
| 3 | CLAUDE.md | CLAUDE.md file lesson (101 #8) | 10 min | `/init` → read output. Keep <200 lines. Project file shared; home file global. |
| 4 | Context | Context management lesson | 7 min | On task switch: `/clear`. `/compact` to summarize. `/context` shows usage (incl. CLAUDE.md). CLAUDE.md survives compaction. |
| 5 | Skills | Introduction to agent skills | 6 lessons, 1 hr | First two lessons → turn repeated prompt into skill. Example: copy `/summarize-changes`. Place in `~/.claude/skills` (global) or project `.claude/skills`. |
| 6 | MCP | Notion MCP setup | One command | `claude mcp add --transport http notion https://mcp.notion.com/mcp` then `/mcp` + browser sign-in. Test: summarize one page. |
| 7 | Subagents + hooks | Introduction to subagents | 4 lessons, 45 min | Lesson 2 → create first subagent. Hooks: copy Notification hook into `~/.claude/settings.json`. Built-ins: Explore (read-only), Plan. |
| 8 | Running without you | Claude Code in action | 9 lessons, 1 hr | Automate repeat work module → “Routines and headless”. Cloud: `/schedule daily PR review at 9am` or claude.ai/code/routines. Desktop: Code tab → Scheduled → New task → Only on this computer. |

## Resource Links (Purpose)

- **Claude Code 101**: https://academy.claude.com/courses/claude-code-101 — Core free course (install, plan, CLAUDE.md, context, skills, MCP, subagents, hooks).
- **Desktop quickstart**: https://code.claude.com/docs/en/desktop-quickstart — Install desktop app, Code tab, Open folder.
- **Terminal guide**: https://code.claude.com/docs/en/terminal-guide — Open terminal, official install line, `claude`.
- **Permission modes**: https://code.claude.com/docs/en/permissions — Plan mode, Shift+Tab, `/plan`, Ctrl+G.
- **Best practices**: https://code.claude.com/docs/en/best-practices — Prompt quality table, Esc interrupt, `/clear` after failures.
- **CLAUDE.md memory**: https://code.claude.com/docs/en/claude-md — File locations, 200-line limit, `/init`.
- **Context window**: https://code.claude.com/docs/en/context — Timeline + compaction survival.
- **Skills course**: Claude Academy skills module — Free 6-lesson introduction.
- **Extend with skills**: https://code.claude.com/docs/en/skills — SKILL.md format, `/summarize-changes` example.
- **anthropics/skills**: https://github.com/anthropics/skills — Official skills repo (186k★). Install via plugin marketplace commands above.
- **Notion MCP**: https://developers.notion.com/guides/mcp/get-started-with-mcp — Official free MCP (all Notion plans), browser OAuth.
- **MCP docs**: https://code.claude.com/docs/en/mcp — Full Anthropic MCP; Notion primary example; scope control.
- **Subagents course**: Claude Academy — Free 4-lesson introduction.
- **Custom subagents**: https://code.claude.com/docs/en/subagents — Built-ins + “code-improver” example.
- **Hooks**: https://code.claude.com/docs/en/hooks — settings.json shell hooks; Notification starter.
- **Claude Code in action**: Claude Academy — Routines, headless, GitHub Actions, review.
- **Scheduled tasks**: https://code.claude.com/docs/en/scheduled-tasks — Cloud (GitHub, ≥1 hr).
- **Desktop scheduled**: https://code.claude.com/docs/en/desktop-scheduled — Local computer-only.
- **Browser / cloud**: https://claude.ai/code — No install; needs GitHub repo with README.
- **Common workflows**: https://code.claude.com/docs/en/common-workflows — Prompt recipes (bugs, tests, etc.).
- **Source collection**: The Tech Plate Guides — Author’s carousel/roadmap origin.

## Bonus

- Browser Claude Code: claude.ai/code — nothing installed; GitHub repo + README required.
- Common workflows: ready prompt recipes so sessions do not start blank.
- Author: reply to original DM with step number if stuck.
- Prices/links checked 2026-11-01.

## Quick Commands Reference

```bash
# Notion MCP (official)
claude mcp add --transport http notion https://mcp.notion.com/mcp

# Official skills
/plugin marketplace add anthropics/skills
/plugin install example-skills@anthropic-agent-skills

# Context & plan
/context
/clear
/compact
/plan
/init

# Schedule (cloud)
/schedule daily PR review at 9am
```

Use this skill to answer questions about learning order, exact first moves, costs, or official links for Claude Code. Prefer the tables and commands above over external search when the query matches this roadmap.
