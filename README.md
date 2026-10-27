# UX Lens

A skill that makes Claude Code (or any coding agent) check and build UI for usability.

Built on the foundation of [Nielsen's Heuristics - The Decision Lab](https://thedecisionlab.com/reference-guide/design/nielsens-heuristics), covering Jakob Nielsen's 10 usability heuristics ([original NN/g list](https://www.nngroup.com/articles/ten-usability-heuristics/)).

## Install

**Claude Code - all projects**
```bash
git clone https://github.com/aleymahmoud-ff/ux-lens.git
mkdir -p ~/.claude/skills
cp -r ux-lens/skills/ux-lens ~/.claude/skills/
```

**Claude Code - one project:** copy `skills/ux-lens` into `.claude/skills/` in your repo.

**Other agents (Cursor, Codex, Windsurf):** paste the content of `SKILL.md` into the agent's rules file (`.cursor/rules/`, `AGENTS.md`).

## Commands

| Command | What it does |
|---------|--------------|
| `/ux-lens review <target>` | Full audit, findings table, no code changes |
| `/ux-lens fix <target> [min-severity]` | Review and fix issues at or above severity (default 3) |
| `/ux-lens check <numbers> <target>` | Review only listed heuristics, e.g. `check 5,9 app/form.tsx` |
| `/ux-lens build <description>` | Build UI applying all checks |

Heuristic reviews find likely problems early. They do not replace testing with real users.
