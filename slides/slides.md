---
theme: seriph
title: Agent-Driven Software Development for Computational Geoscientists
info: |
  Seminar for computational geoscientists at the University of Oxford.
  Source material: seminar_notes.md.
layout: default
class: deck
drawings:
  persist: false
transition: fade
comark: true
duration: 35min
---

<div class="eyebrow">Computational geoscience seminar</div>

# Agent-Driven Software Development for Computational Geoscientists

<div class="title-rule"></div>

<p class="subtitle">
How to use coding agents as practical research software collaborators,
without outsourcing the scientific judgement.
</p>

<div class="abs-bl ml-17 mb-12 meta">
University of Oxford<br>
30-40 min seminar + discussion
</div>

<!--
Open by positioning this as a practical seminar for experienced scientific programmers:
what changes when the tool can read, edit, run, and iterate inside a real repository.
-->

---
layout: default
---

<div class="eyebrow">Real-world impact</div>

# 80% and 800

<div class="kicker-grid">
  <v-click>
    <div class="stat">
      <span class="stat-number">&gt;80%</span>
      <span class="stat-label">of code merged into Anthropic's production codebase was authored by Claude (05/26)</span>
    </div>
  </v-click>

  <v-click>
    <div class="stat">
      <span class="stat-number">800+</span>
      <span class="stat-label">autonomous fixes for a persistent class of API errors (04/26)</span>
    </div>
  </v-click>

  <v-click>
    <div class="stat">
      <span class="stat-number">1,000x</span>
      <span class="stat-label">error-rate reduction from cleanup estimated at four years of human work (04/26)</span>
    </div>
  </v-click>
</div>

<v-click>
  <div class="quiet-box">
    <p>This is not about replacing programmers. It is about a shift in what programmers can ask tools to do.</p>
  </div>
</v-click>

<div class="section-tag">1. Conceptual shift</div>
<div class="slide-no">2</div>

<!--
As of May 2026, Claude authored over 80% of the code merged into Anthropic's own
production codebase. In April 2026, Claude autonomously shipped over 800 fixes for
a persistent class of API errors, reducing the error rate by a factor of 1,000.
Use this as the impact anchor, then immediately frame it as a workflow shift.
-->

---
layout: default
---

<div class="eyebrow">What actually changes</div>

# From chat to agent

<div class="comparison">
  <v-click>
    <div class="column-card">
      <h2>Chat assistance</h2>
      <ul>
        <li>You describe a problem</li>
        <li>You paste the relevant code</li>
        <li>You copy, run, and fix</li>
        <li>The AI gives advice</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="column-card agent-card">
      <h2>Agent-driven work</h2>
      <ul>
        <li>Agent reads the repository</li>
        <li>Agent edits files directly</li>
        <li>Agent runs commands and tests</li>
        <li>Agent iterates toward a result</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <div class="quiet-box">
    <p>The unit of work moves from <strong>answering a question</strong> to <strong>carrying out a task</strong>.</p>
  </div>
</v-click>

<div class="section-tag">1. Conceptual shift</div>
<div class="slide-no">3</div>

<!--
Stress the operational difference: with chat, the human is the keyboard operator.
With an agent, the model has tools and can take actions inside the codebase.
-->

---
layout: default
---

<div class="eyebrow">Decision framework</div>

# When do agents add value?

<div class="fit-grid">
  <v-click>
    <div class="fit-list">
      <h2>Good fit</h2>
      <ul>
        <li>Well-defined but tedious work</li>
        <li>Boilerplate, tests, documentation</li>
        <li>Codebase exploration and mapping</li>
        <li>Cross-cutting refactors</li>
        <li>Project scaffolding and ports</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="fit-list caution">
      <h2>Poor fit</h2>
      <ul>
        <li>Novel scientific decisions</li>
        <li>Unverifiable outputs</li>
        <li>Vague exploratory tasks</li>
        <li>Algorithms you cannot validate</li>
        <li>Work where explanation takes longer than doing it</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <div class="heuristic">
    <p><strong>Heuristic:</strong> if you could brief a skilled programmer who does not know your field, an agent can probably help.</p>
  </div>
</v-click>

<div class="section-tag">1. Conceptual shift</div>
<div class="slide-no">4</div>

<!--
This slide should keep the audience away from both extremes: agents are useful, but
they are not a substitute for scientific judgement or for clear task definition.
-->

---
layout: default
---

<div class="eyebrow">Mental model</div>

# A capable junior collaborator

<div class="model-grid">
  <v-click>
    <div class="model-step">
      <span>Brief</span>
      <h2>Give the task shape</h2>
      <p>Deliverable, constraints, files, success criteria.</p>
    </div>
  </v-click>

  <v-click>
    <div class="model-step">
      <span>Review</span>
      <h2>Treat output as draft</h2>
      <p>Read the diff, run the tests, check the assumptions.</p>
    </div>
  </v-click>

  <v-click>
    <div class="model-step">
      <span>Verify</span>
      <h2>Own scientific judgement</h2>
      <p>Reference solutions, units, conservation, physical constraints.</p>
    </div>
  </v-click>
</div>

<v-click>
  <div class="warning-line">
    Agents can accelerate implementation. They cannot certify scientific correctness.
  </div>
</v-click>

<div class="section-tag">1. Conceptual shift</div>
<div class="slide-no">5</div>

<!--
End the first section with the core mental model from the notes. This phrase should
carry through the later workflow and failure-mode sections.
-->

---
layout: default
---

<div class="eyebrow">Ecosystem</div>

# Four ways agents show up

<div class="tool-grid">
  <v-click>
    <div class="tool-card blue">
      <span>In-editor agent</span>
      <h2>Works where you code</h2>
      <ul>
        <li>Copilot agent mode</li>
        <li>Cursor</li>
        <li>Codex / Claude extensions</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="tool-card sage">
      <span>Local repo agent</span>
      <h2>Reads, edits, tests locally</h2>
      <ul>
        <li>Claude Code</li>
        <li>Codex CLI</li>
        <li>Codex App worktrees</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="tool-card gold">
      <span>Cloud PR agent</span>
      <h2>Delegated issue to PR</h2>
      <ul>
        <li>Codex Cloud</li>
        <li>Copilot cloud agent</li>
        <li>GitHub-assigned agents</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="tool-card accent">
      <span>High-autonomy agent</span>
      <h2>Plans and executes longer tasks</h2>
      <ul>
        <li>Devin Desktop</li>
        <li>Concurrent sessions</li>
        <li>Higher review burden</li>
      </ul>
    </div>
  </v-click>
</div>

<div class="section-tag">2. Ecosystem</div>
<div class="slide-no">6</div>

<!--
Use this as a workflow map, not a ranking. The key point is that agent tools differ
in where they run and how much autonomy they assume.
-->

---
layout: default
---

<div class="eyebrow">Oxford access</div>

# What Oxford researchers already have

<div class="access-grid">
  <v-click>
    <div class="access-card">
      <span>ChatGPT Edu</span>
      <h2>Free via SSO</h2>
      <ul>
        <li>Available to current Oxford staff and students</li>
        <li>Use your Oxford email at chatgpt.com</li>
        <li>No training on your data by default</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="access-card">
      <span>Codex</span>
      <h2>Consent forms required</h2>
      <ul>
        <li>Codex Local for App and CLI</li>
        <li>Codex Cloud for GitHub repositories</li>
        <li>Counts against ChatGPT Edu weekly limits</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="access-card">
      <span>OeRC AI Centre</span>
      <h2>Training and guidance</h2>
      <ul>
        <li>AI coding and research guides</li>
        <li>Getting Started with Codex course</li>
        <li>Workshops, events, and community</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>Practical start: ChatGPT Edu first; complete Codex consent if you want a real coding agent.</p>
  </div>
</v-click>

<div class="section-tag">2. Ecosystem</div>
<div class="slide-no">7</div>

<!--
Keep this concrete for Oxford: SSO access, consent forms, and OeRC support.
The detailed URLs are in the notes; do not make the slide URL-heavy.
-->

---
layout: default
---

<div class="eyebrow">Claude and Claude Code</div>

# Local agent, strong codebase comprehension

<div class="tool-grid">
  <v-click>
    <div class="tool-card accent">
      <span>Plans</span>
      <h2>Pro to Max</h2>
      <ul>
        <li>Pro: $17 annual / $20 monthly</li>
        <li>Max 5x: $100 monthly</li>
        <li>Max 20x: $200 monthly</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="tool-card sage">
      <span>What it does</span>
      <h2>Reads, edits, runs</h2>
      <ul>
        <li>Works locally in the terminal</li>
        <li>Searches and edits across the repository</li>
        <li>Runs tests, build tools, and Git commands</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>Best fit: researchers doing substantial development who want a repository-aware local agent with strong project instructions via <strong>CLAUDE.md</strong>.</p>
  </div>
</v-click>

<div class="section-tag">2. Ecosystem</div>
<div class="slide-no">8</div>

<!--
Do not overload with every tier. Mention the pricing anchor and why Claude Code is
distinctive: local execution, CLAUDE.md, large-codebase comprehension.
-->

---
layout: default
---

<div class="eyebrow">GitHub Copilot and VS Code</div>

# Lowest-friction IDE path

<div class="tool-grid">
  <v-click>
    <div class="tool-card blue">
      <span>Copilot</span>
      <h2>Embedded in the editor</h2>
      <ul>
        <li>Free tier for completions and limited chat</li>
        <li>Pro listed at $10 monthly</li>
        <li>Multi-model backend and GitHub integration</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="tool-card sage">
      <span>VS Code agent mode</span>
      <h2>More than autocomplete</h2>
      <ul>
        <li>Multi-step file edits</li>
        <li>Terminal access and MCP tools</li>
        <li>Instruction files for persistent context</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p><strong>Important:</strong> new Copilot sign-ups for Pro, Pro+, Max, and student plans were paused April-June 2026.</p>
  </div>
</v-click>

<div class="section-tag">2. Ecosystem</div>
<div class="slide-no">9</div>

<!--
The sign-up pause is a required content note. Frame Copilot as the easiest starting
point for VS Code users, while noting that availability may change.
-->

---
layout: default
---

<div class="eyebrow">Agent IDEs</div>

# Cursor and Devin Desktop

<div class="tool-grid">
  <v-click>
    <div class="tool-card gold">
      <span>Cursor</span>
      <h2>Polished VS Code fork</h2>
      <ul>
        <li>Hobby free tier; Pro at $20 monthly</li>
        <li>Agent mode, cloud agents, Bugbot review</li>
        <li>Strong all-in-one IDE experience</li>
      </ul>
    </div>
  </v-click>

  <v-click>
    <div class="tool-card accent">
      <span>Devin Desktop</span>
      <h2>Formerly Windsurf</h2>
      <ul>
        <li>Free light quota; Pro at $20 monthly</li>
        <li>Highest autonomy among tools discussed</li>
        <li>Issue to plan, code, test, and PR workflow</li>
      </ul>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>Higher autonomy increases leverage and risk. Good Git workflow and review discipline matter more, not less.</p>
  </div>
</v-click>

<div class="section-tag">2. Ecosystem</div>
<div class="slide-no">10</div>

<!--
Explicitly mention Windsurf to Devin Desktop. Keep this slide comparative: Cursor
is the polished IDE route; Devin is the high-autonomy route.
-->

---
layout: default
---

<div class="eyebrow">Choosing a tool</div>

# Start from access, then fit the workflow

<div class="decision-flow">
  <v-click>
    <div class="decision-step">
      <span>1</span>
      <h2>Oxford provision?</h2>
      <p>Start with ChatGPT Edu. Use Codex after consent.</p>
    </div>
  </v-click>

  <v-click>
    <div class="decision-step">
      <span>2</span>
      <h2>Already in VS Code?</h2>
      <p>Try Copilot agent mode or a Codex / Claude extension.</p>
    </div>
  </v-click>

  <v-click>
    <div class="decision-step">
      <span>3</span>
      <h2>Want deep local work?</h2>
      <p>Claude Code or Codex CLI/App for repository-level tasks.</p>
    </div>
  </v-click>

  <v-click>
    <div class="decision-step">
      <span>4</span>
      <h2>Sustained heavy dev?</h2>
      <p>Consider Cursor or Devin when the workflow justifies paid autonomy.</p>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>The tool choice matters less than the workflow: scope tightly, work on branches, verify the output.</p>
  </div>
</v-click>

<div class="section-tag">2. Ecosystem</div>
<div class="slide-no">11</div>

<!--
This is the transition into practical workflows. Do not let the tool comparison
become the point of the seminar; bring the audience back to workflow discipline.
-->

---
layout: default
---

<div class="eyebrow">Practical workflows</div>

# Before you start: scope the task

<div class="scope-list">
  <v-click>
    <div class="scope-item">
      <span>01</span>
      <p>What is the concrete deliverable?</p>
    </div>
  </v-click>

  <v-click>
    <div class="scope-item">
      <span>02</span>
      <p>How will I know if it worked?</p>
    </div>
  </v-click>

  <v-click>
    <div class="scope-item">
      <span>03</span>
      <p>What does the agent need to know?</p>
    </div>
  </v-click>

  <v-click>
    <div class="scope-item">
      <span>04</span>
      <p>What should it not do?</p>
    </div>
  </v-click>

  <v-click>
    <div class="scope-item">
      <span>05</span>
      <p>Is this the right tool for this task?</p>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>Vague tasks fail the same way they fail with junior collaborators, just faster and more confidently.</p>
  </div>
</v-click>

<div class="section-tag">3. Practical workflows</div>
<div class="slide-no">12</div>

<!--
Keep the five questions as the operational checklist. Give one concrete example:
"a function that reads a NetCDF file and returns a masked numpy array" is a
deliverable; "improve the data loading code" is not.
-->

---
layout: default
---

<div class="eyebrow">Providing context</div>

# Make the brief unambiguous

<div class="brief-grid">
  <v-click>
    <div class="brief-card accent">
      <span>Persistent context</span>
      <h2>Project instructions</h2>
      <p><strong>CLAUDE.md</strong>, <strong>AGENTS.md</strong>, or <strong>.github/copilot-instructions.md</strong></p>
    </div>
  </v-click>

  <v-click>
    <div class="brief-card sage">
      <span>Scientific context</span>
      <h2>What code cannot infer</h2>
      <p>Equations, expected ranges, numerical pitfalls, physical constraints.</p>
    </div>
  </v-click>

  <v-click>
    <div class="brief-card blue">
      <span>Task context</span>
      <h2>Point to the code</h2>
      <p>Use file paths and function names, not vague descriptions.</p>
    </div>
  </v-click>
</div>

<v-click>
  <div class="prompt-example">
    <p>Work on <strong>src/dynamics/advection.py::advect()</strong>. Preserve the public API. Add tests for mass conservation and boundary behaviour.</p>
  </div>
</v-click>

<div class="section-tag">3. Practical workflows</div>
<div class="slide-no">13</div>

<!--
Emphasise that agents are good at repository context but poor at guessing domain
constraints. Mention examples from the notes: divergence-free velocity fields,
positive tracer values, and CFL-style timestep constraints.
-->

---
layout: default
---

<div class="eyebrow">Context management</div>

# Context is a budget

<div class="context-grid">
  <v-click>
    <div class="context-card">
      <span>Cost</span>
      <p>Every token in and out is paid for.</p>
    </div>
  </v-click>

  <v-click>
    <div class="context-card">
      <span>Attention</span>
      <p>Long histories accumulate stale detail.</p>
    </div>
  </v-click>

  <v-click>
    <div class="context-card">
      <span>Strategy</span>
      <p>Use compact tasks with clear endpoints.</p>
    </div>
  </v-click>
</div>

<div class="context-actions">
  <v-click>
    <div>Start fresh after a completed sub-task</div>
  </v-click>
  <v-click>
    <div>Use <strong>/compact</strong> when the session is useful but long</div>
  </v-click>
  <v-click>
    <div>Store persistent rules in instruction files</div>
  </v-click>
  <v-click>
    <div>Give paths; do not paste full large files</div>
  </v-click>
</div>

<div class="section-tag">3. Practical workflows</div>
<div class="slide-no">14</div>

<!--
The message is not that context windows are small; they are large, but cost and
attention still matter. Use this slide to normalise starting fresh and compacting
instead of dragging every session forward forever.
-->

---
layout: default
---

<div class="eyebrow">Working safely</div>

# Git is the safety net

<div class="git-flow">
  <v-click><div><span>1</span><p>Create a branch</p></div></v-click>
  <v-click><div><span>2</span><p>Let the agent work</p></div></v-click>
  <v-click><div><span>3</span><p>Commit checkpoints</p></div></v-click>
  <v-click><div><span>4</span><p>Review the diff</p></div></v-click>
  <v-click><div><span>5</span><p>Run tests, then merge or PR</p></div></v-click>
</div>

<v-click>

<pre class="safe-workflow"><code>git checkout -b agent/feature-name
# agent works and commits incrementally
git diff
npm test  # or pytest, cargo test, ...</code></pre>

</v-click>

<v-click>
  <div class="note-strip">
    <p>Keep <strong>.gitignore</strong> current so credentials, data files, and build artefacts do not become agent commits.</p>
  </div>
</v-click>

<div class="section-tag">3. Practical workflows</div>
<div class="slide-no">15</div>

<!--
Frame this as one of the most important practices. The agent's output should be
treated like a pull request from a collaborator you respect but do not fully trust.
-->

---
layout: default
---

<div class="eyebrow">Verifying outputs</div>

# Trust comes from checks, not confidence

<div class="verify-ladder">
  <v-click>
    <div class="verify-step"><span>Tests</span><p>Ask for tests alongside implementation.</p></div>
  </v-click>

  <v-click>
    <div class="verify-step"><span>Reference</span><p>Compare to analytical, slower, literature, or previous results.</p></div>
  </v-click>

  <v-click>
    <div class="verify-step"><span>Physics</span><p>Check conservation, positivity, boundaries, units.</p></div>
  </v-click>

  <v-click>
    <div class="verify-step"><span>Suite</span><p>Run existing tests for shared-code regressions.</p></div>
  </v-click>

  <v-click>
    <div class="verify-step"><span>Read</span><p>Read the code that enters your research software.</p></div>
  </v-click>
</div>

<v-click>
  <div class="warning-line compact">
    Agent-written numerical code is not accepted until it is validated.
  </div>
</v-click>

<div class="section-tag">3. Practical workflows</div>
<div class="slide-no">16</div>

<!--
This is the bridge into the later failure-mode section. Scientific correctness
gets a dedicated slide later, but this workflow section should already establish
that verification is part of the task, not a separate optional step.
-->

---
layout: default
---

<div class="eyebrow">Claude Code in depth</div>

# Use it like a controlled coding session

<div class="deep-grid">
  <v-click>
    <div class="deep-card accent">
      <span>Memory</span>
      <h2>CLAUDE.md</h2>
      <p>Purpose, conventions, tests, domain constraints, and boundaries.</p>
    </div>
  </v-click>

  <v-click>
    <div class="deep-card sage">
      <span>Planning</span>
      <h2>Read first, edit later</h2>
      <p>Use plan mode for unclear, multi-file, or unfamiliar work.</p>
    </div>
  </v-click>

  <v-click>
    <div class="deep-card blue">
      <span>Parallelism</span>
      <h2>Worktrees</h2>
      <p>Independent branches for parallel sessions or alternative approaches.</p>
    </div>
  </v-click>
</div>

<v-click>
  <div class="phase-strip">
    <div>Explore</div>
    <div>Plan</div>
    <div>Implement</div>
    <div>Commit</div>
  </div>
</v-click>

<v-click>
  <div class="note-strip">
    <p>Common mistake: letting the session run too long without checkpoints, compaction, or scientific verification.</p>
  </div>
</v-click>

<div class="section-tag">4. Deep dives</div>
<div class="slide-no">17</div>

<!--
This is a Claude Code workflow slide, not another feature list. Mention /init for
CLAUDE.md, Shift+Tab for plan mode, Ctrl+G for editing a plan, /compact for long
sessions, and worktrees for parallel isolation.
-->

---
layout: default
---

<div class="eyebrow">Codex in depth</div>

# A family of coding agents

<div class="codex-map">
  <v-click>
    <div class="codex-surface app"><span>App</span><p>Visual workspace for parallel local tasks.</p></div>
  </v-click>
  <v-click>
    <div class="codex-surface cli"><span>CLI</span><p>Terminal-native and scriptable.</p></div>
  </v-click>
  <v-click>
    <div class="codex-surface cloud"><span>Cloud</span><p>GitHub issue to pull request.</p></div>
  </v-click>
  <v-click>
    <div class="codex-surface ide"><span>Extension</span><p>Agent work without leaving the editor.</p></div>
  </v-click>
</div>

<div class="codex-workflow">
  <v-click><div>Issue</div></v-click>
  <v-click><div>Explore repo</div></v-click>
  <v-click><div>Implement</div></v-click>
  <v-click><div>Run tests</div></v-click>
  <v-click><div>Open PR</div></v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>At Oxford, Codex uses the ChatGPT Edu weekly allowance; treat those tasks as scarce and review PRs carefully.</p>
  </div>
</v-click>

<div class="section-tag">4. Deep dives</div>
<div class="slide-no">18</div>

<!--
Mention Codex Skills as modular project-specific capabilities, Automations for
event-triggered behaviour, and worktrees as the safety mechanism for parallel
tasks. For scientific issues, the PR still needs careful review.
-->

---
layout: default
---

<div class="eyebrow">Cost mechanics</div>

# Agent cost is multiplicative

<div class="token-loop">
  <v-click><div><span>1</span><p>Read files</p></div></v-click>
  <v-click><div><span>2</span><p>Reason and plan</p></div></v-click>
  <v-click><div><span>3</span><p>Write code</p></div></v-click>
  <v-click><div><span>4</span><p>Run commands</p></div></v-click>
  <v-click><div><span>5</span><p>Read output</p></div></v-click>
  <v-click><div><span>6</span><p>Correct mistakes</p></div></v-click>
</div>

<v-click>
  <div class="cost-callout">
    <span>100k-500k tokens</span>
    <p>A complex task on a medium-sized codebase can land in this range.</p>
  </div>
</v-click>

<v-click>
  <div class="note-strip">
    <p>Overspend usually comes from long context, mismatched models, redundant reads, runaway agents, or parallel agents without enough benefit.</p>
  </div>
</v-click>

<div class="section-tag">4. Deep dives</div>
<div class="slide-no">19</div>

<!--
Use this to explain why agent costs do not feel like one prompt. Each action can
create new input and output tokens. Mention that Opus 4.8 API pricing makes a
single complex task plausibly $5-$50 in the notes' example.
-->

---
layout: default
---

<div class="eyebrow">Cost comparison</div>

# Choose the cheapest reliable mode

<div class="cost-table">
  <div class="head">Mode</div>
  <div class="head">Typical fit</div>
  <div class="head">Watch for</div>

  <v-click>
    <div>Oxford ChatGPT Edu</div>
    <div>Learning, scoping, limited Codex tasks</div>
    <div>~30 Codex queries/week</div>
  </v-click>

  <v-click>
    <div>Claude Pro / ChatGPT Plus</div>
    <div>Occasional short coding sprints</div>
    <div>Quota exhaustion on large repos</div>
  </v-click>

  <v-click>
    <div>Claude Max / ChatGPT Pro</div>
    <div>Regular agent-driven development</div>
    <div>Soft limits, not hard caps</div>
  </v-click>

  <v-click>
    <div>API billing</div>
    <div>Automation, bulk, scripted workloads</div>
    <div>Can spike without monitoring</div>
  </v-click>
</div>

<v-click>
  <div class="cost-rules">
    <div>Match model to task before starting</div>
    <div>Compact or clear long sessions</div>
    <div>Monitor usage; batch non-interactive work</div>
  </div>
</v-click>

<div class="section-tag">4. Deep dives</div>
<div class="slide-no">20</div>

<!--
Keep this table intentionally coarse. The exact price list is in the notes and
changes quickly. The actionable message is to choose the cheapest reliable mode,
avoid retrying the same bad prompt on stronger models, and monitor spend.
-->

---
layout: default
---

<div class="eyebrow">Failure mode #1</div>

# Scientific correctness

<v-click>
  <div class="science-risk">
    <p>The code runs. The tests pass. The result looks plausible. The science is wrong.</p>
  </div>
</v-click>

<div class="risk-grid">
  <v-click><div><span>Sign</span><p>Wrong direction, right magnitude.</p></div></v-click>
  <v-click><div><span>Units</span><p>Conversion error hidden by scale.</p></div></v-click>
  <v-click><div><span>Indexing</span><p>Boundary or staggering mistake.</p></div></v-click>
  <v-click><div><span>Physics</span><p>Missed conservation, positivity, or CFL constraints.</p></div></v-click>
</div>

<v-click>
  <div class="warning-line compact">
    Never deploy agent-written numerical code without validation against reference values.
  </div>
</v-click>

<div class="section-tag">5. Failure modes and risks</div>
<div class="slide-no">21</div>

<!--
This is the most important failure mode for the audience. Explain that the danger
is not dramatic failure; it is plausible, confident, executable wrongness. The
mitigation from the notes: test against known solutions and read consequential
algorithms line by line.
-->

---
layout: default
---

<div class="eyebrow">Other technical failure modes</div>

# Plausible, broken, or unreproducible

<div class="failure-stack">
  <v-click>
    <div class="failure-row"><span>Hallucination</span><p>Invented APIs, constants, papers, or claims about existing code.</p></div>
  </v-click>

  <v-click>
    <div class="failure-row"><span>Dependencies</span><p>Packages that do not exist, do not match the API, or add risk.</p></div>
  </v-click>

  <v-click>
    <div class="failure-row"><span>Repository damage</span><p>Deleted files, scope creep, sensitive data, or unsafe Git operations.</p></div>
  </v-click>

  <v-click>
    <div class="failure-row"><span>Reproducibility</span><p>Unrecorded environment assumptions, randomness, or changing data sources.</p></div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>Run the code, check imports and dependencies, inspect <strong>git status</strong> and <strong>git diff</strong>, and record versions.</p>
  </div>
</v-click>

<div class="section-tag">5. Failure modes and risks</div>
<div class="slide-no">22</div>

<!--
Use concrete examples from the notes. Agents can invent APIs, suggest problematic
dependencies, modify files outside scope, or create code that only works in one
environment. Keep the mitigation practical.
-->

---
layout: default
---

<div class="eyebrow">Security, governance, training</div>

# Check the rules before the workflow

<div class="governance-grid">
  <v-click>
    <div class="governance-card accent">
      <span>Data handling</span>
      <p>Credentials, unpublished data, patient data, commercial data, export controls.</p>
    </div>
  </v-click>

  <v-click>
    <div class="governance-card sage">
      <span>Disclosure</span>
      <p>Authorship, attribution, licensing, and reproducibility obligations.</p>
    </div>
  </v-click>

  <v-click>
    <div class="governance-card blue">
      <span>Students</span>
      <p>Check official university guidance; use as a learning tool within assessment rules.</p>
    </div>
  </v-click>
</div>

<v-click>
  <div class="note-strip">
    <p>Oxford ChatGPT Edu and Codex inputs are not used for model training; data residency is in the US.</p>
  </div>
</v-click>

<div class="section-tag">5. Failure modes and risks</div>
<div class="slide-no">23</div>

<!--
Keep the student point nuanced: agents can weaken skill development if they produce
code students do not understand, but can be excellent learning tools for tutoring,
worked examples, and line-by-line explanation.
-->

---
layout: default
---

<div class="eyebrow">Takeaway</div>

# When to use agents

<div class="use-table">
  <div class="head">Use</div>
  <div class="head">Be cautious</div>
  <div class="head">Do not skip</div>

  <v-click>
    <div>Well-scoped implementation</div>
    <div>Scientific decisions</div>
    <div>Reference checks</div>
  </v-click>

  <v-click>
    <div>Tests, docs, scaffolding</div>
    <div>Unverifiable outputs</div>
    <div>Diff review</div>
  </v-click>

  <v-click>
    <div>Repository exploration</div>
    <div>Sensitive data</div>
    <div>Dependency review</div>
  </v-click>

  <v-click>
    <div>Mechanical multi-file changes</div>
    <div>Long unsupervised runs</div>
    <div>Scientific ownership</div>
  </v-click>
</div>

<v-click>
  <div class="summary-line">
    Agents accelerate implementation; researchers remain responsible for correctness.
  </div>
</v-click>

<div class="section-tag">5. Failure modes and risks</div>
<div class="slide-no">24</div>

<!--
Use this as the summary reference before moving into the optional live demo. It
should bring together the whole seminar: scope tightly, branch, verify, and keep
scientific judgement with the researcher.
-->
