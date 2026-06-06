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
