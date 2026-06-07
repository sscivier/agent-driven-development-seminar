---
theme: seriph
title: Agent-Driven Software Development for Computational Geoscientists
info: |
  Seminar for computational geoscientists at the University of Oxford.
  Source material: seminar_notes.md.
layout: default
class: deck
colorSchema: light
transition: fade
duration: 35min
fonts:
  sans: Inter
  mono: JetBrains Mono
  weights: '400,500,600,700'
drawings:
  persist: false
---

<div class="eyebrow">Computational geoscience seminar</div>

# Agent-Driven Software Development for Computational Geoscientists

<div class="title-rule"></div>

<p class="subtitle">
Using coding agents as practical research-software collaborators —
without outsourcing the scientific judgement.
</p>

<div class="meta abs-bl ml-[4.2rem] mb-12">
University of Oxford · June 2026
</div>

<!--
Position this as a practical seminar for experienced scientific programmers:
what changes when the tool can read, edit, run, and iterate inside a real repository.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART ONE</div>
  <h1>The conceptual shift</h1>
  <div class="title-rule"></div>
  <p>What actually changes when an AI can take actions, not just give advice.</p>
</div>

---

<div class="eyebrow">Real-world impact</div>

# It is already happening in production

<div class="stats">
  <v-click>
    <div class="stat">
      <span class="num">&gt;80%</span>
      <span class="lbl">of code merged into Anthropic's own production codebase was authored by Claude (May 2026)</span>
    </div>
  </v-click>
  <v-click>
    <div class="stat">
      <span class="num">800+</span>
      <span class="lbl">autonomous fixes shipped for one persistent class of API errors (Apr 2026)</span>
    </div>
  </v-click>
  <v-click>
    <div class="stat">
      <span class="num">1,000×</span>
      <span class="lbl">error-rate reduction — work estimated at four years for a human developer</span>
    </div>
  </v-click>
</div>

<v-click>
  <p class="lead">Not about replacing programmers — about a shift in <span v-mark="{ at: 4, type: 'underline', color: '#C15F3C' }">what we can ask tools to do</span>.</p>
</v-click>

<!--
Use this as the impact anchor, then immediately reframe it as a workflow shift.
The four-years figure is about the cognitive load of holding code context, not raw typing.
-->

---

<div class="eyebrow">What actually changes</div>

# From chat to agent

<div class="cols cols-2">
  <v-click>
    <div class="block cool">
      <span class="tag">Chat assistance</span>
      <h3>You drive</h3>
      <ul>
        <li>You describe the problem</li>
        <li>You paste the relevant code</li>
        <li>You copy, run, and fix</li>
        <li>The AI gives advice</li>
      </ul>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Agent-driven work</span>
      <h3>The agent acts</h3>
      <ul>
        <li>Reads the repository</li>
        <li>Edits files directly</li>
        <li>Runs commands and tests</li>
        <li>Iterates toward a result</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <p class="lead">The unit of work moves from answering a question to <span v-mark="{ at: 3, type: 'underline', color: '#C15F3C' }">carrying out a task</span>.</p>
</v-click>

<!--
With chat, the human is the keyboard operator. With an agent, the model has tools
and takes actions inside the codebase. That is the whole shift.
-->

---

<div class="eyebrow">Decision framework</div>

# When do agents add value?

<div class="cols cols-2">
  <div class="block">
    <span class="tag">Good fit</span>
    <ul>
      <li>Well-defined but tedious work</li>
      <li>Boilerplate, tests, documentation</li>
      <li>Codebase exploration and mapping</li>
      <li>Cross-cutting refactors</li>
      <li>Scaffolding and Fortran/Matlab → Python ports</li>
    </ul>
  </div>
  <div class="block cool">
    <span class="tag">Poor fit</span>
    <ul>
      <li>Novel scientific decisions</li>
      <li>Outputs you cannot test objectively</li>
      <li>Vague, exploratory tasks</li>
      <li>Algorithms you cannot validate</li>
      <li>Work quicker to do than to brief</li>
    </ul>
  </div>
</div>

<p class="note">
<strong>Heuristic:</strong> if you could brief a skilled programmer who doesn't know your field, an agent can probably help. If it needs judgement only you hold, it cannot.
</p>

<!--
Keep the audience away from both extremes: agents are useful, but they replace
neither scientific judgement nor clear task definition.
-->

---

<div class="eyebrow">Mental model</div>

# A capable, junior collaborator

<div class="cols cols-3">
  <v-click>
    <div class="block">
      <span class="tag">Brief</span>
      <h3>Give the task shape</h3>
      <p>Deliverable, constraints, files, success criteria.</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Review</span>
      <h3>Treat output as a draft</h3>
      <p>Read the diff, run the tests, check the assumptions.</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Verify</span>
      <h3>Keep scientific judgement</h3>
      <p>Reference values, units, conservation, physical limits.</p>
    </div>
  </v-click>
</div>

<v-click>
  <p class="lead accent">Agents accelerate implementation. They cannot <span v-mark="{ at: 4, type: 'circle', color: '#C15F3C' }">certify scientific correctness</span>.</p>
</v-click>

<!--
This phrase — capable but junior collaborator — should carry through the workflow
and failure-mode sections.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART TWO</div>
  <h1>The ecosystem</h1>
  <div class="title-rule"></div>
  <p>Tools, pricing, and what Oxford researchers already have.</p>
</div>

---

<div class="eyebrow">The landscape</div>

# A spectrum of autonomy

<div class="spectrum">
  <div>
    <span class="tag">In-editor</span>
    <h3>Assistive</h3>
    <ul>
      <li>Copilot completions</li>
      <li>Inline chat</li>
      <li>VS Code agent mode</li>
    </ul>
  </div>
  <div>
    <span class="tag">Local repo agent</span>
    <h3>Reads · edits · tests</h3>
    <ul>
      <li>Claude Code</li>
      <li>Codex CLI / App</li>
    </ul>
  </div>
  <div>
    <span class="tag">Cloud / PR agent</span>
    <h3>Issue → pull request</h3>
    <ul>
      <li>Codex Cloud</li>
      <li>Copilot cloud agent</li>
    </ul>
  </div>
  <div>
    <span class="tag">High autonomy</span>
    <h3>Plans long tasks</h3>
    <ul>
      <li>Devin Desktop</li>
      <li>Concurrent sessions</li>
    </ul>
  </div>
</div>

<div class="axis">
  <span>Lower autonomy · you review more often</span>
  <span>Higher autonomy · higher review burden</span>
</div>

<!--
A map, not a ranking. Tools differ in where they run and how much autonomy they assume.
More autonomy buys leverage and demands more review discipline.
-->

---

<div class="eyebrow">Oxford access</div>

# What you already have

<div class="cols cols-3">
  <div class="block">
    <span class="tag">ChatGPT Edu</span>
    <h3>Free via SSO</h3>
    <ul>
      <li>All current Oxford staff & students</li>
      <li>Sign in at chatgpt.com with your ox.ac.uk address</li>
      <li>No training on your data by default</li>
    </ul>
  </div>
  <div class="block">
    <span class="tag">Codex</span>
    <h3>Consent forms required</h3>
    <ul>
      <li>Codex Local for App & CLI</li>
      <li>Codex Cloud for GitHub repos</li>
      <li>Counts against Edu weekly limits (~30/wk)</li>
    </ul>
  </div>
  <div class="block">
    <span class="tag">OeRC AI Centre</span>
    <h3>Training & guidance</h3>
    <ul>
      <li>AI-for-coding & research guides</li>
      <li>"Getting Started with Codex" course</li>
      <li>Workshops, events, community</li>
    </ul>
  </div>
</div>

<p class="note">
Practical start: <strong>ChatGPT Edu</strong> first; complete the <strong>Codex consent</strong> if you want a real coding agent through Oxford's provision.
</p>

<!--
Keep it concrete: SSO access, consent forms, OeRC support. Detailed URLs are in the
notes — don't make the slide URL-heavy.
-->

---

<div class="eyebrow">Claude Code · Anthropic</div>

# Local agent, strong codebase comprehension

<div class="cols cols-2">
  <div class="block">
    <span class="tag">Plans</span>
    <ul>
      <li>Pro — $17/mo annual ($20 monthly)</li>
      <li>Max 5× — $100/mo</li>
      <li>Max 20× — $200/mo</li>
    </ul>
  </div>
  <div class="block">
    <span class="tag">What it does</span>
    <ul>
      <li>Runs locally in the terminal</li>
      <li>Searches & edits across the repo</li>
      <li>Runs tests, build tools, Git</li>
    </ul>
  </div>
</div>

<p class="note">
Best fit: researchers doing substantial development who want a repository-aware local agent with rich project instructions via <strong>CLAUDE.md</strong>.
</p>

<!--
Don't overload with every tier. The pricing anchor plus why it's distinctive:
local execution, CLAUDE.md, large-codebase comprehension.
-->

---

<div class="eyebrow">GitHub Copilot · VS Code</div>

# The lowest-friction IDE path

<div class="cols cols-2">
  <div class="block">
    <span class="tag">Copilot</span>
    <ul>
      <li>Free tier: completions + limited chat</li>
      <li>Pro listed at $10/mo</li>
      <li>Multi-model backend; GitHub integration</li>
    </ul>
  </div>
  <div class="block">
    <span class="tag">VS Code agent mode</span>
    <ul>
      <li>Multi-step file edits</li>
      <li>Terminal access and MCP tools</li>
      <li>Instruction files for persistent context</li>
    </ul>
  </div>
</div>

<p class="note">
<strong>Note:</strong> new Copilot sign-ups (Pro, Pro+, Max, student) were <span v-mark="{ at: 1, type: 'highlight', color: 'rgba(193,95,60,0.18)' }">paused April–June 2026</span>. Existing plans can still upgrade.
</p>

<!--
The sign-up pause is a required content note. Frame Copilot as the easiest starting
point for VS Code users, noting availability may change.
-->

---

<div class="eyebrow">Agent IDEs</div>

# Cursor and Devin Desktop

<div class="cols cols-2">
  <div class="block">
    <span class="tag">Cursor</span>
    <h3>Polished VS Code fork</h3>
    <ul>
      <li>Hobby free tier; Pro at $20/mo</li>
      <li>Agent mode, cloud agents, Bugbot review</li>
      <li>Strong all-in-one IDE experience</li>
    </ul>
  </div>
  <div class="block">
    <span class="tag">Devin Desktop</span>
    <h3>Formerly Windsurf</h3>
    <ul>
      <li>Free light quota; Pro at $20/mo</li>
      <li>Highest autonomy of the tools here</li>
      <li>Issue → plan → code → test → PR</li>
    </ul>
  </div>
</div>

<p class="note">
Higher autonomy increases leverage <em>and</em> risk. Good Git workflow and review discipline matter more, not less.
</p>

<!--
Explicitly state the Windsurf → Devin Desktop rebrand. Cursor is the polished IDE route;
Devin is the high-autonomy route.
-->

---

<div class="eyebrow">Choosing a tool</div>

# Start from access, then fit the workflow

<ul class="steps">
  <v-click><li>Use Oxford provision first — ChatGPT Edu, then Codex after consent.</li></v-click>
  <v-click><li>Already in VS Code? Try Copilot agent mode or a Codex / Claude extension.</li></v-click>
  <v-click><li>Want deep local work? Claude Code or Codex CLI/App for repository-level tasks.</li></v-click>
  <v-click><li>Sustained heavy development? Consider Cursor or Devin when it justifies paid autonomy.</li></v-click>
</ul>

<p class="note">
The tool matters less than the workflow: <strong>scope tightly, work on branches, verify the output</strong>.
</p>

<!--
Transition into practical workflows. Don't let the tool comparison become the point;
bring the audience back to workflow discipline.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART THREE</div>
  <h1>Practical workflows</h1>
  <div class="title-rule"></div>
  <p>How to actually work with an agent — scope, context, safety, verification.</p>
</div>

---

<div class="eyebrow">Before you start</div>

# Scope the task

<div class="cols" style="grid-template-columns: 1.1fr 1fr; align-items: start;">

<ul class="steps">
  <li>What is the concrete deliverable?</li>
  <li>How will I know it worked?</li>
  <li>What does the agent need to know?</li>
  <li>What should it <em>not</em> do?</li>
  <li>Is this the right tool for this task?</li>
</ul>

```python
# A deliverable — an agent can act on this
def load_var(path: str, name: str) -> np.ma.MaskedArray:
    """Read `name` from a NetCDF file as a masked array."""
    ...

# Not a deliverable
#   "improve the data loading code"
```

</div>

<p class="note">
Vague tasks fail the way they fail with junior collaborators — just faster, and more confidently.
</p>

<!--
The five questions are the operational checklist. The code makes the deliverable vs.
non-deliverable distinction concrete.
-->

---
layout: two-cols-header
layoutClass: gap-10
---

<div class="eyebrow">Providing context</div>

# Make the brief unambiguous

::left::

<div class="cols" style="grid-template-columns: 1fr; gap: 1.3rem;">
  <div class="block">
    <span class="tag">Persistent</span>
    <p>Project instructions: <strong>CLAUDE.md</strong>, <strong>AGENTS.md</strong>, <strong>copilot-instructions.md</strong>.</p>
  </div>
  <div class="block">
    <span class="tag">Scientific</span>
    <p>What the code can't reveal: equations, expected ranges, numerical pitfalls, physical constraints.</p>
  </div>
  <div class="block">
    <span class="tag">Task</span>
    <p>Point to the code: <code>advect()</code> in <code>src/dynamics/advection.py</code> — not "the advection function".</p>
  </div>
</div>

::right::

<<< @/snippets/CLAUDE.example.md

<!--
Agents are good at repository context, poor at guessing domain constraints: divergence-free
velocity fields, positive tracers, CFL timestep limits. Persist that in the instruction file.
-->

---

<div class="eyebrow">Context management</div>

# Context is a budget

<div class="cols cols-3">
  <div class="block">
    <span class="tag">Cost</span>
    <p>Every token in and out is paid for.</p>
  </div>
  <div class="block">
    <span class="tag">Attention</span>
    <p>Long histories accumulate stale detail and degrade quality.</p>
  </div>
  <div class="block">
    <span class="tag">Strategy</span>
    <p>Chain compact, well-scoped tasks with clear endpoints.</p>
  </div>
</div>

<div class="flow">
  <span>Start fresh after a sub-task</span>
  <span class="arrow">·</span>
  <span><code>/compact</code> when long but useful</span>
  <span class="arrow">·</span>
  <span>Persist rules in instruction files</span>
  <span class="arrow">·</span>
  <span>Give paths, not full files</span>
</div>

<!--
Context windows are large, but cost and attention still matter. Normalise starting fresh
and compacting instead of dragging every session forward forever.
-->

---

<div class="eyebrow">Working safely</div>

# Git is the safety net

<v-click>
  <p class="lead">Treat the agent's output like a PR from a collaborator you respect but don't <span v-mark="{ at: 1, type: 'underline', color: '#C15F3C' }">yet fully trust</span>.</p>
</v-click>

```bash {1|2|3|4|all}
git checkout -b agent/feature-name   # never let an agent work on main
# the agent works and commits incrementally
git diff                             # review every change before accepting
pytest                               # or npm test, cargo test, ...
```

<p class="note">
Keep <strong>.gitignore</strong> current so credentials, data files, and build artefacts never become agent commits.
</p>

<!--
One of the most important practices. Commit checkpoints let you git checkout back to a
known-good state if a session goes wrong.
-->

---

<div class="eyebrow">Verifying outputs</div>

# Trust comes from checks, not confidence

<ul class="steps">
  <v-click><li><strong>Tests</strong> — ask for them alongside the implementation.</li></v-click>
  <v-click><li><strong>Reference</strong> — compare to analytical, slower, literature, or prior results.</li></v-click>
  <v-click><li><strong>Physics</strong> — conservation, positivity, boundaries, units.</li></v-click>
  <v-click><li><strong>Suite</strong> — run existing tests to catch shared-code regressions.</li></v-click>
  <v-click><li><strong>Read</strong> — read the code that enters your research software.</li></v-click>
</ul>

<v-click>
  <p class="lead accent">Agent-written numerical code is not accepted until it is validated.</p>
</v-click>

<!--
The bridge into failure modes. Verification is part of the task, not an optional extra step.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART FOUR</div>
  <h1>Deep dives</h1>
  <div class="title-rule"></div>
  <p>Claude Code and Codex — and the cost mechanics underneath.</p>
</div>

---

<div class="eyebrow">Claude Code in depth</div>

# Run it like a controlled session

<div class="cols cols-3">
  <div class="block">
    <span class="tag">Memory</span>
    <h3>CLAUDE.md</h3>
    <p>Purpose, conventions, tests, domain constraints, boundaries. <code>/init</code> to start.</p>
  </div>
  <div class="block">
    <span class="tag">Planning</span>
    <h3>Read first, edit later</h3>
    <p>Plan mode (<code>Shift+Tab</code>) for unclear, multi-file, or unfamiliar work.</p>
  </div>
  <div class="block">
    <span class="tag">Parallelism</span>
    <h3>Worktrees</h3>
    <p>Isolated branches for parallel sessions or alternative approaches.</p>
  </div>
</div>

<div class="flow">
  <span>Explore</span><span class="arrow">→</span>
  <span>Plan</span><span class="arrow">→</span>
  <span>Implement</span><span class="arrow">→</span>
  <span>Commit</span>
</div>

<p class="note">
Common mistake: letting a session run long without checkpoints, compaction, or scientific verification.
</p>

<!--
A workflow slide, not a feature list. /init for CLAUDE.md, Shift+Tab for plan mode,
/compact for long sessions, worktrees for parallel isolation.
-->

---

<div class="eyebrow">Codex in depth</div>

# A family of coding agents

<div class="cols cols-4 tight">
  <div class="block"><span class="tag">App</span><p>Visual workspace for parallel local tasks.</p></div>
  <div class="block"><span class="tag">CLI</span><p>Terminal-native and scriptable.</p></div>
  <div class="block"><span class="tag">Cloud</span><p>GitHub issue → pull request.</p></div>
  <div class="block"><span class="tag">Extension</span><p>Agent work without leaving the editor.</p></div>
</div>

<div class="flow">
  <span>Issue</span><span class="arrow">→</span>
  <span>Explore repo</span><span class="arrow">→</span>
  <span>Implement</span><span class="arrow">→</span>
  <span>Run tests</span><span class="arrow">→</span>
  <span>Open PR</span>
</div>

<p class="note">
At Oxford, Codex draws on the ChatGPT Edu weekly allowance — treat those tasks as scarce, and review every PR for the science.
</p>

<!--
Skills as modular capabilities, Automations for event-triggered behaviour, worktrees as the
safety mechanism for parallel tasks. Scientific PRs still need careful review.
-->

---

<div class="eyebrow">Cost mechanics</div>

# Agent cost is multiplicative

<div class="flow">
  <span>Read files</span><span class="arrow">→</span>
  <span>Reason & plan</span><span class="arrow">→</span>
  <span>Write code</span><span class="arrow">→</span>
  <span>Run commands</span><span class="arrow">→</span>
  <span>Read output</span><span class="arrow">→</span>
  <span>Correct mistakes</span>
</div>

<v-click>
  <p class="lead">A complex task on a medium codebase: <span v-mark="{ at: 1, type: 'box', color: '#C15F3C' }">100k–500k tokens</span> — roughly $5–$50 at Opus pricing.</p>
</v-click>

<p class="note">
Overspend usually comes from long context, mismatched models, redundant reads, runaway agents, or parallel agents without the benefit to match.
</p>

<!--
Each action creates new input and output tokens, so cost doesn't feel like one prompt.
On subscription plans, a few large tasks can exhaust the monthly allocation.
-->

---

<div class="eyebrow">Cost comparison</div>

# Choose the cheapest reliable mode

| Mode | Typical fit | Watch for |
|---|---|---|
| Oxford ChatGPT Edu | Learning, scoping, limited Codex tasks | ~30 Codex queries/week |
| Claude Pro / ChatGPT Plus | Occasional short coding sprints | Quota exhaustion on large repos |
| Claude Max / ChatGPT Pro | Regular agent-driven development | Soft limits, not hard caps |
| API billing | Automation, bulk, scripted work | Can spike without monitoring |

<p class="note">
Match the model to the task <em>before</em> starting · compact or clear long sessions · monitor usage and batch non-interactive work.
</p>

<!--
Intentionally coarse — exact prices are in the notes and move fast. The message: cheapest
reliable mode, don't retry the same bad prompt on a stronger model, monitor spend.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART FIVE</div>
  <h1>Failure modes &amp; risks</h1>
  <div class="title-rule"></div>
  <p>The sober assessment — starting with the one that matters most here.</p>
</div>

---

<div class="eyebrow">Failure mode #1</div>

# Scientific correctness

<p class="lead accent">The code runs. The tests pass. The result looks plausible. <span v-mark="{ at: 0, type: 'circle', color: '#C15F3C' }">The science is wrong.</span></p>

<div class="cols cols-4 tight">
  <div class="block"><span class="tag">Sign</span><p>Right magnitude, wrong direction.</p></div>
  <div class="block"><span class="tag">Units</span><p>Conversion error hidden by scale.</p></div>
  <div class="block"><span class="tag">Indexing</span><p>Boundary or staggering mistake.</p></div>
  <div class="block"><span class="tag">Physics</span><p>Missed conservation, positivity, CFL.</p></div>
</div>

<p class="note">
Never deploy agent-written numerical code without validation against reference values. For any algorithm of consequence, read it line by line.
</p>

<!--
The most important failure mode for this audience. The danger is not dramatic failure —
it is plausible, confident, executable wrongness.
-->

---

<div class="eyebrow">Other technical failure modes</div>

# Plausible, broken, or unreproducible

<div class="cols cols-2">
  <div class="block">
    <span class="tag">Hallucination</span>
    <p>Invented APIs, constants, papers, or claims about existing code.</p>
  </div>
  <div class="block">
    <span class="tag">Dependencies</span>
    <p>Packages that don't exist, don't match the API, or add risk.</p>
  </div>
  <div class="block">
    <span class="tag">Repository damage</span>
    <p>Deleted files, scope creep, sensitive data, unsafe Git operations.</p>
  </div>
  <div class="block">
    <span class="tag">Reproducibility</span>
    <p>Unrecorded environments, randomness, or shifting data sources.</p>
  </div>
</div>

<p class="note">
Run the code · check imports & dependencies · inspect <code>git status</code> and <code>git diff</code> · record versions and set seeds.
</p>

<!--
Concrete examples from the notes. Keep the mitigation practical and routine.
-->

---

<div class="eyebrow">Security · governance · training</div>

# Check the rules before the workflow

<div class="cols cols-3">
  <div class="block">
    <span class="tag">Data handling</span>
    <p>Credentials, unpublished data, patient or commercial data, export controls.</p>
  </div>
  <div class="block">
    <span class="tag">Disclosure</span>
    <p>Authorship, attribution, licensing, reproducibility obligations.</p>
  </div>
  <div class="block">
    <span class="tag">Students</span>
    <p>A risk to skill-building <em>and</em> an excellent learning tool — within assessment rules.</p>
  </div>
</div>

<p class="note">
Oxford ChatGPT Edu and Codex inputs are <strong>not used for model training</strong>; data residency is in the US.
</p>

<!--
Keep the student point nuanced: agents can weaken skill development if students don't
understand the output, but are excellent for tutoring, worked examples, and explanation.
-->

---

<div class="eyebrow">Takeaway</div>

# When to use agents

| Use | Be cautious | Don't skip |
|---|---|---|
| Well-scoped implementation | Scientific decisions | Reference checks |
| Tests, docs, scaffolding | Unverifiable outputs | Diff review |
| Repository exploration | Sensitive data | Dependency review |
| Mechanical multi-file changes | Long unsupervised runs | Scientific ownership |

<p class="lead accent">Agents accelerate implementation; researchers stay responsible for correctness.</p>

<!--
The summary reference before the optional demo: scope tightly, branch, verify, and keep
scientific judgement with the researcher.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART SIX</div>
  <h1>Live demo</h1>
  <div class="title-rule"></div>
  <p>Process, not spectacle.</p>
</div>

---

<div class="eyebrow">Live demo</div>

# A small model, a real workflow

<div class="block" style="margin-top: 1.6rem;">
  <span class="tag">Target</span>
  <p>A ~200-line scientific Python model — a 1D advection or heat-equation solver. It works, but has no tests.</p>
</div>

<ul class="steps">
  <li>Ask the agent to explain the codebase.</li>
  <li>Show CLAUDE.md — project instructions and a scientific constraint.</li>
  <li>Request a test plan <em>before</em> implementation.</li>
  <li>Implement, inspect the diff, run the tests.</li>
</ul>

<p class="lead accent">But are these tests sufficient?</p>

<!--
Low-risk, reproducible, honest. The debrief: the agent did useful work in 5 minutes, but
the researcher judged test sufficiency and the science. Highlight the gap between passing
tests and scientific validity.
-->

---
layout: center
class: takeaways
---

<div class="eyebrow">In closing</div>

# Six things to take away

<ul class="steps" style="max-width: 54rem;">
  <li>Agent-driven development is real and useful — for well-scoped tasks with clear criteria.</li>
  <li>The shift is from answering questions to taking actions.</li>
  <li>You already have access — ChatGPT Edu and Codex via SSO, with OeRC support.</li>
  <li>The bottleneck moves to task definition, context, and verification.</li>
  <li>Scientific correctness is your responsibility.</li>
  <li>Use Git as your safety net — branches, commits, diffs.</li>
</ul>

<!--
Bring the whole seminar together before discussion. Points curated from notes §6.4.
-->

---
layout: center
class: discussion
---

<div class="eyebrow">Over to you</div>

# Discussion

<div class="qlist">
  <div>
    <span class="tag">Warm-up</span>
    <p>Have you used an agent on real research code? What happened?</p>
  </div>
  <div>
    <span class="tag">Practical</span>
    <p>What's the most tedious part of your workflow — a candidate for an agent?</p>
  </div>
  <div>
    <span class="tag">Conceptual</span>
    <p>How would you verify that agent-written numerical code is scientifically correct?</p>
  </div>
  <div>
    <span class="tag">Governance</span>
    <p>What would you check before signing off a student's agent-written pipeline?</p>
  </div>
  <div>
    <span class="tag">Sceptical</span>
    <p>When is agent-driven development <em>not</em> the right choice?</p>
  </div>
  <div>
    <span class="tag">Sceptical</span>
    <p>What would make you trust agent-written code in a published result?</p>
  </div>
</div>

<!--
Questions curated from notes §6.3. Open with the warm-up to get people talking.
-->

---
class: disclosure
---

<div class="eyebrow">AI disclosure</div>

# How this talk was made

| Tool | How it was used |
| --- | --- |
| **Claude Code** — Claude Opus 4.8 | Slide design & build; content drafting & revision |
| **ChatGPT** — OpenAI (incl. web browsing) | Research, fact-checking, ideation & structure |
| **OpenAI Codex** — Oxford institutional access | Coding assistance |
| **GitHub Copilot** — in VS Code | In-editor code completion |

<p class="note">
AI generated substantial portions of the design and text. I directed and supervised the
work throughout — setting the framing and focus, iterating on research, plan and content,
and curating and verifying all outputs. I am responsible for the final content.
</p>

<p class="meta">
Disclosed following emerging norms for generative-AI use — ICMJE recommendations and the
AI Disclosure (AID) Framework.
</p>

<!--
Closing transparency slide — fitting for a talk about agent-driven development. Structure
follows the standard disclosure recipe: tools (product · model/service), roles, extent, and
a statement of human verification and responsibility.
-->
