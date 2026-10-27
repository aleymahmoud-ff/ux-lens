# Nielsen Heuristics Skill

A skill that makes Claude Code (or any coding agent) apply Jakob Nielsen's 10 usability heuristics when building or reviewing UI.

## Install

**Claude Code - all projects**
```bash
git clone https://github.com/aleymahmoud-ff/nielsen-heuristics.git
mkdir -p ~/.claude/skills
cp -r nielsen-heuristics/skills/nielsen-heuristics ~/.claude/skills/
```

**Claude Code - one project:** copy `skills/nielsen-heuristics` into `.claude/skills/` in your repo.

**Other agents (Cursor, Codex, Windsurf):** paste the content of `SKILL.md` into the agent's rules file (`.cursor/rules/`, `AGENTS.md`).

## Commands

| Command | What it does |
|---------|--------------|
| `/nielsen-heuristics review <target>` | Full audit, findings table, no code changes |
| `/nielsen-heuristics fix <target> [min-severity]` | Review and fix issues at or above severity (default 3) |
| `/nielsen-heuristics check <numbers> <target>` | Review only listed heuristics, e.g. `check 5,9 app/form.tsx` |
| `/nielsen-heuristics build <description>` | Build UI applying all checks |

## Source

Based on [Nielsen's Heuristics - The Decision Lab](https://thedecisionlab.com/reference-guide/design/nielsens-heuristics) and Nielsen's original [10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/).

Heuristic reviews find likely problems early. They do not replace testing with real users.
