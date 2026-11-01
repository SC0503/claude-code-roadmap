---
name: claude-code-roadmap-full
description: "Complete Claude Code from-zero roadmap with security analysis, costs, 8 steps, first moves, official commands, and full extracted content from every linked resource (Claude Academy, docs, GitHub skills, Notion MCP, hooks, subagents, scheduling). Use when the user asks for Claude Code setup path, roadmap, learning order, CLAUDE.md, skills, MCP, subagents, hooks, or scheduled tasks."
type: knowledge
lifecycle: active
---

# Claude Code Roadmap From Zero — Full Extraction + Crawled Sources

Structured extraction of the official-resource roadmap (The Tech Plate Guides / Notion) plus full key content crawled from every linked resource. Verified 2026-11-01. All links official; no phishing or malicious payloads.

## Security Analysis & Warnings

Document is safe. Domains limited to academy.claude.com, code.claude.com, developers.notion.com, github.com/anthropics/skills, claude.ai, mcp.notion.com.

**Caution (standard Claude Code surfaces):**
- Hooks (Step 7): Execute shell from `~/.claude/settings.json` or project settings. Official starter is desktop notification. Review before adding any hook. Hooks run with full user permissions.
- MCP (Step 6): `claude mcp add --transport http notion https://mcp.notion.com/mcp` is official Notion command. Grants workspace access after OAuth. Scope carefully (`--scope user` / `--scope project` / local default).
- Plugins (Step 5): `/plugin marketplace add anthropics/skills` then `/plugin install example-skills@anthropic-agent-skills` targets official Anthropic repo. Plugins may include hooks/MCP.
- No destructive commands present in the roadmap.

## Prerequisites and Cost

| Item | Detail |
|------|--------|
| Claude Code access | Paid plan required. Pro $20/mo or $17/mo ($200/year). Free plan excludes it. Max/Team/Enterprise also include it. |
| Courses & docs | All free. Cost is only the Claude subscription. |
| Cloud scheduled tasks | Need GitHub repo; Anthropic servers; max 1/hour; paid plan. No local files. |
| Desktop scheduled tasks | No GitHub; runs only while app open + computer awake; one catch-up on wake. Access to local files. Min interval 1 min (Claude-set) or 1 hr (forms). |
| OS | macOS 13+ or Windows 10 1809+ for terminal. Desktop: Mac/Windows (Linux beta via apt/.deb). |

## Steps 1–8

| # | Step | Start with | Length | First move / Command |
|---|------|------------|--------|----------------------|
| 1 | Set it up | Claude Code 101 | 12 lessons, 1.5 hr | Open course → lesson “Installing Claude Code”. Desktop alternative: download app → Code tab → Open folder. Terminal: Cmd+Space → Terminal → follow guide step 2. |
| 2 | Plan mode | Lesson 5 of Claude Code 101 | 8 min | Shift+Tab until plan mode. Ask “how the project works”. Ctrl+G to edit plan. `/plan` for single prompt. |
| 3 | CLAUDE.md | CLAUDE.md file lesson (101 #8) | 10 min | `/init` → read output. Keep <200 lines. Project file shared; home file global. |
| 4 | Context | Context management lesson | 7 min | Next task switch: run `/clear` first. `/compact` to summarize; `/context` shows usage. |
| 5 | Skills | Introduction to agent skills | 6 lessons, 1 hr | First two lessons, then turn something typed twice into a skill. Copy summarize-changes example. |
| 6 | MCP | Notion’s MCP setup page | One command | `claude mcp add --transport http notion https://mcp.notion.com/mcp` then `/mcp` + sign in. |
| 7 | Subagents + hooks | Introduction to subagents | 4 lessons, 45 min | Lesson two: make first subagent. Hooks: copy Notification hook into settings.json. |
| 8 | Running it without you | Claude Code in action | 9 lessons, 1 hr | Jump to Automate repeat work → Routines and headless. `/schedule daily PR review at 9am` or desktop Scheduled. |

## Resource Links (with Crawled Content)

### Claude Code 101 (https://academy.claude.com/courses/claude-code-101)
- Structure: What is Claude Code? (2), Your first prompt (2), Daily workflows (3), Customizing Claude Code (5).
- Objectives: Explain AI coding agents; agentic loop + context + tools + permissions; install across terminal/VS Code/JetBrains/Desktop/web; effective prompts (manual/auto/Plan Mode); Explore → Plan → Code → Commit; context commands; CLAUDE.md; custom subagents/skills; MCP; hooks.
- Start: https://academy.claude.com/courses/claude-code-101/what-is-claude-code

### Desktop Quickstart (https://code.claude.com/docs/en/desktop-quickstart)
1. Download installer (macOS universal, Windows x64/ARM64) or Linux apt/.deb. Sign in.
2. Open Code tab in sidebar.
3. Environment selector → Local → Open folder. Pick model. Prompt. Review diffs (Auto/Accept edits/Manual/Plan).
- Requires paid subscription. Linux beta.

### Terminal Guide
- Open Terminal (Cmd+Space on Mac). Paste official install: `curl -fsSL https://claude.ai/install.sh | bash` (or Windows equivalent). Then `claude`.

### Best Practices (https://code.claude.com/docs/en/best-practices)
**Instead of / Try:**
| Instead of | Try |
|------------|-----|
| "fix the login bug" | "users report login fails after the session times out. look at token refresh in src/auth/, write a failing test that reproduces it, then fix it" |
| "add a calendar widget" | "follow the pattern in HotDogWidget.php and build a calendar widget that lets you pick a month and page between years. no new libraries" |

- Esc to interrupt. `/clear` after two failed corrections. Keep CLAUDE.md <200 lines. Use `/effort` not "think hard". Deterministic enforcement via hooks/deny rules.

### CLAUDE.md (https://code.claude.com/docs/en/claude-md)
- Locations: Project `./CLAUDE.md` or `.claude/CLAUDE.md` (shared); User `~/.claude/CLAUDE.md` (all projects); Local `./CLAUDE.local.md` (gitignore).
- `/init`: Analyzes codebase, suggests or creates. Does not overwrite existing. Target <200 lines. Put repeated corrections and non-code facts only.

### Skills (https://code.claude.com/docs/en/skills + https://github.com/anthropics/skills)
**Create skill:**
```bash
mkdir -p ~/.claude/skills/summarize-changes
```
SKILL.md example:
```markdown
---
description: Summarizes uncommitted changes and flags anything risky
---
## Current changes
!`git diff HEAD`

## Instructions
Summarize the changes above in two or three bullet points, then list any risks.
```
- Locations: Personal `~/.claude/skills/`, Project `.claude/skills/`, Plugin, etc.
- Official repo: `/plugin marketplace add anthropics/skills` then `/plugin install example-skills@anthropic-agent-skills` or `document-skills@...`.
- document-skills (docx/pdf/pptx/xlsx) are source-available production skills; example-skills are educational.

### Notion MCP (https://developers.notion.com/guides/mcp/get-started-with-mcp)
```bash
claude mcp add --transport http notion https://mcp.notion.com/mcp
```
Then `/mcp` → browser OAuth. Scopes: local (default), `--scope project` (.mcp.json), `--scope user`. Free on every Notion plan. No API key.

### MCP Overview (https://code.claude.com/docs/en/mcp)
- Official standard. Notion example matches above. Local > Project > User precedence. Trust required for project servers. OAuth tokens managed securely.

### Subagents (https://code.claude.com/docs/en/subagents)
Built-ins: Explore (read-only fast search), Plan (plan-mode research), General-purpose.
Custom example (code-improver):
```markdown
---
name: code-improver
description: Scans files and suggests improvements for readability, performance, and best practices.
tools: Read, Grep, Glob
model: sonnet
---
You are a code improvement specialist. For each issue you find, explain the problem, show the current code, and provide an improved version.
```
Invoke: "Use the code-improver agent to suggest improvements in this project." Locations: `~/.claude/agents/` or `.claude/agents/`.

### Hooks (https://code.claude.com/docs/en/hooks)
Notification hook (starter):
```json
{
  "hooks": {
    "Notification": [
      {
        "matcher": "permission_prompt",
        "hooks": [
          {
            "type": "command",
            "command": "${CLAUDE_PROJECT_DIR}/.claude/hooks/notify.sh"
          }
        ]
      }
    ]
  }
}
```
Hooks execute shell (or HTTP/MCP/prompt). Review all scripts. Place in `~/.claude/settings.json` or project `.claude/settings.json`. First hook Anthropic teaches is desktop alert on wait.

### Scheduled Tasks (https://code.claude.com/docs/en/scheduled-tasks)
- Cloud: Anthropic servers, GitHub repo required, ≥1 hour, no local files.
- Desktop: Local, app open + awake, local files, catch-up on wake.
- Example: `/schedule daily PR review at 9am` or claude.ai/code/routines. Desktop: Code tab → Scheduled → New task → Only on this computer.

### Other
- Browser Claude Code: https://claude.ai/code — nothing installed; GitHub repo + README required.
- Common workflows: Prompt recipes for bugs, tests, etc.

## Quick Commands Reference

```bash
# Notion MCP (official)
claude mcp add --transport http notion https://mcp.notion.com/mcp

# Official skills
/plugin marketplace add anthropics/skills
/plugin install example-skills@anthropic-agent-skills
/plugin install document-skills@anthropic-agent-skills

# Context, plan, init
/context
/clear
/compact
/plan
/init

# Schedule (cloud)
/schedule daily PR review at 9am
```

## Bonus

- Browser Claude Code: claude.ai/code — nothing installed; GitHub repo + README required.
- Common workflows: ready prompt recipes so sessions do not start blank.
- Author: reply to original DM with step number if stuck.
- Prices/links checked 2026-11-01.

Use this skill to answer questions about learning order, exact first moves, costs, official commands, or detailed content from the linked resources. Prefer the tables and extracted sections above.
