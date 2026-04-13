# Agent Instructions for inv-report-claude

This workspace uses the **WAT framework** (Workflows, Agents, Tools) to separate probabilistic AI reasoning from deterministic execution. See [CLAUDE.md](../CLAUDE.md) for the full architecture and philosophy.

## Quick Reference

- **Tools**: Python scripts in `tools/` — deterministic, testable, reusable execution
- **Workflows**: Markdown SOPs in `workflows/` — define objectives, inputs, tool sequences, outputs, and error handling
- **Credentials**: API keys in `.env` (gitignored) — never store secrets anywhere else
- **Deliverables**: Final outputs go to cloud services; local files are disposable

## Agent Responsibilities

Your role is **orchestration and decision-making**, not execution:

1. **Read the relevant workflow** before starting assigned tasks
2. **Check `tools/` first** — reuse existing scripts rather than creating new ones
3. **Execute deterministically** — run tools via `run_in_terminal` or equivalent, don't attempt multi-step operations directly
4. **Handle failures gracefully** — read error messages, fix the tool, retest, document in workflows
5. **Update workflows** when you discover better approaches or encounter recurring issues
6. **Keep `.env` secure** — never print credentials or commit secrets

## Why This Matters

Direct AI execution degrades fast. With 90% accuracy per step:
- 5 steps → 59% success
- 10 steps → 35% success

By offloading to deterministic tools, you stay in your wheelhouse (reasoning and decision-making) and avoid cascading errors.

## Workflow Development Checklist

When creating or updating workflows:

- [ ] Clear objective statement
- [ ] Required inputs explicitly listed
- [ ] Tool sequence with rationale
- [ ] Expected outputs documented
- [ ] Edge cases and error handling defined
- [ ] Known constraints or rate limits noted

## Common Patterns

**Scraping or API calls:**
- Check `tools/` for existing scrapers first
- Create new tool if none covers your use case
- Update workflow with discovered limits (rate limits, timeout behavior, etc.)

**Data transformation:**
- Deterministic processing belongs in `tools/`
- AI-driven decisions stay in workflow or agent reasoning

**Cloud integration (Sheets, Slides, Drive):**
- Tools handle auth and API calls
- Deliverables go to cloud; local files are transient

## Example: Running a Workflow

```bash
# 1. Read the workflow
cat workflows/task_name.md

# 2. Identify required inputs
# (Credentials? Data files?)

# 3. Run the tool
python tools/script_name.py --arg1 value1

# 4. Validate output
# - Check for errors in .tmp/ or cloud output
# - If failed, fix tool and retest

# 5. Update workflow if you found new constraints
# - Rate limits discovered?
# - Better method found?
# - Add to workflow for next run
```

## File Organization

```
.github/
  copilot-instructions.md      ← You are here
.env                           # Credentials (gitignored)
CLAUDE.md                      # Framework philosophy and architecture
tools/                         # Python execution scripts
  script_name.py              # Deterministic operations
workflows/                     # Markdown SOPs
  task_name.md                # Objective, inputs, tool sequence, outputs
credentials.json, token.json   # OAuth tokens (gitignored)
.tmp/                          # Temporary processing files (disposable)
```

## Git Conventions

- **Never commit**: `.env`, `credentials.json`, `token.json`, `.tmp/`
- **Always commit**: Workflows, tools, CLAUDE.md, this file
- Tools should be version-controlled and evolve over time

## Getting Started

1. Check [CLAUDE.md](../CLAUDE.md) to understand the framework rationale
2. Review `workflows/` to see how tasks are structured
3. Look at `tools/` to understand available execution scripts
4. When assigned a task, read its workflow and execute the tool sequence
5. If something breaks: fix the tool, retest, update the workflow

---

**Last updated**: April 13, 2026  
**Framework**: WAT (Workflows, Agents, Tools)  
**Maintainer**: You
