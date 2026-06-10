# Agent-Driven Software Development for Computational Geoscientists

## Seminar Notes — Mid-2026

**Target audience:** PhD students, postdoctoral researchers, research software engineers, and faculty in computational geoscience.

**Assumed background:** Experienced scientific programmers who have likely experimented with ChatGPT for coding; many familiar with Git and GitHub. Most not advanced AI users.

**Format:** 30–40 minute seminar + ~20 minutes discussion.

---

## Seminar Outline and Timings

| Segment | Duration | Notes |
|---|---|---|
| 1. What is agent-driven development? | 5 min | The conceptual shift |
| 2. The ecosystem — tools, pricing, Oxford access | 8 min | Current landscape |
| 3. Practical workflows | 8 min | How to actually work with agents |
| 4. Claude Code and Codex: deep dive | 7 min | Lessons from real use |
| 5. Cost, failure modes, and risks | 7 min | The sober assessment |
| 6. Live demo (optional) | 5 min | A focused illustration |
| Discussion | 20 min | Structured questions |

---

---

## Part 1 — What Is Agent-Driven Development?

### Real-world impact: why this matters now

This is not a distant prospect. Agents are already doing substantial work in production software development at leading technology organisations.

As of **May 2026**, **Claude authored over 80%** of the code merged into Anthropic's own production codebase.

In a concrete example from **April 2026**, Claude autonomously shipped **over 800 fixes** for a persistent class of API errors, reducing the error rate by a factor of **1,000**. An engineer estimated that this cleanup work would have taken a human developer **four years** to complete due to the cognitive load of managing the necessary code context.

This is not a story about AI replacing programmers. It is a story about a change in what programmers can accomplish — and about the importance of understanding how to work effectively and safely with these tools.

---

### The frontier is moving into the science

The software-engineering results above are no longer the whole story. Over the first half of 2026, frontier models began making credited contributions to science itself — not just to the code around it.

- **Mathematics — "Claude's Cycles" (March 2026).** Donald Knuth published a paper after Claude Opus 4.6 solved an open graph-theory conjecture he had worked on for decades, in roughly an hour across 31 guided explorations. The key step — recognising the problem's structure as a Cayley digraph — came from the model. (Stanford: `www-cs-faculty.stanford.edu/~knuth/papers/claude-cycles.pdf`)
- **Mathematics — Erdős problem #728 (January 2026).** Terence Tao reported that GPT-5.2 Pro solved an open Erdős problem "more or less autonomously", with the proof subsequently formalised in Lean. Tao's caveats matter: the achievement is more about *speed* than depth; he estimates only ~1–2% of open Erdős problems are simple enough for today's AI to solve with minimal human involvement, and on hard problems humans still map the strategy.
- **Across the sciences — OpenAI's GPT-5 science report.** OpenAI's "Early experiments in accelerating science with GPT-5" documents contributions across mathematics, physics, and biology — including a case where GPT-5 contributed the key idea that completed a proof for researchers Sawhney and Sellke. The researchers' framing: a "fast reasoning partner", with every step independently verified by humans.
- **Hypothesis generation — Anthropic Mythos 5 (June 2026).** In blinded comparisons, scientists preferred Mythos 5's molecular-biology hypotheses ~80% of the time over earlier models, and one proposed mechanism received independent experimental validation. In a week-long autonomous genomics run, it compiled single-cell data across 138 species and designed a cross-species cell-type model reportedly outperforming a recently published *Science* model at a fraction of the size. (Mythos 5 is a limited-release research model; Claude Fable 5, released 9 June 2026, brings Mythos-class capability to general availability.)

Two things are simultaneously true and should both be presented:

1. Agents are becoming genuine **scientific collaborators**: they propose approaches, check derivations, catch sign, unit, and mathematical errors that the researcher missed, and teach unfamiliar material effectively.
2. In every credited case above, **verification and final judgement remained human**. The pattern is "AI proposes, human verifies and decides" — not autonomous science.

The practical consequence for researchers: it is no longer accurate to treat an agent as *only* a junior software engineer that must be kept away from the science. Engaging it with the science — as a sparring partner, second reviewer, and tutor — is increasingly where the value is, provided the verification discipline described in Parts 3 and 5 is maintained.

---

### The conceptual shift

Most researchers will have encountered AI coding assistance as **chat-based help**: you describe a problem, the model produces a suggestion, you copy and paste it, you check it, you move on. This is genuinely useful, but it is fundamentally a *conversation*. You remain the operator of the keyboard; the AI offers advice.

**Agent-driven development is different.** An agent is given a task, is given access to your codebase and to a set of tools — file reading, file writing, shell execution, Git operations, web search, API calls — and is allowed to work autonomously through a plan, making decisions, taking actions, and iterating toward a result. Rather than answering questions, the agent *does things*.

The practical consequences of this shift are significant:

- A task can be described at a higher level of abstraction ("implement a finite-difference solver for this PDE and write tests for it") and the agent handles the details across multiple files and steps.
- The agent can read, understand, and modify large amounts of code that it was not directly shown.
- Multi-step workflows — clone a repository, understand the codebase, identify a bug, write a fix, run tests, commit, open a pull request — can be executed without constant human direction.
- But the agent can also make persistent mistakes, consume significant resources, and produce plausible-sounding but subtly wrong results.

The key mental model for researchers to internalise: **an agent is a capable collaborator who needs good briefs, produces output that must be reviewed, and should not be trusted on scientific correctness without verification**. It is junior *in your project and your specific problem* — it does not know your conventions, your data quirks, or your unstated constraints. But it is markedly less junior in the science with every model generation: a current frontier agent will often propose sound scientific approaches and catch mathematical or physical errors that you missed. The human role is therefore best described not as "the only one who can engage with the science" but as **the one who decides and verifies**.

### How this differs from traditional coding assistance

| Feature | Chat-based (e.g., ChatGPT prompt) | Agent-based (e.g., Claude Code, Codex) |
|---|---|---|
| Scope | Single question or snippet | Multi-file, multi-step task |
| Execution | You copy-paste and run | Agent reads, writes, and executes |
| Codebase awareness | What you paste in | Reads full repository |
| Iteration | Manual | Agent self-corrects |
| Git integration | None | Branches, commits, PRs |
| Risk | Low (you control every change) | Higher (agent modifies files directly) |
| Cost | Low to moderate | Potentially high |

### What kinds of tasks benefit most?

Agent-driven development is **not always the right choice**. It adds overhead (time, money, and risk of agent error) and is most valuable for tasks that are:

- **Well-defined but tedious**: boilerplate, test writing, documentation generation, refactoring to a consistent style.
- **Exploration tasks**: "understand this 10,000-line codebase I inherited and give me a map of its structure."
- **Cross-cutting changes**: "rename this function everywhere and update all callers."
- **Scaffolding**: setting up a new project, CI/CD pipeline, packaging, installation scripts.
- **Port/translation**: converting Fortran or Matlab routines to Python.
- **Scientific sparring**: deriving and checking equations, critiquing a method, explaining unfamiliar techniques, reviewing code or derivations for scientific errors.

It is **less suited** to:

- Decisions that are yours to make: research direction, which approximation is acceptable, what counts as a valid result (agents can inform and critique these decisions, but cannot own them).
- Extremely exploratory or poorly-scoped work.
- Tasks where the output cannot be tested or checked objectively — if neither you nor the agent can verify it, neither of you should trust it.

A useful heuristic — updated for 2026: the old advice was "if you could brief a skilled programmer who doesn't know your field, an agent can do it." Frontier agents increasingly *do* know the field, so the boundary has moved. The boundary now is **ownership of decisions and verification**: an agent can engage with the science — propose, derive, check, explain — but the decision about what is scientifically acceptable, and the final verification, are yours.

---

---

## Part 2 — The Ecosystem (Mid-2026)

### 2.1 Claude and Claude Code (Anthropic)

**What it is:** Anthropic's Claude models (Haiku, Sonnet, Opus) power both a general-purpose chat interface (claude.ai and the Claude desktop app) and a dedicated agentic coding tool, **Claude Code**, which runs as a terminal CLI, an IDE extension (VS Code, JetBrains), or within the Claude desktop app.

**Pricing (as of June 2026):**

| Plan | Price | Claude Code included? | Notes |
|---|---|---|---|
| Free | $0 | No | Limited usage; Sonnet available |
| Pro | $17/mo (annual) or $20/mo | Yes | Suitable for short coding sprints in small codebases |
| Max 5x | $100/mo | Yes | 5× more usage than Pro; good for regular use |
| Max 20x | $200/mo | Yes | 20× more usage than Pro; power users |
| Team | Contact | Yes | Centralised billing, SSO, admin controls |
| Enterprise | Contact | Yes | Custom deployment, Bedrock/Vertex support |

**API pricing (for Claude Console / pay-as-you-go use):**

- Haiku 4.5: ~$0.80/$4.00 per million input/output tokens (small, fast, cheap)
- Sonnet 4.6: standard mid-tier pricing
- Opus 4.8: $15/$75 per million tokens (standard); fast mode $30/$150 per million tokens

Note: "fast mode" for Opus 4.8 makes the model 2.5× faster at approximately 2× the token cost. It is available in research preview in Claude Code and on consumption-based plans.

**Claude Code — what it actually does:**

Claude Code runs locally in your terminal (no remote code index). It:

- Reads your repository without you selecting files manually (uses agentic search)
- Writes, edits, and creates files across the project
- Executes shell commands (test runners, build systems, Git)
- Integrates with GitHub and GitLab (issues → PRs workflow)
- Supports CLAUDE.md memory files for persistent project instructions
- Supports MCP (Model Context Protocol) for tool integrations
- Has an "auto mode" (safer long-running alternative to `--dangerously-skip-permissions`)
- Supports "routines": scheduled or event-triggered tasks
- Can be run in parallel instances via the desktop app

**Models available in Claude Code:** Haiku 4.5, Sonnet 4.6, Opus 4.8.

**Strengths:**

- Strong codebase comprehension across large repositories
- Good at multi-file, multi-step tasks
- CLAUDE.md system allows rich project-specific customisation
- Runs locally — code never sent to a remote index
- Strong safety defaults (asks before modifying files or running commands)
- Excellent scientific Python, Fortran, C++ capability
- MCP integrations (GitHub, filesystem, databases, custom tools)

**Weaknesses:**

- Subscription costs add up quickly for heavy agentic use
- Max plan is required for sustained heavy use ($100–200/mo)
- Long tasks can consume substantial tokens
- No first-party compute: runs against Anthropic API (either via subscription credits or Console billing)

**Best suited to:** Researchers who do substantial software development and want a deeply integrated, locally-running agent. The Max plan makes sense for anyone doing this as a significant part of their work.

---

### 2.2 ChatGPT and OpenAI Codex

**ChatGPT pricing (as of June 2026, UK pricing shown):**

| Plan | Price | Notes |
|---|---|---|
| Free | £0 | GPT-5.5 Instant with limits; limited Codex access |
| Go | £7/mo | More messages; may include ads |
| Plus | £20/mo | GPT-5.5 Thinking, expanded agent mode, expanded Codex usage |
| Pro | From £89/mo | 5× or 20× more usage; maximum Codex tasks; GPT-5.5 Pro |
| Team/Business | Contact | Dedicated workspace, no model training, admin controls |
| Enterprise | Contact | SAML SSO, compliance, data residency options |
| Edu | Institutional | Free at point of use for Oxford staff and students (see below) |

**OpenAI API pricing (flagship models, June 2026):**

- GPT-5.5: $5/$30 per million input/output tokens
- GPT-5.4: $2.50/$15 per million tokens
- GPT-5.4 mini: $0.75/$4.50 per million tokens
- Batch API: 50% discount for async processing (useful for bulk analysis tasks)

**Codex (OpenAI's agentic coding product):**

Codex is OpenAI's dedicated coding agent, available in multiple forms:

- **Codex App** (macOS, Windows desktop): visual workspace for coordinating parallel coding agents, worktrees, multi-project management.
- **Codex Cloud/Web** (chatgpt.com/codex): connects to a GitHub repository, suggests changes as pull requests.
- **Codex CLI** (`npm i -g @openai/codex`): terminal-based coding agent, similar to Claude Code.
- **Codex IDE extensions**: VS Code, Cursor, and Devin Desktop extensions.
- **GitHub Codex integration**: Codex can be assigned as a GitHub assignee to work on issues and open PRs.

Codex is powered by models in the GPT-5.x-Codex series (e.g. GPT-5.2-Codex, GPT-5.3-Codex) — models specifically fine-tuned for agentic coding tasks.

**Strengths of ChatGPT/Codex:**

- Widest user base; most tutorials and community resources
- Strong general coding capability
- Codex App's multi-agent parallel workflow is distinctive
- Well-integrated with GitHub (cloud agent, PR review, issue triage)
- ChatGPT Edu provides Oxford researchers free institutional access

**Weaknesses:**

- Codex access currently requires consent forms at Oxford (see below)
- Less cohesive project memory system compared to Claude's CLAUDE.md
- Pro pricing can be expensive for moderate users

---

### 2.3 GitHub Copilot

**What it is:** Microsoft/GitHub's AI assistant, deeply integrated into IDEs (VS Code, JetBrains, Visual Studio, Xcode, Neovim, Eclipse). Originally inline completions; now includes chat, agent mode, cloud agent, and code review.

**Pricing (June 2026):**

> **Important note:** As of April–June 2026, new sign-ups for Copilot Pro, Pro+, Max, and student plans are **temporarily paused**. Existing plans can be upgraded. Self-serve Business sign-ups on GitHub Free/Team are also paused. This situation may change; check github.com/features/copilot for current status.

| Plan | Price | Key features |
|---|---|---|
| Free | $0 | 2,000 completions/month; limited chat; no cloud agent |
| Pro | $10/mo | Unlimited completions; cloud agent; 3rd-party agents (Claude Code, Codex); $15/mo AI credits |
| Pro+ | $39/mo | Premium models (Opus); 4×+ usage; $70/mo AI credits; audit logs |
| Max | $100/mo | 2.9×+ usage over Pro+; $200/mo AI credits; priority access |
| Business | $19/seat/mo | Team management; pooled AI credits; policy controls |
| Enterprise | $39/seat/mo | All Business features plus larger credit pool, priority models |

**AI Credits model:** GitHub Copilot now operates on a hybrid model — plans include a monthly AI credit allowance for agent and premium model usage. Overage is charged at usage-based rates.

**Models available** (varies by plan): Claude Haiku 4.5, Claude Sonnet 4.6, Claude Opus 4.7/4.8, Gemini 2.5 Pro, Gemini 3.x series, GPT-5 mini, GPT-5.2 through GPT-5.5 series, MAI-Code-1-Flash (Microsoft's own model), and others.

**Agent mode in VS Code:** As of mid-2026, Copilot's agent mode in VS Code allows multi-step task execution with file editing, terminal access, and MCP tool integration — comparable to Claude Code within the IDE.

**GitHub Copilot cloud agent:** Can be assigned issues on GitHub, works in a cloud environment, and opens PRs. Third-party agents (Claude Code, OpenAI Codex) can also be assigned issues this way from Pro+ onwards.

**Strengths:**

- Deeply integrated into VS Code and other IDEs; minimal context switching
- Free tier is genuinely useful for completions and inline chat
- Works with multiple model backends (not locked to one provider)
- Strong GitHub integration (PR summaries, code review, issue → PR workflows)
- MCP support for tool integrations
- Education/student plans available

**Weaknesses:**

- Credit-based billing for agent use can be opaque
- New sign-ups currently paused (mid-2026)
- Agent mode less mature than Claude Code for sustained multi-step work
- Quality varies by model selection

**Best suited to:** Researchers who live in VS Code and want AI assistance deeply woven into their IDE workflow, without switching tools. The free tier is the lowest-friction starting point.

---

### 2.4 Cursor

**What it is:** A VS Code fork (from Anysphere, Inc.) with deeply integrated AI features — inline completions, chat, agent mode, cloud agents, code review (Bugbot). Cursor maintains a separate product from VS Code but supports most VS Code extensions.

**Pricing (June 2026):**

| Plan | Price | Notes |
|---|---|---|
| Hobby (Free) | $0 | Limited agent requests; limited Tab completions |
| Pro | $20/mo | Extended agent limits; frontier models; MCPs, skills, hooks; cloud agents |
| Teams | $40/user/mo | Centralised billing; team marketplace; Bugbot code review; SSO |
| Enterprise | Custom | Pooled usage; SCIM; audit logs; access controls; priority support |

**Key features:**

- **Tab**: Cursor's completion model, trained specifically for code editing (not just completion).
- **Agent mode**: Multi-file editing with file system access and terminal.
- **Bugbot**: AI-powered code review on PRs (usage-based billing).
- **Cloud agents**: Background tasks with team-shared context.
- **MCP support**: Tool integrations.
- **Skills and hooks**: Custom instructions and workflow automation.
- **Marketplace**: Internal rules, skills, and plugins shared across a team.

**Strengths:**

- Polished, cohesive IDE experience
- Background agents and cloud automation
- Team marketplace for sharing project-specific rules
- Supports multiple model backends
- Active community and rapid feature development

**Weaknesses:**

- Forked from VS Code — not the same as VS Code; some extensions behave differently; settings diverge over time
- $20/mo Pro tier is competitive but adds up alongside other tools
- Rapid product evolution means features/pricing may shift

**Best suited to:** Researchers who want a fully integrated IDE + agent experience and are comfortable using a VS Code fork. Strong choice if you want a single tool that does everything.

---

### 2.5 Devin (formerly Windsurf Desktop)

**What it is:** Cognition AI's Devin is a fully autonomous software engineering agent. **Windsurf** (the IDE previously developed by Codeium) was acquired by Cognition in 2025 and is now rebranded as **Devin Desktop** — the IDE you use to interact with Devin agents and to code alongside them. The Devin product spans a cloud agent (Devin Cloud) and the local IDE (Devin Desktop).

**Pricing (June 2026):**

| Plan | Price | Notes |
|---|---|---|
| Free | $0 | Light agent quota; limited models; unlimited inline edits and Tab |
| Pro | $20/mo | Increased quotas; frontier models (OpenAI, Claude, Gemini); SWE 1.6 and open-source models; Devin Cloud |
| Max | $200/mo | Significantly higher quotas; everything in Pro |
| Teams | $80/mo + $40/full user/mo | Unlimited members; centralised billing; admin dashboard; unlimited Devin Desktop |
| Enterprise | Custom | Dedicated VPC; SAML/OIDC SSO; dedicated account team |

**Devin's SWE model:** Devin has its own proprietary SWE (Software Engineering) model, with SWE 1.6 being the latest generation. This model is available free on Pro plans alongside standard frontier models.

**Key capabilities:**

- Full agentic task execution: Devin can be given an issue and will plan, code, test, and submit a PR autonomously
- Concurrent sessions (unlimited on Max/Team/Enterprise)
- Integrations: Slack, Teams, Linear, Jira, GitHub, GitLab, Bitbucket
- Devin Desktop (formerly Windsurf): full IDE with agent integration, Tab completions, inline edits

**Usage model:** Plans include a daily/weekly usage allowance that refreshes automatically. Cost per message varies with model, task complexity, and reasoning required. Pro users can purchase extra usage at API pricing if they exceed their quota.

**Strengths:**

- Highest level of autonomy among the tools discussed
- SWE 1.6 model purpose-built for software engineering tasks
- Devin Desktop provides a polished IDE experience
- Strong integrations with project management tools
- Concurrent sessions allow parallel workloads

**Weaknesses:**

- Highest autonomy = highest risk of unintended changes if not properly bounded
- Pricing complexity (Teams base fee + per-seat fee)
- Less suited to one-off chat-style interactions; designed for sustained autonomous work
- Less focus on the scientific Python / numerical computing ecosystem

**Best suited to:** Teams with sustained, high-volume software development needs who are comfortable with a high-autonomy agent and have good Git workflows and review processes.

---

### 2.6 VS Code Agent Mode

VS Code (without Copilot, Cursor, or Devin Desktop) provides agent-like capabilities through:

- **GitHub Copilot extension** (agent mode): multi-step task execution with file editing, terminal, and MCP.
- **Claude Code extension** (Anthropic): Claude Code's full capabilities directly in the VS Code sidebar.
- **Codex IDE extension** (OpenAI): Codex coding agent within VS Code.
- **MCP server support**: tools exposed to any compatible agent.
- **Instruction files** (`.github/copilot-instructions.md`, `.instructions.md`): persistent instructions for Copilot agent.
- **Prompt files** (`.prompt.md`): reusable task prompts.

The VS Code agent ecosystem is now genuinely capable: agent mode can read your repository, edit files across multiple directories, execute terminal commands, and iterate on its own output. **You do not necessarily need a dedicated agent IDE** — if you already use VS Code, you may have most of what you need.

---

### 2.7 Anthropic API pricing (for direct API users)

For researchers who want fine-grained control and pay-per-use (e.g., for scripted workflows or pipelines):

| Model | Input ($/M tokens) | Output ($/M tokens) | Typical use |
|---|---|---|---|
| Haiku 4.5 | ~$0.80 | ~$4.00 | High volume, simple tasks |
| Sonnet 4.6 | ~$3.00 | ~$15.00 | General coding and analysis |
| Opus 4.8 | $15.00 | $75.00 | Complex reasoning, hardest tasks |
| Opus 4.8 (fast) | $30.00 | $150.00 | When speed matters more than cost |

For comparison, a 1M-token context is roughly 750,000 words — about 10–15 typical research papers. A complex agentic task on a medium-sized codebase might consume 50,000–500,000 tokens depending on scope.

---

### 2.8 University of Oxford institutional access

**ChatGPT Edu:**

- Available free at point of use to **all current Oxford staff and students**.
- Login via SSO (Single Sign-On): go to chatgpt.com, use your `abcd1234@ox.ac.uk` address.
- **What you get:** GPT-5.5 (unlimited), Canvas, web search, code interpreter. No training on your data by default. Covered by InfoSec's security assessment.
- **Weekly limits** on intensive features (from December 2025): ~20 GPT-5.5 Thinking messages, ~40 images, ~30 Codex queries, ~40 min voice mode per week. These reset weekly.
- **Elevated access**: Available via internal recharge (purchase through budget holder, GL code or PO required). Covers higher limits plus GPT-5.5 Pro and Deep Research.

**Codex at Oxford:**

- Available to all staff and students via consent forms (staff can also access Codex Cloud).
- **Codex Local**: complete the [Codex Local Consent form](https://unioxfordnexus.sharepoint.com/:l:/s/ITServices-AIMLCompetencyCentre/JAA5VRMMMX4TRoq0PAko9YUeAc_7mMOG9G5LawRq2Vy_Xw4) to use the Codex App and CLI locally.
- **Codex Cloud**: complete the [Codex Cloud Consent form](https://unioxfordnexus.sharepoint.com/:l:/s/ITServices-AIMLCompetencyCentre/JAB7wqs4VdFmQpEkBJz6CHe3AauDW4BnufuTvYTqR_d70tE) to connect a GitHub repository and work via the cloud.
- Codex usage counts against your ChatGPT Edu weekly limits (~30 queries/week).
- Training course: [Getting Started with Codex](https://canvas.ox.ac.uk/courses/289256) on Canvas.

**OeRC AI Competency Centre:**

- Run by the Oxford e-Research Centre as part of the University's digital transformation programme.
- Website: [oerc.ox.ac.uk/ai-centre](https://oerc.ox.ac.uk/ai-centre)
- Provides training, AI guides, tool guidance, and community.
- Relevant guides: [Getting started with AI for Coding](https://oerc.ox.ac.uk/ai-centre/ai-guides/getting-started-with-ai-for-coding), [Getting started with AI for Researchers](https://oerc.ox.ac.uk/ai-centre/ai-guides/getting-started-with-ai-for-researchers).
- Events: workshops, webinars, "AI Exploration Week", MondAI Roundup newsletter.
- Contact: [aimlcompetencycentre@it.ox.ac.uk](mailto:aimlcompetencycentre@it.ox.ac.uk)
- Oxford GPT Library: custom GPTs shared within the Oxford workspace.
- LinkedIn group: [OeRC AI Competency Centre](https://www.linkedin.com/groups/15690177/).

**Practical recommendation for Oxford researchers:**

1. Start with **ChatGPT Edu** via SSO — it is free, data-protected, and requires no setup.
2. Complete the **Codex consent forms** if you want to try agentic coding through Oxford's provision.
3. For deeper agentic coding work (Claude Code, Cursor, etc.), you will likely need a personal or group subscription — assess whether it is worth it for your workflow before committing.

---

### Summary comparison table

| Tool | Free tier | Cheapest paid | Agent capable | Local execution | Best starting point for... |
|---|---|---|---|---|---|
| ChatGPT Edu (Oxford) | ✅ Free via SSO | (elevated access via recharge) | Limited (Codex, weekly quota) | No (cloud) | Most Oxford users starting out |
| Codex (Oxford) | ✅ Free via consent form | Elevated via recharge | ✅ Yes | ✅ Yes (CLI/App) | Oxford users trying coding agents |
| Claude Code | Via Pro ($17/mo) | $17/mo | ✅ Yes | ✅ Yes | Individuals wanting deep code agents |
| GitHub Copilot | ✅ Free (limited) | $10/mo (paused new sign-ups) | ✅ Yes | In-IDE | VS Code users; team integration |
| Cursor | ✅ Free (limited) | $20/mo | ✅ Yes | In-IDE | All-in-one IDE + agent experience |
| Devin | ✅ Free (limited) | $20/mo | ✅ Yes (high autonomy) | ✅ Yes (Desktop) | Teams with sustained dev workloads |

---

---

## Part 3 — Practical Agent-Driven Development Workflows

### 3.1 Before you start: scoping the task

The most common mistake new users make is **throwing a loosely defined problem at an agent and expecting a solution**. Agents fail at vague tasks the same way junior programmers do — except they fail more confidently.

**Before starting any agent task, ask yourself:**

1. **What is the concrete deliverable?** ("A function that reads a NetCDF file and returns a masked numpy array for a given variable" is a deliverable. "Improve the data loading code" is not.)
2. **How will I know if it worked?** Define success criteria before you start. Ideally these are testable (unit tests, numerical checks, output comparisons).
3. **What does the agent need to know?** Domain context it cannot infer from the code. Scientific constraints. Conventions specific to your field or codebase.
4. **What should it NOT do?** Boundaries matter: "do not modify the existing API", "do not introduce new dependencies", "stay within the existing file structure".
5. **Is this the right tool for this task?** Some tasks take 2 minutes to do yourself and 20 minutes to explain to an agent. Others take you 2 hours and an agent 5 minutes.

### 3.2 Providing context effectively

Agents work best when they have the right context. This means:

**Repository context:**

- Use **CLAUDE.md** (for Claude Code) or **`.github/copilot-instructions.md`** (for GitHub Copilot) to give persistent project-level instructions. These are read at the start of every session. They should include: what the project does, the key conventions, the testing framework, anything the agent should always know.
- Be specific: "This project uses `pytest` for testing, `black` for formatting, and follows the NumPy docstring convention" is more useful than "this is a scientific Python project."

**Scientific and domain context:**

- Agents generally do not know your scientific domain well. If you are implementing a physical parameterisation, briefly explain the governing equations, the expected range of inputs and outputs, and any known numerical pitfalls.
- Don't assume the agent knows that your velocity field must be divergence-free, that your tracer values must be positive, or that your time step must satisfy the CFL condition.

**Task context:**

- A well-structured task request includes: the goal, the constraints, the testing criterion, and any relevant context from the codebase.
- Provide file paths and function names rather than descriptions: "the `advect()` function in `src/dynamics/advection.py`" is unambiguous; "the advection function" may not be.

### 3.3 Context management

**Context windows and their limits:**

All language models operate within a **context window** — the amount of text they can process at once. As of mid-2026, frontier models have large context windows (100K–200K+ tokens), but:

- Longer context = higher cost (you pay for every token in and out)
- Model attention quality can degrade over very long contexts
- Agents often accumulate irrelevant history that consumes context without adding value

**Practical strategies for context management:**

1. **Use compact tasks.** Break large tasks into sub-tasks with clear deliverables. A chain of well-scoped small tasks often costs less and produces better results than one large ambiguous task.

2. **Start fresh contexts frequently.** Long-running conversations with many back-and-forth turns accumulate stale context. When you have completed a sub-task and are moving on, start a new conversation or session.

3. **Use CLAUDE.md / instruction files** to store what needs to persist across sessions. You should not re-explain your project conventions in every session — put them in the instruction file.

4. **Summarise and compact.** Both Claude Code and Codex include a `/compact` command that summarises the current conversation and replaces it with a shorter summary, reducing token consumption while preserving the key decisions and code state. In Claude Code you can give it a focus: `/compact Focus on the API changes`. Use this when a session has been productive but is getting long, rather than abandoning the conversation history entirely.

5. **Avoid sending full large files unnecessarily.** If an agent needs to check a specific function, give it the file path and function name; it will read what it needs. Don't paste 2,000 lines of unrelated code into the prompt.

6. **Be selective with codebase size.** If your repository is very large (millions of lines), work in sub-directories or specify which parts are relevant. Agents are capable but not free.

### 3.4 Managing large codebases

Working with large repositories requires a different approach:

- **Use the agent to map the codebase first.** Ask it to describe the structure, identify key modules, and explain how components relate to each other. This is a high-value, low-risk use of agents and saves substantial onboarding time.
- **Work in well-defined modules.** Break changes into independent units. "Refactor the I/O module" is much safer than "refactor the entire codebase."
- **Maintain a CLAUDE.md hierarchy.** Claude Code reads CLAUDE.md files at each level of the directory tree. Use a top-level CLAUDE.md for project-wide context and per-directory CLAUDE.md files for module-specific context.
- **Do not give the agent write access to everything at once.** For safety, work in branches. Review before merging.

### 3.5 Using Git effectively with agents

**This is one of the most important practices.** Git is your safety net.

- **Always work on a branch.** Never have an agent work directly on `main`. Create a feature branch for every non-trivial agent task.
- **Commit checkpoints.** Ask the agent to commit after each logical step. If it goes wrong, you can `git checkout` to a known good state.
- **Review diffs before merging.** Treat the agent's output as you would a pull request from a collaborator you respect but do not fully trust yet.
- **Use `.gitignore` appropriately.** Make sure the agent cannot accidentally commit credentials, large data files, or build artefacts.

A typical safe workflow:

```
git checkout -b agent/feature-name
# Give task to agent
# Agent works, commits incrementally
# You review the diff with git diff or in the IDE
# You run tests
git checkout main
git merge --no-ff agent/feature-name
# or open a PR for team review
```

### 3.6 Verifying outputs

**Never trust agent output without verification.** This is especially critical in scientific computing, where bugs can produce plausible-looking but wrong results.

**Strategies:**

1. **Write tests as part of the task.** Ask the agent to write unit tests *at the same time* as it writes the code. A function without a test is a function you cannot verify.

2. **Compare to a reference.** For numerical routines, always check against:
   - An analytical solution where available
   - A simpler, slower reference implementation
   - Literature values or benchmark results
   - The previous (hand-written) implementation

3. **Check edge cases and physical constraints.** Ask the agent (or test yourself): does this function conserve mass? Does it produce positive definite outputs when expected? Does it degrade gracefully at boundaries?

4. **Run existing test suites.** Before accepting agent changes, run your full test suite. Agents often break existing tests in subtle ways when modifying shared utilities.

5. **Read the code.** This sounds obvious, but it is often skipped. Read what the agent actually wrote, not just whether the tests pass. The code is going into your research software; you are responsible for it.

6. **Use version control as a review tool.** `git diff` before accepting any agent commit.

7. **Use an agent as a second scientific reviewer.** Verification cuts both ways: a fresh agent session (ideally a different model from the one that wrote the code) asked to review code or a derivation for scientific errors will routinely catch sign errors, unit mistakes, and slips in the mathematics — in agent-written *and* human-written work. This is an addition to the checks above, never a replacement for reference values and your own reading: a second reviewer, not the only one.

### 3.7 Reproducibility considerations

Agents can introduce reproducibility risks:

- **Implicit dependencies.** The agent may install packages, pin versions, or introduce imports that are not in your `requirements.txt` or `environment.yml`.
- **Non-determinism.** If the agent uses randomness, make sure seeds are set.
- **Environment assumptions.** The agent may write code that works on its execution environment but not on your HPC cluster, a different OS, or a collaborator's machine.
- **Documentation.** If the agent writes code without docstrings, this impairs reproducibility by future users (including yourself six months later).

**Practical mitigations:** always ask the agent to update dependency files; always check that new code works in a clean environment; always review for hard-coded paths.

---

---

## Part 4 — Deep Dives: Claude Code and Codex

### 4.1 Claude Code: lessons from real use

#### CLAUDE.md files

The single most powerful feature of Claude Code that new users underestimate is the **CLAUDE.md file** (and the CLAUDE.local.md variant, which is gitignored). This file is read at the start of every session.

What to put in CLAUDE.md:

- Project purpose and structure (one paragraph)
- Key conventions: coding style, naming conventions, test framework
- What the agent should always do (e.g., "always update CHANGELOG.md when making user-facing changes")
- What the agent should never do (e.g., "never modify the Fortran source files in `src/legacy/`")
- How to run tests, build the project, check style
- Domain context relevant to the codebase
- Notes on the external data dependencies

CLAUDE.md files can be nested: a top-level CLAUDE.md for the whole project, and per-module CLAUDE.md files for specific subsystems. The agent reads them all.

**Creating a CLAUDE.md:** Run `/init` inside Claude Code to automatically generate a starter CLAUDE.md based on your project structure — it analyses your build systems, test frameworks, and code patterns to give you a useful starting point to refine.

**Keeping CLAUDE.md effective:** Keep it short and focused. For each line, ask: "Would removing this cause Claude to make mistakes?" If not, cut it. A bloated CLAUDE.md causes Claude to ignore its contents. Move domain knowledge or workflows that are only occasionally relevant to **Skills** files (see below) so they load on demand rather than on every session. Use emphasis ("IMPORTANT", "YOU MUST") for rules that need strict adherence. CLAUDE.md files can import other files using `@path/to/import` syntax, which is useful for linking to README files or team documentation.

**Global CLAUDE.md:** You can also maintain a `~/.claude/CLAUDE.md` that applies to all Claude Code sessions across all projects — useful for personal preferences and workflow conventions.

#### Planning mode

Claude Code has a dedicated **plan mode** — a permission mode in which Claude reads files and proposes a plan but makes **no edits or file changes** until you explicitly approve.

**Entering plan mode:**

- Start a session in plan mode: `claude --permission-mode plan`
- Toggle into plan mode mid-session: press `Shift+Tab`
- Exit plan mode to begin implementation: toggle again with `Shift+Tab`

**The recommended four-phase workflow for non-trivial tasks:**

1. **Explore** (in plan mode): Ask Claude to read the relevant files and understand the codebase. It can answer questions and map dependencies without making any changes.
2. **Plan** (in plan mode): Ask Claude to produce a detailed implementation plan. Press `Ctrl+G` to open the plan in your editor for direct review and editing before Claude proceeds.
3. **Implement** (switch out of plan mode): Ask Claude to implement the plan. It codes, runs tests, and iterates.
4. **Commit**: Ask Claude to commit with a descriptive message and open a pull request.

**When to use plan mode:** Plan mode adds overhead and is most valuable when the scope is unclear, the change touches multiple files, or you are unfamiliar with the part of the codebase being modified. For small, well-understood tasks (fixing a typo, adding a log line), skip planning and proceed directly.

**Codex `/plan` command:** Codex similarly supports a `/plan` command that produces a structured implementation plan for review before any code changes are made.

#### Auto mode and safety

Claude Code's **`--dangerously-skip-permissions`** flag allows it to run without asking permission for each action. This is fast but risky. The recommended alternative for long-running tasks is **auto mode**, which is a safer preset that still avoids constant interruptions while maintaining safety guardrails.

For research code that you rely on, prefer **permission-based mode** for any task that modifies existing files, and **always work on a branch**.

#### Parallel agents

The Claude desktop app and the web interface support running **multiple Claude Code instances in parallel**. This is useful for:

- Running independent tasks simultaneously (one agent tests, another documents, another implements a new feature)
- Exploring alternative implementations in parallel branches
- Reducing wall-clock time for large refactoring tasks

However, parallel agents consume tokens in parallel — costs multiply correspondingly. Budget carefully.

#### MCP integrations

Claude Code supports **Model Context Protocol (MCP)** servers, which allow it to interact with external tools:

- **GitHub MCP**: create issues, PRs, comment on code reviews
- **Filesystem MCP**: access files outside the project directory
- **Custom MCPs**: databases, simulation frameworks, observatory archives, HPC schedulers

For researchers, custom MCP servers can expose domain-specific resources (e.g., a catalogue service, a model parameter database, or a workflow manager) directly to the agent.

#### Skills

Claude Code supports **Skills** — reusable, domain-specific knowledge and workflow definitions stored as `SKILL.md` files in `.claude/skills/`. Unlike CLAUDE.md (which loads every session), skills load on demand when relevant, keeping the base context lean.

Skills can encode:

- Domain-specific conventions and patterns (e.g., how your project structures physical parameterisations)
- Repeatable workflows invoked directly (e.g., `/fix-issue 1234` to trigger a structured bug-fixing workflow)
- Code style conventions specific to a module or language

Invoke a skill explicitly with `/skill-name`, or let Claude load it automatically when the context suggests it is relevant.

#### Plugins

Claude Code has a **marketplace of plugins** — run `/plugin` to browse available plugins. Plugins bundle skills, hooks, subagents, and MCP servers into a single installable unit. Particularly useful:

- **Code intelligence plugins**: give Claude precise symbol navigation, "go to definition", and automatic error detection after edits — especially valuable for typed languages (Python with type hints, TypeScript, C++).
- **Framework-specific plugins**: provide Claude with detailed knowledge of particular frameworks or APIs relevant to your project.

Plugins are community and Anthropic-provided; review them before installation just as you would any dependency.

#### Worktrees

Claude Code supports **Git worktrees** for running parallel agent sessions on the same repository without edit conflicts:

```
claude --worktree feature-name
```

This creates a separate Git checkout on a new branch. Run the same command with a different name in a second terminal for a fully isolated parallel session. Useful for:

- Running independent tasks simultaneously (e.g., bugfix in one worktree, feature implementation in another)
- Experimenting with alternative approaches in isolation
- Background agents working while you continue in the main branch

#### Routines

**Routines** (introduced in Claude Code, April 2026) allow you to configure recurring tasks: scheduled, event-triggered, or API-called. For research applications, this could be:

- Nightly CI runs that use the agent to triage test failures
- Automatic PR review triggered on every PR
- Periodic documentation updates

#### Common mistakes with Claude Code

1. **Letting it run too long without checkpoints.** Long agent sessions accumulate errors and costs. Use commit-often workflows.
2. **Not reading CLAUDE.md.** The agent will make better decisions with good project instructions; don't neglect this.
3. **Asking for too much at once.** "Rewrite the entire data pipeline" is a recipe for a broken codebase. Break it into steps.
4. **Not verifying numerical correctness.** The agent will pass its own tests but may not test the science. You must.
5. **Using Opus for tasks that don't need it — or using a weaker model and then retrying.** Assess the complexity of a task before starting and choose accordingly. Simple tasks (formatting, documentation, routine refactoring, test generation) work well with Haiku or Sonnet. Reserve Opus for genuinely complex multi-step reasoning. Trying a task with one model and then re-running it with a stronger one wastes tokens on both runs.
6. **Ignoring context accumulation.** Very long conversations cost more and eventually degrade in quality. Use `/compact [instructions]` to summarise the current conversation — you can give compact a focus, e.g. `/compact Focus on the API changes made so far` — or start a fresh session with `/clear` between unrelated tasks.

---

### 4.2 Codex: lessons from real use

#### The Codex family

Codex is not a single product: it is a family of tools sharing a backend:

- The **Codex App** (desktop) is best for new users — visual, clear, manageable parallel tasks.
- The **Codex CLI** (`codex`) is best for power users — scriptable, terminal-native.
- **Codex Cloud** is best for GitHub-centric workflows — assign issues, receive PRs.
- The **Codex IDE extension** is best for those who want agent capabilities without leaving their editor.

#### Skills in Codex

The Codex App supports **Skills** — reusable, project-specific capabilities that the agent can invoke. Skills can encode:

- How to run the test suite for a specific project
- How to format code according to your conventions
- How to update documentation when code changes
- Domain-specific patterns (e.g., "when writing a scientific function, always include a physical units check")

This is the Codex analogue of CLAUDE.md, but more modular.

#### Automations

Codex supports **Automations** — agent behaviours that run unprompted in response to events. For research software, useful automations include:

- Issue triage: Codex reads new GitHub issues and labels/prioritises them
- CI failure analysis: Codex analyses test failures and suggests fixes
- PR review: Codex reviews every PR for style, potential bugs, and test coverage

#### Worktrees and parallel agents

The Codex App uses Git **worktrees** to support parallel agent tasks — each task runs in its own working tree, so agents do not conflict. This is the safest way to run multiple agents in parallel on the same repository.

#### GitHub integration

Codex's deepest value is in its **GitHub integration**. You can assign a GitHub issue to Codex (or to Claude Code, or to the GitHub Copilot cloud agent) and it will:

1. Read the issue
2. Explore the repository to understand the relevant code
3. Implement a fix or feature
4. Run tests
5. Open a PR with the changes

For routine issues (bug reports with clear reproduction steps, small feature requests, documentation updates), this workflow can be very efficient. For scientific correctness issues, **the PR must be carefully reviewed before merging** — the agent does not know your science.

#### Context management in Codex

Codex supports a `/compact` command analogous to Claude Code's — it summarises the current conversation to reduce token consumption when a session has been running long. Use it before switching to a new sub-task within the same session.

#### Cost patterns with Codex

Codex uses the ChatGPT Edu weekly allowance at Oxford (~30 queries/week). Beyond that, usage charges at API rates. For the free/institutional tier, budget your 30 queries as if they are valuable — use them for genuinely useful tasks, not exploratory chat.

For Pro/paid users, Codex costs are included in the plan allowance, with overage at API pricing.

---

---

## Part 5 — Cost, Failure Modes, and Risks

### 5.1 How costs arise

Token consumption in agent workflows is **multiplicative**, not linear. A single agentic task may involve:

1. The agent reading multiple files (input tokens)
2. The agent reasoning about the plan (output tokens)
3. The agent writing code (output tokens)
4. The agent reading the output of shell commands (input tokens)
5. The agent correcting mistakes (further output tokens)
6. The agent reading more context to understand an error (more input tokens)

A complex task on a medium-sized codebase can easily consume 100,000–500,000 tokens. At Opus 4.8 pricing ($15 input / $75 output per million tokens), a single complex task might cost $5–$50. On a subscription plan with usage credits, you may exhaust your monthly allocation with a few large tasks.

**Common causes of unnecessary expenditure:**

- **Long context accumulation**: Not clearing old conversation history. Each message in a long conversation re-sends the entire history.
- **Mismatched model selection**: Using Opus 4.8 ($15/$75 per M tokens) for tasks that Haiku 4.5 (~$0.80/$4 per M tokens) handles equally well, or retrying a failed task on a more expensive model rather than adjusting the prompt.
- **Redundant reads**: The agent reading the same large file multiple times in a session.
- **Verbose prompts**: Unnecessary context, full file pastes, long preambles.
- **Runaway agents**: An agent stuck in a loop that you are not watching.
- **Parallel agents**: Multiple simultaneous agents consuming tokens in parallel without corresponding benefit.

**Cost control strategies:**

1. **Match the model to the task before starting.** Assess the complexity and scope of the task and choose a model accordingly: Haiku or Sonnet for simple, well-defined tasks; Opus for complex multi-step reasoning. Trying a cheaper model and then re-running on a stronger one wastes tokens on both attempts. Conversely, using Opus for everything wastes money on tasks that Sonnet handles equally well.
2. **Use subscription plans for predictable workloads.** API billing can spike unexpectedly; a Pro or Max plan gives a monthly ceiling (with soft limits, not hard caps, but the incentive structure is clearer).
3. **Set context budgets.** Some tools allow you to specify maximum context lengths or cost thresholds.
4. **Work in focused sessions.** Shorter, more focused conversations cost less than long exploratory ones.
5. **Use `/compact` in Claude Code** to summarise long conversations.
6. **Monitor your usage.** Both the Anthropic Console and the OpenAI platform provide usage dashboards. Check them regularly.
7. **Use Batch API for non-interactive tasks.** OpenAI's Batch API gives 50% discounts for tasks that don't need immediate response. For bulk analysis (e.g., running an agent over many files or many test cases), this is significant.

---

### 5.2 Failure modes and risks

#### Scientific correctness risks

This is the most important failure mode for researchers. Agents can:

- Implement a physically plausible but numerically incorrect algorithm
- Make a sign error, an indexing error, or a unit conversion error that produces results in the right ballpark but wrong in detail
- Reproduce a well-known algorithm incorrectly (misremembering a paper)
- Miss domain-specific constraints (conservation laws, positivity constraints, CFL conditions)

**Why this is dangerous:** Unlike a software bug that produces a crash or obviously wrong output, a scientific error may produce results that look plausible. The agent is confident; the code runs; the tests pass; but the science is wrong.

**Mitigation:** Test against known solutions. Never deploy agent-written numerical code without validation against reference values. For any algorithm of consequence, read the implementation line by line.

**The check cuts both ways.** The same capability that produces confident errors also catches them: an agent asked to *review* a derivation or a numerical routine will frequently find sign errors, unit mistakes, and mathematical slips that the human author missed. Use an agent as an additional scientific reviewer of your own work as well as of agent output — a second reviewer, never the only one.

#### Plausible but incorrect outputs (hallucination in code)

Agents can:

- Invent API functions that do not exist
- Cite papers or constants incorrectly
- Use deprecated or removed features of libraries
- Make false claims about the behaviour of existing code

**Mitigation:** Always run the code. Check imports exist. Verify any cited physical constants or literature values independently.

#### Dependency hallucinations

Agents may suggest adding packages that:

- Do not exist on PyPI/conda
- Exist but have different API than stated
- Are not maintained or have known vulnerabilities
- Introduce incompatibilities with your existing dependencies

**Mitigation:** Review any new dependencies before installing. Check package existence and version independently. Review requirements.txt / environment.yml after every agent session.

#### Repository damage

Agents that have write access can:

- Delete files accidentally
- Overwrite files with incorrect versions
- Commit sensitive data (credentials, large data files)
- Break the Git history if given rebase or force-push capabilities
- Modify files outside the intended scope

**Mitigation:**

- Always work on branches, never on main
- Never give an agent force-push or history-rewriting permissions
- Check `.gitignore` before starting
- Use `git status` and `git diff` before every commit
- Keep backups of critical data files outside the Git repository

#### Over-trusting agents

Researchers who achieve early successes with agents sometimes begin to skip review steps. This is a pattern that leads to undetected errors accumulating in the codebase.

**Mitigation:** Maintain the habit of reviewing every change, even when it looks correct. Treat agent output as a first draft, not a finished product.

#### Reproducibility concerns

Agent-written code may:

- Rely on non-reproducible randomness
- Depend on specific environment configurations not recorded anywhere
- Use APIs or data sources that change over time
- Produce results that vary across runs due to non-determinism in the model

**Mitigation:** Document the agent-assisted workflow. Record software versions. Set random seeds. Test across environments.

#### Security and confidentiality

- Never give agents access to credentials, API keys, or sensitive personal or research data unless you are certain of the data handling policies.
- Oxford's ChatGPT Edu and Codex provision: your input data is not used for model training and is subject to the same security arrangements as Microsoft 365. Data residency is in the US.
- For agents running locally (Claude Code CLI, Codex CLI): your data is sent to Anthropic/OpenAI servers as part of the API call. Review the data handling policies of each provider.
- Be particularly careful with unpublished research data, patient data, commercial-in-confidence information, and anything that might be subject to export controls.

#### Cost runaway

An agent stuck in an error loop, or a routine running unexpectedly, can accumulate substantial costs without user awareness.

**Mitigation:**

- Set billing alerts in the API console
- Monitor usage dashboards
- For routines or scheduled tasks, set maximum execution limits
- Watch your first few agent sessions closely before allowing autonomous unsupervised operation

#### Governance and policy considerations

Research groups should consider:

- **Attribution and authorship:** If an agent wrote substantial portions of code in a published software package, how is this disclosed? Some journals and conference proceedings are beginning to require disclosure.
- **Code ownership and licensing:** Code generated by an AI tool may have unclear licensing status in some jurisdictions. Review your institution's policy.
- **Reproducibility obligations:** If your published results depend on agent-written code, is that code sufficiently documented and tested for others to reproduce?
- **Student training:** This cuts both ways. Students who rely on agents to *produce* code without understanding it may fail to develop core computational skills. However, agents can also be excellent **learning tools** — and not only for programming: for tutoring, explaining concepts interactively, walking through code line-by-line, generating worked examples, and answering "why does this work?" questions in real time. Researchers increasingly report learning *science* from agent dialogue — unfamiliar methods, the reasoning behind a derivation, the trade-offs between approaches — not just syntax. Research groups should think carefully about when agent use is pedagogically appropriate for production or assessment work, while actively encouraging its use as a learning and exploration tool.
- **Data handling policies:** Before using any cloud tool with research data, check whether the data can be sent off-site and what governance applies.

---

---

## Part 6 — Seminar Structure, Slides, and Discussion

### 6.1 Suggested slide structure

**Slide 1: Title**
Agent-Driven Software Development for Computational Geoscientists

**Slides 2–6: The conceptual shift (5–6 min)**

- Slide 2: Real-world impact — Anthropic's 80%/800 stat as an opening anchor
- Slide 3: The frontier is moving into the science — Knuth's "Claude's Cycles", Erdős #728 (with Tao's caveats), the GPT-5 science report, Mythos 5 hypothesis generation; verification stayed human in every case
- Slide 4: Chat → Agent: what changes? (diagram)
- Slide 5: What kinds of tasks benefit from agents? (decision framework table)
- Slide 6: The mental model: a capable collaborator — junior in your project, less junior in the science every release; you decide and verify

**Slides 5–10: The ecosystem (8 min)**

- Slide 5: Map of the landscape (diagram: tools positioned by autonomy, cost, integration)
- Slide 6: Oxford access — what you already have (ChatGPT Edu, Codex via OeRC AI Centre)
- Slide 7: Claude and Claude Code (pricing, key features, best for)
- Slide 8: GitHub Copilot and VS Code (pricing, key features)
- Slide 9: Cursor and Devin (pricing, key features)
- Slide 10: How to choose — a decision tree for researchers

**Slides 11–15: Practical workflows (8 min)**

- Slide 11: Before you start — scoping the task (the five questions)
- Slide 12: Providing context — CLAUDE.md, instruction files, domain context
- Slide 13: Context management — why it matters, strategies
- Slide 14: Working safely — always-on-a-branch, commit checkpoints, review the diff
- Slide 15: Verifying outputs — testing, comparison to reference, physical constraints

**Slides 16–19: Deep dives (7 min)**

- Slide 16: Claude Code — CLAUDE.md, planning mode, auto mode, parallel agents
- Slide 17: Codex — Skills, Automations, worktrees, GitHub integration
- Slide 18: Cost management — token consumption, model selection, usage patterns
- Slide 19: Cost comparison table: subscription vs. API vs. Oxford provision

**Slides 20–23: Failure modes and risks (7 min)**

- Slide 20: Scientific correctness — the hardest failure mode to detect
- Slide 21: Other failure modes — hallucination, dependency errors, repository damage
- Slide 22: Security and governance — what to check before using any tool
- Slide 23: Summary: when to use agents, when to be cautious

**Slide 24: Live demo introduction**

- Slide 25+: (Live demo — see below)

**Slide N: Discussion questions**

---

### 6.2 Suggested live demonstration

**Goal:** Illustrate good agent workflow, not impressive autonomous output. Demonstrate the *process*, not just the result.

**Recommended demonstration: building `d8demo` from a scaffold with staged, scoped prompts**

The demo builds `d8demo`, a tiny educational package for D8 flow routing and flow accumulation on synthetic DEMs, live from a clean scaffold. The point is the *workflow* — scoping, persistent context, plan-before-code, diff review, verification — not an impressive autonomous result. The prepared prompts live in `d8_prompts.md`.

**Setup (prepare in advance):**

- The `d8demo` repository, with the scaffolded starting point committed on `demo-start` (a LICENSE, a placeholder README, and a short repository description — no implementation).
- The staged prompts ready to paste, in `d8_prompts.md` (scaffold → source + tests → example → docs).
- The finished package on `demo-solution` as a safety net, in case the live run runs long or goes awry.
- Claude Code installed and authenticated; `uv` installed.

Brief the audience first with the two background slides (DEM, D8 routing, flow accumulation; the hand-checkable 3×3 valley) so they know what is being built.

**Demonstration script:**

You will not run all four stages in five minutes — branch `demo-live` off `demo-start`, then pick one or two stages that best show the workflow (the scaffold and source-and-tests prompts are the richest). For each prompt, narrate the workflow beats rather than the code.

0. **Branch** (15 sec): `git checkout demo-start && git checkout -b demo-live`. "We never let an agent work on `main` — and we have a finished solution on another branch as a fallback."

1. **Scaffold** (1 min): Paste the scaffold prompt. The agent sets up the `uv` package, minimal dependencies, a short README, and `CLAUDE.md` / `AGENTS.md`. Point out that persistent context (educational style, explicit NumPy, tests-first, scientific assumptions in docstrings, no new dependencies without asking) goes in *up front*.

2. **Source + tests** (1–2 min): Paste the source prompt. The agent first researches D8, asks clarifying questions, proposes a package design and tests, states its scientific assumptions, and proposes a plan — *before* writing code. Highlight this: scoping and plan-first are doing the work. Then it implements DEM generation, D8 routing, and flow accumulation with tiny deterministic tests.

3. **Review and run** (1 min): Show the `git diff`. Run `uv run pytest`. Tests pass. Ask: "But are these tests sufficient? Is the science right?" Point back to the hand-checkable cases from the background slide — that is how we validate, not by trusting green tests.

4. **(If time) Example / docs**: The remaining prompts add an end-to-end CLI example that plots DEM → directions → accumulation, and a short background note. Mention these exist rather than running them live.

5. **Debrief** (1 min): "Notice what we did: scoped each stage tightly, gave persistent context once, made the agent plan and state assumptions before coding, reviewed the diff, and ran the tests — then asked whether the science was right. The agent did the work; we kept the scientific judgement."

**Why this demonstration works:**

- Low risk: small synthetic package, no live internet, deterministic — and a finished `demo-solution` branch as a fallback
- Illustrates the *workflow* (scope → context → plan → review → verify), not just the output
- Naturally raises the discussion of scientific correctness, with hand-checkable cases as the answer
- Reproducible: same prompts, same results every time
- Honest: shows an agent doing genuinely useful work, but also where our judgement is required

---

### 6.3 Discussion questions

**For the plenary discussion (~20 min):**

**Opening questions (get people talking):**

1. "Has anyone here already used an agent tool — Claude Code, Copilot, Cursor, Codex — for actual research code? What happened?"
2. "What part of your current software development workflow do you find most tedious? Is that a candidate for agent assistance?"

**Conceptual questions:**
3. "How would you verify that agent-written numerical code is scientifically correct? What is your 'safety net'?"
4. "If a student in your group used Claude Code to write the data processing pipeline for their thesis chapter, what would you want to check before signing off?"

**Practical questions:**
5. "What would you put in a CLAUDE.md for your main research codebase right now? What does an agent need to know to work usefully on it?"
6. "For the work your group does — typical codebases, typical tasks — which of the tools we discussed seems most relevant? What would you try first?"

**Governance and policy:**
7. "What institutional policies apply to using these tools for research in your department? Does your group have an agreed position on this?"
8. "If you publish a software paper for a codebase that was significantly developed with agent assistance, how would you handle attribution and reproducibility?"

**Sceptical questions (important to ask):**
9. "When is agent-driven development *not* the right choice? Can you think of research tasks where you would actively avoid it?"
10. "What would have to be true for you to trust agent-written code in a published, peer-reviewed scientific result?"

---

### 6.4 Key takeaways (for closing the seminar)

1. **Agent-driven development is real and useful** — not hype, not magic, but a genuine productivity multiplier for well-scoped tasks with clear criteria.

2. **The shift is from answering questions to taking actions** — this creates both power and risk, and requires a more careful workflow.

3. **Agents are becoming scientific collaborators, not just coders** — they propose approaches, check derivations, catch errors you missed, and teach. Engage them with the science; keep the decisions and the verification yours.

4. **You already have access** — ChatGPT Edu and Codex are available to all Oxford staff and students via SSO, with training and guidance from the OeRC AI Competency Centre.

5. **The bottleneck shifts, but does not disappear** — agents accelerate implementation; the bottleneck moves to task definition, context provision, and scientific verification. These require your expertise.

6. **Scientific correctness is your responsibility** — agents can confidently produce plausible-looking errors, and review matters more, not less. But verification cuts both ways: an agent makes an excellent *second* scientific reviewer of your own work — never the only one.

7. **Start small and build trust** — try an agent on a low-stakes task (writing tests, generating boilerplate, explaining an inherited codebase). Build your intuition for its strengths and failure modes before using it on critical code.

8. **Use Git as your safety net** — branches, commits, diffs. This is non-negotiable.

---

---

## Appendix A — Further Reading and Resources

### Documentation and official guides

- Claude Code documentation: [code.claude.com/docs/en/overview](https://code.claude.com/docs/en/overview)
- Claude Code best practices: [code.claude.com/docs/en/best-practices](https://code.claude.com/docs/en/best-practices)
- Using CLAUDE.md files: [claude.com/blog/using-claude-md-files](https://claude.com/blog/using-claude-md-files)
- Introduction to agentic coding (Anthropic): [claude.com/blog/introduction-to-agentic-coding](https://claude.com/blog/introduction-to-agentic-coding)
- Codex best practices: [developers.openai.com/codex/learn/best-practices](https://developers.openai.com/codex/learn/best-practices)
- Codex quickstart: [developers.openai.com/codex/quickstart](https://developers.openai.com/codex/quickstart)
- GitHub Copilot docs: [docs.github.com/en/copilot](https://docs.github.com/en/copilot)

### Oxford-specific resources

- OeRC AI Competency Centre: [oerc.ox.ac.uk/ai-centre](https://oerc.ox.ac.uk/ai-centre)
- Getting started with AI for Coding guide: [oerc.ox.ac.uk/ai-centre/ai-guides/getting-started-with-ai-for-coding](https://oerc.ox.ac.uk/ai-centre/ai-guides/getting-started-with-ai-for-coding)
- Getting started with AI for Researchers: [oerc.ox.ac.uk/ai-centre/ai-guides/getting-started-with-ai-for-researchers](https://oerc.ox.ac.uk/ai-centre/ai-guides/getting-started-with-ai-for-researchers)
- ChatGPT Edu guide: [oerc.ox.ac.uk/ai-centre/generative-ai-tools/chatgpt-edu](https://oerc.ox.ac.uk/ai-centre/generative-ai-tools/chatgpt-edu)
- Codex at Oxford guide: [oerc.ox.ac.uk/ai-centre/generative-ai-tools/codex](https://oerc.ox.ac.uk/ai-centre/generative-ai-tools/codex)
- Getting Started with Codex (Canvas course): [canvas.ox.ac.uk/courses/289256](https://canvas.ox.ac.uk/courses/289256)
- AI Competency Centre contact: [aimlcompetencycentre@it.ox.ac.uk](mailto:aimlcompetencycentre@it.ox.ac.uk)

### Pricing and access (current as of June 2026 — always verify)

- Claude pricing: [claude.com/pricing](https://claude.com/pricing)
- OpenAI API pricing: [openai.com/api/pricing](https://openai.com/api/pricing)
- GitHub Copilot plans: [docs.github.com/en/copilot/get-started/plans](https://docs.github.com/en/copilot/get-started/plans)
- Cursor pricing: [cursor.com/pricing](https://cursor.com/pricing)
- Devin pricing: [devin.ai/pricing](https://devin.ai/pricing)

---

## Appendix B — Example CLAUDE.md for a Research Codebase

```markdown
# Project: PyAtmos — 1D atmospheric radiative-convective model

## What this project does
PyAtmos is a Python implementation of a 1D radiative-convective atmosphere model
for exoplanet climate research. The core is in `src/pyatmos/`. Data files are in
`data/` (not version-controlled; see README for sources). Tests are in `tests/`.

## Key conventions
- Python 3.11+; dependencies in `environment.yml` (conda) and `requirements.txt` (pip)
- Style: black formatting, isort imports, ruff linting
- Docstrings: NumPy style
- All physical quantities in SI units unless explicitly documented otherwise
- All functions operating on atmospheric profiles take `z` (altitude in metres) as first argument

## Testing
- Run tests with: `pytest tests/ -v`
- Test data (small fixtures) in `tests/data/`
- Before submitting any changes, ensure `pytest tests/ && ruff check src/` pass

## Scientific constraints you must respect
- Temperature profiles must satisfy the dry adiabatic lapse rate constraint in convective layers
- Optical depths must be positive; negative values indicate a bug
- Albedos must be in [0, 1]; emissivities in [0, 1]
- The surface boundary condition is T_surface > 0 (Kelvin)
- Do NOT modify `src/pyatmos/legacy_core.f90` — this is a reference implementation,
  not active code. Read-only.

## What you should NOT do
- Do not add new dependencies without updating both environment.yml and requirements.txt
- Do not use hard-coded file paths; use `pathlib.Path` relative to the project root
- Do not remove existing test functions; only add to the test suite
- Do not modify `data/` directory contents

## Workflow reminders
- Always work on a feature branch, not main
- Commit after each logical step
- Update CHANGELOG.md when making user-facing changes
```

---

## Appendix C — Pricing Summary Table (June 2026)

*Prices in USD unless noted. Always verify current pricing at source before making commitments. Pricing evolves rapidly.*

| Tool / Tier | Monthly cost | Includes | Notes |
|---|---|---|---|
| **Claude Free** | $0 | Limited usage; Sonnet | No Claude Code |
| **Claude Pro** | $17/mo (annual) / $20/mo | Claude Code; Sonnet & Opus | Good for occasional use |
| **Claude Max 5x** | $100/mo | 5× usage; all models | Recommended for regular coding use |
| **Claude Max 20x** | $200/mo | 20× usage; all models; priority | Power users |
| **Claude API — Haiku 4.5** | Pay per use | $0.80/$4 per M tok | Cheap, fast |
| **Claude API — Sonnet 4.6** | Pay per use | ~$3/$15 per M tok | General purpose |
| **Claude API — Opus 4.8** | Pay per use | $15/$75 per M tok | Most capable |
| **ChatGPT Edu (Oxford)** | Free | GPT-5.5 unlimited; weekly limits on Thinking/Codex | SSO; no training data use |
| **ChatGPT Plus** | £20/mo | GPT-5.5 Thinking; expanded Codex | UK pricing |
| **ChatGPT Pro** | From £89/mo | 5× or 20× usage; GPT-5.5 Pro; max Codex | UK pricing |
| **OpenAI API — GPT-5.4** | Pay per use | $2.50/$15 per M tok | Good general use |
| **OpenAI API — GPT-5.5** | Pay per use | $5/$30 per M tok | Flagship |
| **GitHub Copilot Free** | $0 | 2,000 completions/mo; limited chat | No cloud agent |
| **GitHub Copilot Pro** | $10/mo | Unlimited completions; cloud agent; $15 AI credits | New sign-ups paused (June 2026) |
| **GitHub Copilot Pro+** | $39/mo | Premium models; $70 AI credits; audit logs | New sign-ups paused |
| **GitHub Copilot Max** | $100/mo | $200 AI credits; priority models | Upgrade from existing only (June 2026) |
| **GitHub Copilot Business** | $19/seat/mo | Team management; pooled credits | New self-serve paused (June 2026) |
| **Cursor Hobby** | $0 | Limited agents; limited Tab | Good starting point |
| **Cursor Pro** | $20/mo | Full agent; frontier models; MCP | Most individual researchers |
| **Cursor Teams** | $40/user/mo | Team admin; Bugbot; shared context | Research groups |
| **Devin Free** | $0 | Light quota; limited models; unlimited Tab | Good starting point |
| **Devin Pro** | $20/mo | Frontier models; Devin Cloud; SWE 1.6 | Individual researchers |
| **Devin Max** | $200/mo | Higher quota | Power users |
| **Devin Teams** | $80/mo + $40/full user | Centralised; admin; unlimited Desktop | Teams |

---

*Document compiled June 2026. All pricing and feature information should be verified at source before presentation, as the ecosystem evolves rapidly. Oxford-specific information sourced from the OeRC AI Competency Centre website (oerc.ox.ac.uk/ai-centre).*
