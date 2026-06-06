# Slide Outline — Agent-Driven Software Development for Computational Geoscientists

## Proposed slides

| # | Title | Content summary |
|---|---|---|
| 1 | **Agent-Driven Software Development for Computational Geoscientists** | Title slide |
| 2 | **80% and 800: why this matters now** | Opening impact statement — Claude authoring >80% of Anthropic's production code; 800 fixes, 1,000× error reduction, four years of work |
| 3 | **From chat to agent: what actually changes** | Side-by-side comparison: chat (you paste, you execute) vs agent (reads repo, writes files, runs commands, iterates) |
| 4 | **When do agents add value?** | Decision framework table: well-suited tasks (boilerplate, scaffolding, porting, cross-cutting) vs poorly-suited (novel algorithm design, unverifiable outputs) |
| 5 | **The right mental model** | "Capable but junior collaborator": needs good briefs, output must be reviewed, cannot be trusted on scientific correctness without verification |
| 6 | **The landscape (mid-2026)** | Overview diagram positioning tools by autonomy × IDE-integration: ChatGPT/Codex, Claude Code, Copilot, Cursor, Devin |
| 7 | **What Oxford researchers already have** | ChatGPT Edu (free via SSO), Codex (consent forms required), OeRC AI Competency Centre resources |
| 8 | **Claude and Claude Code** | Key tiers (Pro $17, Max $100/$200), what Claude Code actually does, strengths (local execution, CLAUDE.md, large codebase comprehension) |
| 9 | **GitHub Copilot** | Free tier, Pro $10/mo, agent mode in VS Code, multi-model backend; note on new sign-up pause (April–June 2026) |
| 10 | **Cursor and Devin Desktop** | Cursor ($20/mo, VS Code fork, polished); Devin ($20/mo, highest autonomy, formerly Windsurf — the rebrand should be called out explicitly) |
| 11 | **Choosing a tool: a decision tree** | Visual decision tree: start with Oxford provision → VS Code user? → want full IDE integration? → sustained heavy dev? |
| 12 | **Before you start: scope the task** | The five questions (deliverable, success criterion, what the agent needs, what it must not do, is this the right tool?) |
| 13 | **Providing context effectively** | CLAUDE.md / `.github/copilot-instructions.md`; scientific domain context; specific file paths over vague descriptions |
| 14 | **Context management** | Why context accumulates and costs money; compact tasks; `/compact`; start fresh contexts; don't paste full files |
| 15 | **Working safely with Git** | Always on a branch; commit checkpoints; review diffs before merging; `.gitignore` hygiene; the canonical safe workflow snippet |
| 16 | **Verifying outputs** | Write tests alongside code; compare to reference/analytical solution; check physical constraints; run existing test suite; read the code |
| 17 | **Claude Code in depth** | CLAUDE.md (what to put in it, `/init`); plan mode (Shift+Tab, four-phase workflow); parallel agents and worktrees; top mistakes |
| 18 | **Codex in depth** | The four products (App, CLI, Cloud, extension); Skills; Automations; GitHub issue → PR workflow |
| 19 | **Cost: how it adds up** | Multiplicative token use explained; common causes of overspend; control strategies (model matching, `/compact`, billing alerts) |
| 20 | **Cost comparison at a glance** | Simplified table: free tier, cheapest paid, rough task cost, when each tier makes sense |
| 21 | **Failure mode #1: scientific correctness** | Own slide, prominent — sign errors, unit errors, plausible-but-wrong results; why this is especially dangerous; mitigation |
| 22 | **Other technical failure modes** | Hallucinated APIs/constants; dependency issues; repository damage; reproducibility (non-determinism, implicit deps) |
| 23 | **Security, governance, and student training** | Data handling (don't send sensitive data); attribution/licensing; the dual role of agents for students (productivity *and* learning tool) |
| 24 | **Summary: when to use agents** | Concise when-to/when-not-to table or bullets — a takeaway reference |
| 25 | **Live demo** | Brief framing slide for the optional demo |
| 26 | **Discussion** | Structured discussion questions |

**Total: 26 slides** (including title and discussion). At 35 min target, that is ~1.3 min/slide for content slides, which is comfortable given some slides will be 30 seconds and others 3 minutes.

---

## Content flagged as too dense for slides → speaker notes

- **Full pricing tables** (§2.1–2.5): all the tier-by-tier details. Slides 8–10 should show only the key tiers; the full breakdown is better as a handout or speaker note.
- **Anthropic API pricing table** (§2.7): the per-token numbers are useful in cost discussion but too granular for a slide; a simplified 3-row version (Haiku/Sonnet/Opus) on slide 20 would work.
- **Advanced Claude Code features**: worktrees, routines, plugins, MCP server details, Skills — good to mention briefly on slide 17 but individual bullet depth better as speaker notes.
- **Reproducibility section** (§3.7): good points but too fine-grained for a standalone slide; folded into slide 22 as a few bullets.
- **Context window size numbers** (§3.3): the 100K–200K token figures are useful context but don't need their own bullet on a slide.
- **The 7-entry chat-vs-agent comparison table** (§1): useful, but the full table is dense. Slide 3 could show a trimmed 4-row version and let the rest live in speaker notes.
