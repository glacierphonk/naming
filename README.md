# naming

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill for naming products, SaaS tools, brands, and projects.

Metaphor-driven naming that produces memorable, meaningful names — and avoids AI slop.

## What this does

When invoked, this skill guides Claude through a structured naming process:

1. **Naming brief** — establish what the product does, who it's for, what it should feel like
2. **Metaphor exploration** — map conceptual territories before brainstorming names
3. **Candidate generation** — produce names grounded in metaphor, not thesaurus surfing
4. **Filtering** — kill AI slop and anti-patterns
5. **Evaluation** — score and compare finalists with a weighted rubric
6. **Availability checking** — verify domains, handles, and package names
7. **Decision** — present top candidates with origin stories and trade-offs

## Install

### As a project skill (this project only)

Clone or copy the repo contents into your project's `.claude/skills/naming/` directory:

```bash
# From your project root
mkdir -p .claude/skills
git clone https://github.com/glacierphonk/naming.git .claude/skills/naming
```

### As a personal skill (all projects)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/glacierphonk/naming.git ~/.claude/skills/naming
```

## Usage

In Claude Code:

```
/naming
```

Then describe what you need a name for. Claude will walk you through the full process.

You can also reference the skill naturally in conversation — describe your naming challenge and Claude will pull in the relevant reference files.

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Entry point — process overview and navigation |
| `principles.md` | Core naming principles (metaphor, real words, compounds, length) |
| `phonosemantics.md` | Sound-meaning connections — how sounds convey attributes |
| `anti-patterns.md` | AI name slop, fatal flaws, red flags checklist |
| `metaphor-mapping.md` | How to explore metaphor territories + starter maps |
| `cultural-references.md` | When mythology/literature/science references work vs. fail |
| `brand-architecture.md` | Naming within brand families and product lines |
| `availability.md` | Platform checking workflow and domain landscape |
| `case-studies.md` | Real product name origins and analysis |
| `evaluation.md` | Scoring rubric, comparison framework, decision checklist |

## Philosophy

**Names are compressed stories, not labels.** The best names plant a concrete image that unfolds into understanding — what the product does, what it feels like, where it comes from.

This skill is opinionated:

- **Metaphor over thesaurus.** Don't search for synonyms of your product's category. Explore what else in the world works like your product.
- **Real words over invented words.** Real-word brand names have ~68.8% recall vs ~38.1% for invented names. The brain follows the path of least resistance.
- **Story over sound.** A name with a great origin story and average sound will outperform a name with perfect phonetics and no story.
- **Kill AI slop.** Suffixes like -ly, -ify, -able, meaningless portmanteaus, and thesaurus extraction produce polished-but-interchangeable names. This skill actively filters them out.

## Contributing

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions, file structure, and how to add language files or case studies.

## License

MIT
