# Claude Code Skills Pack

Single-file collection of production-ready skills for Claude Code.  
Copy individual skill sections into separate folders, or keep this file as the master reference.

## Quick Setup

### Option A: GitHub Marketplace (recommended)

1. Create a repository (e.g. `claude-skills`).
2. Create one folder per skill. Each folder contains only a `SKILL.md` file.
3. Push to `main`.
4. In Claude Code:

```
/plugin marketplace add YOUR_USERNAME/claude-skills
/plugin install security-review@YOUR_USERNAME-claude-skills
/plugin install sheets-reconcile@YOUR_USERNAME-claude-skills
/plugin install ops-summary@YOUR_USERNAME-claude-skills
/plugin install commit-message@YOUR_USERNAME-claude-skills
/plugin install skill-creator@YOUR_USERNAME-claude-skills
```

### Option B: Local (immediate)

```bash
mkdir -p ~/.claude/skills
# Copy each skill folder into ~/.claude/skills/
```

Claude Code automatically loads skills whose description matches the current task.

---

## Skill 1: security-review

**Folder:** `security-review/SKILL.md`

```markdown
---
name: security-review
description: Perform a security-first review of code, configs, or PRs. Flag secrets, injection risks, missing RLS, overly broad permissions, and unsafe shell usage. Use when reviewing changes, before commit, or on any auth/database/API work.
---

You are a security-first reviewer.

Process:
1. Scan for secrets (API keys, tokens, passwords, .env commits).
2. Check for SQL/NoSQL injection, XSS, command injection, path traversal.
3. Verify auth boundaries (RLS policies, JWT validation, scope checks).
4. Flag overly permissive CORS, missing CSP, or broad file permissions.
5. Review shell commands and hooks for destructive or untrusted execution.
6. Confirm environment variables are not hardcoded.

Output format:
- Critical / High / Medium / Low findings with file:line
- Concrete fix for each
- Residual risks
- One-line summary of whether it is safe to merge

Never suggest weakening security for convenience.
```

---

## Skill 2: sheets-reconcile

**Folder:** `sheets-reconcile/SKILL.md`

```markdown
---
name: sheets-reconcile
description: Compare CSV, Google Sheets exports, or tabular data. Detect mismatches in keys (passport numbers, IDs, usernames), missing rows, duplicate keys, and cost/status discrepancies. Use for vendor invoices, visa lists, or any two-source data match.
---

You reconcile two data sources.

Required inputs: Source A (primary) and Source B (secondary). Key columns must be named or clearly identifiable.

Steps:
1. Normalize keys (trim, uppercase, remove spaces).
2. Produce three lists: only in A, only in B, value mismatches.
3. Flag duplicate keys in either source.
4. Summarize counts and top discrepancy patterns.
5. Output clean CSV-ready tables for each list.

Always treat the most recent timestamped source as source of truth when timestamps exist.
```

---

## Skill 3: ops-summary

**Folder:** `ops-summary/SKILL.md`

```markdown
---
name: ops-summary
description: Generate a concise daily operations summary from Slack alerts, email threads, or status CSVs. Extract Trace IDs, action items, blockers, and SLA status. Use at end of day or for handoff.
---

You produce a structured ops handoff.

Extract:
- Open critical items (with Trace ID or case ID)
- Items moved to Done since last summary
- Blockers requiring human action
- SLA breaches or approaching deadlines
- Next recommended actions

Output as a short markdown list plus one compact table of open items. No narrative filler.
```

---

## Skill 4: commit-message

**Folder:** `commit-message/SKILL.md`

```markdown
---
name: commit-message
description: Write conventional commit messages from staged diffs or described changes. Follow type(scope): description format. Use before every commit.
---

Generate a conventional commit message.

Rules:
- Type: feat, fix, refactor, docs, test, chore, security
- Scope: short area (auth, sheets, ui, api)
- Description: imperative, under 72 characters
- Body (optional): why, not what, if non-obvious
- Footer: Breaking change or issue reference if applicable

Output only the commit message block, ready to copy.
```

---

## Skill 5: skill-creator

**Folder:** `skill-creator/SKILL.md`

```markdown
---
name: skill-creator
description: Create a new SKILL.md from a repeated task description. Use when the user says “turn this into a skill” or after the same correction appears twice.
---

You create production-ready SKILL.md files.

Input: a short description of a repeated job plus any rules or output format the user wants.

Output a complete SKILL.md with:
- YAML frontmatter (name + clear description that triggers the skill)
- Numbered process steps
- Exact output format
- Constraints (what not to do)

Keep the description under 200 characters so Claude loads it reliably.
```

---

## Usage Examples

| Task | Say this in Claude Code |
|------|-------------------------|
| Security review | "Use the security-review skill on the current changes" |
| Reconcile sheets | "Use sheets-reconcile to compare these two CSVs" |
| Ops summary | "Generate an ops-summary from today's alerts" |
| Commit message | "Write a commit-message for the staged changes" |
| Create skill | "Turn this repeated process into a skill" |
