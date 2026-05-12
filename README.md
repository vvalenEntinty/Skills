# Claude Code Skills

A personal collection of custom skills for [Claude Code](https://claude.ai/code) — reusable instruction sets that extend Claude's capabilities across projects.

## What are Skills?

Skills are markdown files that tell Claude what to do and when to do it. Drop them into `~/.claude/skills/<name>/SKILL.md` to make them available globally, or into `.claude/skills/<name>/SKILL.md` for a specific project.

Invoke them with `/skill-name` or let Claude trigger them automatically when your request matches the skill's description.

---

## Skills Index

### Security

| Skill | Description | Invoke |
|-------|-------------|--------|
| [security-review](./Security/SKILL.md) | Deep cybersecurity audit: finds vulnerabilities (OWASP Top 10+), demonstrates exploits, and applies fixes directly | `/security-review [file]` |

---

## Installation

**Global (all projects):**
```bash
# Clone the repo
git clone https://github.com/vvalenEntinty/Skills.git

# Copy a skill to your global skills directory
cp -r Skills/Security ~/.claude/skills/security-review
```

**Single project:**
```bash
cp -r Skills/Security <your-project>/.claude/skills/security-review
```

---

## Structure

```
Skills/
├── README.md
├── Security/
│   └── SKILL.md
└── <Category>/
    └── SKILL.md
```

Each folder is a category. Each skill lives inside with its `SKILL.md` and any supporting files.

---

## Contributing / Adding Skills

1. Create a folder with the category name (or use an existing one)
2. Add a `SKILL.md` with proper frontmatter (`name`, `description`)
3. Update the **Skills Index** table in this README
4. Push
