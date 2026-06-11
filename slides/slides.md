---
theme: seriph
title: Agent-Driven Software Development for Computational Geoscientists
info: |
  Seminar for computational geoscientists at the University of Oxford.
  Source material: docs/seminar_notes.md.
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
Using coding agents as practical research collaborators —
without outsourcing the scientific judgement.
</p>

<div class="meta abs-bl ml-[4.2rem] mb-12">
University of Oxford · June 2026
</div>

<!--
**Title · 0:00.**

Thanks everyone. I'd like to talk about a shift that's already changing how research software gets written — coding agents: AI that doesn't just answer
questions about code, but actually reads, edits, runs, and iterates inside a real
repository.

My aim is for this to be practical for people who already write scientific code. By the end I want you to know what these tools are,
which to reach for, and how to drive them safely.
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

<!--
**Part 1 · through ~6:00.**

Let's start with what's actually new here — the key aspect that's changed even over the past few months.
-->

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
I want to start with a number, because this is not a distant prospect — it's already
happening in production at the places building these tools.

As of May this year, Claude authored over 80% of the code merged into Anthropic's own
production codebase. And to make that concrete: in one case in April, the agent
autonomously shipped over 800 fixes for a single persistent class of API errors, and
cut the error rate by a factor of a thousand. The engineer who looked at it estimated
that same cleanup would have taken a human developer about four years.

I'm not telling you this to say programmers are going away. I'm telling you because it
reframes what we can ask a tool to do.
-->

---

<div class="eyebrow">The frontier is moving</div>

# Not just the code — the science

<div class="cols cols-2">
  <v-click>
    <div class="block">
      <span class="tag">Graph theory</span>
      <p><strong>"Claude's Cycles"</strong> — Donald Knuth published after Claude solved a graph-theory conjecture he'd worked on for decades (Mar 2026).</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Mathematics</span>
      <p><strong>Erdős #728</strong> — solved "more or less autonomously" (Tao, Jan 2026). His caveat: speed, not depth — ~1–2% of open problems in reach.</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Across the sciences</span>
      <p><strong>"A fast reasoning partner"</strong> — OpenAI's GPT-5 science report: credited ideas in maths, physics, biology; every step human-verified.</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Hypotheses</span>
      <p><strong>Preferred 4 times in 5</strong> — blinded comparison of Claude Mythos 5's molecular-biology hypotheses; one mechanism independently validated (Jun 2026).</p>
    </div>
  </v-click>
</div>

<v-click>
  <p class="lead">The pattern in every case: <span v-mark="{ at: 5, type: 'underline', color: '#C15F3C' }">AI proposes — humans verify and decide</span>.</p>
</v-click>

<!--
And just in the last six months, the story has moved beyond the code into the science
itself.

In March, Donald Knuth published a paper after Claude solved an open
graph-theory conjecture he'd worked on for decades. The model spotted the underlying
structure, a Cayley digraph, in about an hour. In January, Terence Tao reported an open
Erdős problem was solved more or less autonomously — and his caveats are worth keeping: it says
more about speed than depth, and he reckons only one or two percent of open Erdős problems
are within reach of today's AI without serious human involvement.

OpenAI published a whole report of early science experiments, where the researchers' own framing was a "fast reasoning partner",
with every step independently verified. And just this month, in blinded comparisons,
scientists preferred Claude Mythos 5's molecular-biology hypotheses about four times in
five, and one proposed mechanism has since been validated experimentally.

And this isn't slowing down — Anthropic released Fable 5 just this week, a Mythos-class
model in general availability, pitched explicitly on its science gains.

I'll add my own experience: these models now routinely catch scientific and mathematical
errors in my work that I hadn't caught — and I learn science from them, not just syntax.
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
Most of you have met AI coding as chat: you describe a problem, it suggests some code, you
copy it, paste it, check it, and move on. That's genuinely useful — but you're still the
one driving the keyboard.

An agent is different. You give it a task, plus access to your repository and a set of
tools — reading files, writing files, running shell commands, Git, web search — and it
works through a plan under your supervision: reading the code, editing it, running the tests, and
iterating toward a result.

So the unit of work moves from answering a question to carrying out a task.
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
      <li>Cross-cutting refactors and ports</li>
      <li>Scientific sparring — derive, check, critique, explain</li>
    </ul>
  </div>
  <div class="block cool">
    <span class="tag">Still yours</span>
    <ul>
      <li>Decisions only you can own</li>
      <li>What counts as a valid result</li>
      <li>Outputs neither of you can check</li>
      <li>Vague, exploratory tasks</li>
      <li>Work quicker to do than to brief</li>
    </ul>
  </div>
</div>

<p class="note">
<strong>Heuristic, 2026 edition:</strong> the agent increasingly <em>does</em> know your field. The boundary isn't domain knowledge any more — it's <strong>who owns the decisions and the verification</strong>. That's you.
</p>

<!--
Because the agent can act, the temptation is to throw everything at it — but it isn't
always the right choice.

It's a good fit for work that's well-defined but tedious — boilerplate, tests,
documentation, refactoring, exploring an inherited codebase, porting Fortran or Matlab to
Python. And — this is the part that's changed recently — it's also genuinely good as a
scientific sparring partner: deriving and checking equations, critiquing a method,
explaining an unfamiliar technique, reviewing your code for scientific errors.

What stays yours isn't a capability boundary so much as an ownership boundary: decisions
about research direction and acceptable approximations, what counts as a valid result,
anything neither you nor the agent can check objectively, vague exploratory work, and
anything where briefing takes longer than doing.

The heuristic used to be "if you could brief a skilled programmer who doesn't know your
field, an agent can help." That's out of date — the agent increasingly does know your
field. The boundary now is who owns the decisions and the verification. That's you.
-->

---

<div class="eyebrow">Mental model</div>

# A capable collaborator — junior in <em>your</em> project

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
  <p class="lead accent">Junior in your project, less junior in the science every release — it catches errors you didn't. <span v-mark="{ at: 4, type: 'circle', color: '#C15F3C' }">You certify correctness</span>.</p>
</v-click>

<!--
If you take one mental model away from today, make it this one: an agent is a capable
collaborator that's junior in *your* project — it doesn't know your conventions, your data
quirks, your unstated constraints.

That means three things in practice. You brief it — give the task shape: the deliverable,
the constraints, the files, the success criteria. You review what comes back as a draft —
read the diff, run the tests, check the assumptions. And you keep the scientific judgement
yourself — the reference values, the units, conservation, physical limits.

In
the science, it's less junior with every release — in my own work these models now catch
mathematical and scientific errors I hadn't spotted, and I learn from them. So don't treat
it as a typist you have to keep away from the science; treat it as a collaborator whose
scientific contributions you check.
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

<!--
**Part 2 · through ~13:00.** [If running long, the Cursor/Devin slide is the flex point —
compress it to one sentence each.]

So that's the idea. Now let's get concrete: what tools actually exist in mid-2026, what
they cost, and — the part that matters most for this room — what you already have through
Oxford.
-->

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
Don't think of these tools as a ranking — think of it as a map, along a spectrum of
autonomy.

At the assistive end you have in-editor help: Copilot completions, inline chat, VS Code's
agent mode. Then local repository agents that read, edit, and run tests on your machine —
Claude Code, the Codex CLI and app. Then cloud or pull-request agents that take a GitHub
issue and hand you back a PR — Codex Cloud, the Copilot cloud agent. And at the far end,
the high-autonomy tools that plan and execute long tasks, like Devin Desktop, often several
sessions at once.

The thing to notice is the trade-off along that axis: more autonomy buys you more leverage,
but it raises your review burden, not lowers it.
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
ChatGPT Edu is free at the point of use for every current Oxford staff member and student.
You just sign in at chatgpt.com with your ox.ac.uk address — it's single sign-on. Your data
isn't used for training, and it's covered by InfoSec's security assessment. There are weekly
limits on the intensive features, such as "thinking" mode.

For an actual coding agent through Oxford, that's Codex — and it needs a consent form, one
for Codex Local for the app and CLI, one for Codex Cloud to connect a GitHub repo (staff only). Those
Codex tasks draw on the same weekly Edu allowance.

And you're not on your own with this: the OeRC AI Competency Centre runs training, guides
for AI-for-coding and for researchers, a "Getting Started with Codex" course, and regular
workshops. So the practical starting point is: ChatGPT Edu first, then complete the Codex
consent if you want to try the agentic side.
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
Let me pick out a few of the main tools rather than marching through all of them. First,
Claude Code, from Anthropic.

It runs locally, in your terminal — there's no remote index of your code. It searches and
edits across the whole repository without you hand-picking files, and it runs your tests,
your build tools, and Git for you. On price, it comes with the Pro plan at about seventeen
dollars a month on the annual deal, and then Max at a hundred or two hundred a month for
sustained heavy use.

What makes it distinctive for us is two things: it genuinely comprehends large codebases,
and it has the CLAUDE.md system — a file where you write persistent project instructions
that it reads at the start of every session. So it's the best fit if you're doing
substantial development and want a repository-aware local agent you can teach about your
project once.

One very current note: Anthropic released Fable 5 this week — their newest flagship — and
it runs in Claude Code. It's included on the subscription plans until the 22nd of June,
after which it moves behind usage credits.
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
<strong>Note:</strong> new Copilot sign-ups (Pro, Pro+, Max, student) <span v-mark="{ at: 1, type: 'highlight', color: 'rgba(193,95,60,0.18)' }">paused since April 2026 — still in effect</span>; check current status. Existing plans can upgrade.
</p>

<!--
If you live in VS Code, GitHub Copilot is the lowest-friction way in. The free tier already
gives you completions and limited chat; Pro is listed at ten dollars a month. It's not
locked to one model — there's a multi-model backend behind it — and it has tight GitHub
integration.

And it's not just autocomplete any more: VS Code's agent mode does multi-step file edits,
has terminal access and MCP tools, and reads persistent instruction files, much like Claude
Code but inside the editor.

One caveat you should know about: new Copilot sign-ups — Pro, Pro+, Max, and the student
plans — have been paused since April, and as of this week that's still in effect; GitHub
says they'll reopen "in the coming weeks", so check the Copilot page. Existing plans can
still upgrade. And a billing note: since the first of June, all Copilot plans bill through
GitHub's AI Credits, with a monthly allowance included. To be honest, this has priced me out, and seems more designed for corporate customers. Still, for VS Code users it's the
easiest first step.
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
Two more worth knowing. Cursor is a polished fork of VS Code with the AI built deeply in —
a free hobby tier, Pro at twenty dollars a month, agent mode, cloud agents, and its own
code-review bot. If you want one cohesive all-in-one IDE-plus-agent, it's a strong choice.

And then Devin — and I'll flag this explicitly because the naming changed: Windsurf, the IDE
that used to be Codeium's, was acquired by Cognition and is now rebranded as Devin Desktop.
Free light quota, Pro at twenty dollars. Devin is the highest-autonomy tool here — give it
an issue and it'll plan, code, test, and open a PR.
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
So how do you choose? My advice is to start from access.

Use Oxford's provision first — ChatGPT Edu, then Codex once you've done the consent. If
you're already in VS Code, you could try Copilot's agent mode or a Codex or Claude extension there.
If you want deep local work on a real repository, that's Claude Code or the Codex CLI and
app. And only if you're doing sustained, heavy development does it make sense to pay for the
high-autonomy options like Cursor or Devin.

Whichever you pick, the same three
habits carry you: scope the task tightly, work on branches, and verify the output. That's
Part Three.
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

<!--
**Part 3 · through ~19:00.**

This is the practical heart of the talk: four habits that separate people who get real value
from agents from people who get a mess. Scope, context, safety, verification.
-->

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
The single most common mistake new users make is throwing a loosely-defined problem at an
agent and expecting a solution. Agents can fail at vague tasks the same way junior programmers
do — except faster, and more confidently.

So before you start anything, ensure you can answer five questions. What is the concrete deliverable? How will I
know it worked — ideally something testable? What does the agent need to know that it can't
infer from the code? What should it not do — what are the boundaries? And is this even the
right tool for this task?

The code on the right makes the key distinction concrete. "A function that reads a variable
from a NetCDF file and returns a masked array" — that's a deliverable, an agent can act on
it. "Improve the data loading code" is not a deliverable; it's a wish. Get the task to the
top form before you hand it over.
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
Once you've scoped it, the agent needs context — and there are three kinds.

Persistent context goes in a project instructions file — CLAUDE.md for Claude Code, AGENTS.md,
or copilot-instructions.md. These are read at the start of every session, so you write them
once, and possibly update them periodically: what the project does, the conventions, the test framework. Be specific — e.g., "this project
uses pytest, black, and NumPy docstrings."

Scientific context is the part that's on us. A frontier agent often knows the physics in
general — what it cannot know is which constraints apply to *your* configuration. It doesn't necessarily know that your timestep has to satisfy the CFL
condition, unless you say so. If you're implementing a parameterisation, give it the
governing equations, the expected ranges, the known numerical pitfalls.

And task context: point at the code precisely. "The advect function in
src/dynamics/advection.py" is unambiguous; "the advection function" might not be. On the
right is a trimmed CLAUDE.md so you can see what that looks like in practice.
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
A quick but important idea: treat context as a budget.

It matters for two reasons. Cost — you pay for (or have count towards your usage limits) every token going in and coming out, and a
long history can re-send itself every turn. And attention — over very long contexts the model
accumulates stale detail and the quality actually degrades. The fix is to chain compact,
well-scoped tasks with clear endpoints rather than running one enormous session.

Concretely: start fresh after you finish a sub-task; use `/compact` when a session has been
productive but is getting long; keep your standing rules in the instruction file so you're
not re-explaining them; and give the agent paths rather than pasting whole files. Small
habits, but they keep both your bill and your output quality healthy.
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
This is one of the most important practices in the whole talk, so I'll be blunt about it:
Git is your safety net, and it's non-negotiable.

The mindset is to treat the agent's output like a pull request from a collaborator you
respect but don't yet fully trust. So: always work on a branch — never let an agent work on
main. Let it commit incrementally as it goes, so you have checkpoints you can roll back to.
Review every change with git diff before you accept it. And run your tests.

One small thing that saves real pain: keep your .gitignore current, so credentials, data
files, and build artefacts can never accidentally end up in an agent's commit. If a session
goes off the rails, those commit checkpoints mean you just check out the last good state and
carry on.
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
  <v-click><li><strong>Second reviewer</strong> — a fresh agent checks the science: signs, units, derivations. It catches <em>your</em> errors too.</li></v-click>
</ul>

<v-click>
  <p class="lead accent">Agent-written numerical code is not accepted until it is validated.</p>
</v-click>

<!--
And then verification — because trust should come from checks, not from how confident the
output looks. This is especially true for us, where a bug can produce a plausible-looking but
wrong result.

Six things. Ask for tests alongside the implementation — a function without a test is a
function you can't verify. Compare against a reference: an analytical solution, a slower
implementation, literature values, or your previous hand-written version. Check the physics —
conservation, positivity, boundaries, units. Run your existing suite, because agents often
break shared code in subtle ways. Read the code — actually read what went in, not just
whether the tests went green. It's going into your research software; you own it.

And the sixth is new, and it cuts the other way: use a fresh agent session — ideally a
different model — as a second scientific reviewer. Ask it to check the signs, the units, the
derivation. It will catch errors in the agent's work *and in yours*.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART FOUR</div>
  <h1>Deep dives</h1>
  <div class="title-rule"></div>
  <p>What Claude Code and Codex share, where they differ — and the cost mechanics underneath.</p>
</div>

<!--
**Part 4 · through ~24:00.**

Now a bit deeper on the two tools you're most likely to actually use — Claude Code and Codex.
The headline is that they've converged: same concepts, same shapes, different emphasis. So
I'll show you the shared anatomy once, then the differences that actually matter, and then
the cost mechanics underneath all of them.
-->

---

<div class="eyebrow">Claude Code &amp; Codex · what's shared</div>

# Two products, one anatomy

| Concept | Claude Code | Codex |
|---|---|---|
| Surfaces | CLI · desktop app · web · IDE extension | app · CLI · cloud · IDE extension |
| Persistent instructions | **CLAUDE.md** — <code>/init</code> to draft | **AGENTS.md** |
| On-demand knowledge | Skills | Skills |
| Plan before code | Plan mode (<code>Shift+Tab</code>) | <code>/plan</code> |
| Parallel work | Worktrees, parallel sessions | Worktree per task |
| Runs unprompted | Routines | Automations |

<p class="note">
Learn the <strong>concepts</strong> once — instruction files · plan first · skills · worktrees · <strong>explore → plan → implement → commit</strong> — and they transfer to whichever agent you use.
</p>

<!--
Rather than a tour of each product, I'll give an overview of their shared features, and then some differences.

Both ship as a CLI, an app, a cloud agent, and an editor extension. Both read a persistent
instruction file at the start of every session — CLAUDE.md for Claude Code, where `/init`
drafts you a starter from the project; AGENTS.md for Codex. And the parity runs deep: both
support nested per-directory files for subsystem-specific rules and a global personal file
that applies across all your projects. Both have skills — modular,
on-demand knowledge that loads when relevant instead of every session. Both let you plan
before any code is written: plan mode in Claude Code, Shift+Tab, where it reads and proposes
but changes nothing until you approve; the `/plan` command in Codex. That plan step is where
you catch misunderstandings early — before the tokens are spent and the diff exists. Both run
parallel sessions safely via Git worktrees. And both now run unprompted, scheduled or
event-triggered — Routines in Claude Code, Automations in Codex: nightly test triage,
automatic PR review.
-->

---

<div class="eyebrow">Claude Code &amp; Codex · what differs</div>

# Same anatomy, different centre of gravity

<div class="cols cols-2">
  <div class="block">
    <span class="tag">Access at Oxford</span>
    <p><strong>Codex</strong> comes with ChatGPT Edu — consent forms, ~30 queries/week. <strong>Claude Code</strong> needs a personal plan, from $17/mo.</p>
  </div>
  <div class="block">
    <span class="tag">Default workflow</span>
    <p><strong>Claude Code:</strong> interactive local session in your terminal. <strong>Codex:</strong> headline flow is dispatch — issue in, PR out.</p>
  </div>
  <div class="block">
    <span class="tag">Safety model</span>
    <p><strong>Claude Code</strong> mediates each action through permission modes — plan, ask, auto. <strong>Codex</strong> runs tasks inside an OS-level sandbox.</p>
  </div>
  <div class="block">
    <span class="tag">Token economics</span>
    <p>Mid-2026 reports: Claude burns more tokens per task; Codex allowances stretch further at the same price tier.</p>
  </div>
</div>

<p class="note">
Benchmarks have them near parity — choose by <strong>access and workflow</strong>, not capability. Either way: review every PR for the science.
</p>

<!--
So if they're the same shape, what actually decides between them? Four things.

Access. Codex is the agent Oxford already gives
you: it comes with ChatGPT Edu once you've done the consent forms, drawing on the weekly
allowance of around thirty queries — treat those as scarce and spend them on tasks that are
worth it. Claude Code has no institutional route; it needs a personal plan, from about
seventeen dollars a month.

Workflow. Claude Code's natural home is the interactive
local session: you in the terminal, supervising as it works. Codex leans towards dispatch:
its headline flow takes a GitHub issue, explores the repo, implements, runs the tests, and
hands you back a pull request. For routine, well-specified issues that's genuinely efficient.

Safety model — both keep you in the loop, by different mechanisms. Claude Code mediates each
action through permission modes: plan mode, where it can't change anything; the default,
asking before it acts; and an auto mode for long runs. Codex's distinctive move is
sandboxing — tasks execute inside an OS-level sandbox, with approval settings controlling
what reaches your real files and network.

And token economics — this one's from the mid-2026 comparison reports rather than gospel,
and it moves fast: Claude tends to burn more tokens per task, and Codex's message allowances
stretch further at the same price tier. Worth checking before you commit to heavy use.

On raw capability the benchmarks have them near parity — so choose by access and workflow.
-->

---

<div class="eyebrow">Cost mechanics</div>

# The model is stateless — you pay to re-send the chat

<div class="flow">
  <span>turn 1 sends <strong>1</strong></span><span class="arrow">→</span>
  <span>turn 2 sends <strong>1·2</strong></span><span class="arrow">→</span>
  <span>turn 3 sends <strong>1·2·3</strong></span><span class="arrow">→</span>
  <span>uncached cost grows <strong>~quadratically</strong></span>
</div>

<v-click>
  <p class="lead">Prompt caching — automatic in Claude Code <em>and</em> Codex — re-bills the unchanged prefix at <span v-mark="{ at: 1, type: 'box', color: '#C15F3C' }">~10% of input price</span>.</p>
</v-click>

<v-click>
  <p class="lead">Caching flattens the bill, <span v-mark="{ at: 2, type: 'underline', color: '#C15F3C' }">not the attention degradation</span> — only shorter context fixes that. <em>Context is a budget</em> (Part 3).</p>
</v-click>

<p class="note">
Scale: a complex task ≈ <strong>50k–500k tokens</strong>, roughly $3–$30 at frontier pricing. Overspend comes from long context, mismatched models, redundant reads, runaway or parallel agents.
</p>

<!--
Here's the cost intuition that catches people out. The agent model is *stateless*. It remembers nothing between steps, so every step
re-sends the entire history so far as input. Turn one sends one turn's worth; turn ten sends
ten. Uncached, the cost of a session grows roughly quadratically with its length.

What rescues this is prompt caching — automatic in both Claude Code and Codex: the unchanged
prefix of the conversation is re-billed at about a tenth of the normal input price, which
flattens the dollar curve, and the quota burn, considerably. Caching is not the same thing
as `/compact`: caching makes re-sending the same history cheaper; `/compact` summarises the
history so there's less of it to send.

And caching does nothing for the third cost — attention. Over very long contexts quality
degrades regardless of what you're billed; only shorter context helps. That's the mechanism
behind "context is a budget" back in Part Three: fresh sessions, `/compact`, paths not pastes.

For scale: a complex task on a medium codebase can run fifty thousand to half a million
tokens — roughly three to thirty dollars at frontier pricing: Opus 4.8 is five dollars in,
twenty-five out per million tokens, and Fable 5 is ten and fifty. On a subscription plan, a
few big tasks can eat your weekly or monthly allocation.
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
So the cost message in one line: use the cheapest mode that reliably does the job.

Oxford's Edu access is your free tier for learning,
scoping, and limited Codex tasks, bounded by that weekly quota. A Claude Pro or ChatGPT Plus
plan suits occasional short sprints to medium-usage agent-drive work. The Max or Pro tiers are for high-usage agent-driven work.
And direct API billing is for automation and bulk jobs — powerful, but it can spike if you're
not watching it.

Three habits underneath all of it: match the model to the task before you start rather than
retrying a bad prompt on a more expensive model; compact or clear long sessions; and monitor your usage dashboard.
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

<!--
**Part 5 · through ~29:00.**

Now the sober part — and I think the most important part for this room. Where do these tools
fail? And I'm going to start with the one that matters most for scientists.
-->

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
Never deploy without validation against reference values; read any algorithm of consequence line by line.
</p>

<v-click>
  <p class="note">
  <strong>It cuts both ways:</strong> an agent reviewing <em>your</em> derivation will catch errors you missed. Use it as a second reviewer — never the only one.
  </p>
</v-click>

<!--
This is the slide I'd most want you to remember from the whole talk. So, the code runs. The
tests pass. The result looks plausible. And the science is wrong.

That's what makes this dangerous. A normal software bug crashes, or gives you obvious
nonsense. A scientific error doesn't announce itself — the agent is confident, the code
executes, the numbers are in the right ballpark. The failure is plausible, confident, and
executable, which is the worst combination.

The forms it takes are familiar to you: a sign error — right magnitude, wrong direction; a
unit conversion hidden by scale; a boundary or array-staggering mistake; a missed physical
constraint like conservation, positivity, or the CFL condition. So the rule is firm: never
deploy agent-written numerical code without validating it against reference values, and for
any algorithm of consequence, read it line by line. This is the part that stays yours.

And to be fair to the tools — the same capability cuts both ways. So fold it into the process: a fresh agent as a second
scientific reviewer.
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
Beyond the science itself, there's a cluster of more ordinary technical failure modes worth
naming.

Hallucination: the agent invents an API that doesn't exist, a physical constant, a paper, or
makes a confident but false claim about how your existing code behaves. Dependencies:
it suggests packages that aren't real, don't match the API it assumes, or quietly add risk.
Repository damage: deleted files, scope creep beyond what you asked, sensitive data committed,
or unsafe Git operations. And reproducibility: unrecorded environments, unseeded randomness,
data sources that shift under you.

The mitigations are routine, and that's the point — make them habits. Run the code. Check the
imports and any new dependencies actually exist. Look at git status and git diff before you
commit. Record your versions and set your seeds. Use instructions files.
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
    <p>A risk to skill-building <em>and</em> an excellent tutor — for the science, not just the code — within assessment rules.</p>
  </div>
</div>

<p class="note">
Oxford ChatGPT Edu and Codex inputs are <strong>not used for model training</strong>; data residency is in the US.
</p>

<!--
Last in this section: the rules around the work, which are easy to skip past but matter.

On data handling — be careful what you expose: credentials, unpublished data, anything
confidential, anything under export controls. The reassuring
news for Oxford is that ChatGPT Edu and Codex inputs are not used for model training, though
data residency is in the US. On disclosure — think about authorship and attribution,
licensing, and your reproducibility obligations if published results lean on agent-written
code.

And students for students, there's a genuine risk: a student who
leans on an agent to produce code they don't understand doesn't build the core skills. But
the very same tool is an excellent tutor — and not just for programming. Worked examples,
walking through code line by line, explaining why a method works, the reasoning behind a
derivation — people increasingly learn the science itself this way, and I include myself in
that. So the nuance is: be thoughtful about agent use for assessed or production work, while
actively encouraging it as a way to learn and explore.
-->

---

<div class="eyebrow">Takeaway</div>

# When to use agents

| Use | Be cautious | Don't skip |
|---|---|---|
| Well-scoped implementation | Decisions that are yours | Reference checks |
| Tests, docs, scaffolding | Unverifiable outputs | Diff review |
| Exploration & mechanical changes | Sensitive data | Dependency review |
| Scientific sparring & second review | Long unsupervised runs | Scientific ownership |

<p class="lead accent">Agents propose, check, and teach — decisions and verification stay yours.</p>

<!--
To pull this together, use agents confidently for well-scoped implementation, for tests, docs and scaffolding, for
exploring a codebase and mechanical multi-file changes — and, as we've seen, as a scientific
sparring partner and second reviewer. Be cautious wherever judgement or sensitivity enters:
the decisions that are yours to own, outputs you can't verify, sensitive data, long
unsupervised runs. And never skip the four things in the last column — reference checks, diff
review, dependency review, and scientific ownership.
-->

---
layout: center
class: divider
---

<div class="divider">
  <div class="dnum">PART SIX</div>
  <h1>Live demo</h1>
  <div class="title-rule"></div>
  <p>Process, not spectacle (depends how it goes).</p>
</div>

<!--
[OPTIONAL — not in the 30-min budget. ~5 min if time and appetite allow. The point is to
show the *workflow*, not an impressive autonomous result. If you're not running it live,
say one line — "I'll spare you the live demo, but here's the shape of it" — and advance to
the close. The two background slides are quick (~1–2 min) so the audience knows what we're
building. Prompts are in docs/d8_prompts.md; full demo script in docs/seminar_notes.md §6.2.]
-->

---

<div class="eyebrow">Demo background · the science</div>

# Where does the water go?

<p class="lead">Given a landscape's elevation, <span v-mark="{ at: 1, type: 'underline', color: '#C15F3C' }">where does water flow, and where does it collect?</span></p>

<div class="flow">
  <span>Elevation grid (DEM)</span><span class="arrow">→</span>
  <span>Flow directions</span><span class="arrow">→</span>
  <span>Flow accumulation</span><span class="arrow">→</span>
  <span>Rivers &amp; catchments</span>
</div>

<v-click>
  <p class="note" style="margin-top: 1.6rem;">
  This is the basis of <strong>drainage networks, catchments (watersheds), erosion, and flood routing</strong>. Our demo — <strong>d8demo</strong> — is a tiny <em>educational</em> version on small synthetic landscapes, not a production hydrology tool.
  </p>
</v-click>

<!--
**Demo background 1 · ~30s.**

First, the wider picture — what is the package even for. This is hydrological flow modelling:
you start from a landscape's elevation and you want to know where water flows and where it
collects. The input is a DEM — a digital elevation model, just a grid of heights. From that
you derive, first, a flow direction for every cell, and then flow accumulation — how much
drains through each cell — which is what gives you rivers, channels, and catchment boundaries.

It underpins drainage networks, catchment delineation, erosion and flood modelling. The thing
we'll build, d8demo, is a deliberately tiny, educational version of this on small synthetic
landscapes — not a production hydrology package.
-->

---

<div class="eyebrow">Demo background · the method</div>

# D8 flow routing

<div class="cols cols-3">
  <v-click>
    <div class="block">
      <span class="tag">The rule</span>
      <h3>Steepest of eight</h3>
      <p>Water runs downhill: each cell sends <em>all</em> its flow to the single lowest of its eight surrounding neighbours. One cell → one downstream cell.</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Accumulation</span>
      <h3>Count what drains through</h3>
      <p>For each cell, count how many cells drain through it. Totals grow downstream, so the large values trace out the channels.</p>
    </div>
  </v-click>
  <v-click>
    <div class="block">
      <span class="tag">Outlets</span>
      <h3>Where flow leaves</h3>
      <p>The lowest cells have no downhill neighbour — water leaves the grid there.</p>
    </div>
  </v-click>
</div>

<v-click>
  <p class="note">"D8" = <strong>deterministic, eight directions</strong>. It is the simplest of a family of routing methods — and the building block the real tools elaborate on.</p>
</v-click>

<!--
**Demo background 2 · ~45s.**

So how does D8 actually decide where the water goes? The rule is deliberately simple. Water
runs downhill, so each cell just sends all of its flow to whichever of its eight surrounding
neighbours is lowest — the steepest way down. One cell, one downstream cell. That's the "D8":
deterministic, eight directions.

Once every cell has a direction, accumulation is just bookkeeping: for each cell, count how
many cells ultimately drain through it. Those totals grow as you go downstream, so the big
numbers light up the channels. And the lowest cells — the ones with no lower neighbour — are
outlets, where water leaves the grid. That's the whole method; the production tools add
machinery on top, but this is the core.
-->

---

<div class="eyebrow">Demo background · worked example</div>

# Small enough to check by hand

<div class="d8-fig">
  <div class="d8-panel">
    <div class="d8-cap">Elevation (DEM)</div>
    <div class="d8-grid d8-dem">
      <div class="d8-cell">1.2</div><div class="d8-cell d8-ch">0.2</div><div class="d8-cell">1.2</div>
      <div class="d8-cell">1.1</div><div class="d8-cell d8-ch">0.1</div><div class="d8-cell">1.1</div>
      <div class="d8-cell">1.0</div><div class="d8-cell d8-ch">0.0</div><div class="d8-cell">1.0</div>
    </div>
  </div>
  <div class="d8-sep">→</div>
  <div class="d8-panel">
    <div class="d8-cap">Flow direction</div>
    <div class="d8-grid d8-flow">
      <div class="d8-cell">→</div><div class="d8-cell">↓</div><div class="d8-cell">←</div>
      <div class="d8-cell">→</div><div class="d8-cell">↓</div><div class="d8-cell">←</div>
      <div class="d8-cell">→</div><div class="d8-cell d8-outlet"><span class="d8-dot"></span></div><div class="d8-cell">←</div>
    </div>
  </div>
  <div class="d8-sep">→</div>
  <div class="d8-panel">
    <div class="d8-cap">Accumulation</div>
    <div class="d8-grid d8-acc">
      <div class="d8-cell d8-a1">1</div><div class="d8-cell d8-a3">3</div><div class="d8-cell d8-a1">1</div>
      <div class="d8-cell d8-a1">1</div><div class="d8-cell d8-a6">6</div><div class="d8-cell d8-a1">1</div>
      <div class="d8-cell d8-a1">1</div><div class="d8-cell d8-a9">9</div><div class="d8-cell d8-a1">1</div>
    </div>
  </div>
</div>

<style scoped>
.d8-fig { display: flex; align-items: center; justify-content: center; gap: 1.1rem; margin: 1.6rem 0 1.2rem; }
.d8-panel { display: flex; flex-direction: column; align-items: center; gap: .55rem; }
.d8-cap { font-size: .72rem; letter-spacing: .06em; text-transform: uppercase; color: #8a8178; font-weight: 600; }
.d8-grid { display: grid; grid-template-columns: repeat(3, 50px); grid-template-rows: repeat(3, 50px); gap: 4px; }
.d8-cell { display: flex; align-items: center; justify-content: center; border-radius: 7px; font-size: 1rem; font-weight: 600; color: #2c2a28; font-variant-numeric: tabular-nums; }
.d8-dem .d8-cell { background: #ddc9ad; }
.d8-dem .d8-ch { background: #9cc0d2; color: #1d3b48; }
.d8-flow .d8-cell { background: #f1ece5; color: #C15F3C; font-size: 1.35rem; font-weight: 700; }
.d8-flow .d8-outlet { background: #C15F3C; }
.d8-flow .d8-outlet .d8-dot { width: 13px; height: 13px; border-radius: 50%; background: #fff; box-shadow: 0 0 0 3px rgba(255,255,255,.4); }
.d8-acc .d8-cell { background: rgba(193,95,60,.10); }
.d8-acc .d8-a3 { background: rgba(193,95,60,.32); }
.d8-acc .d8-a6 { background: rgba(193,95,60,.58); color: #fff; }
.d8-acc .d8-a9 { background: rgba(193,95,60,.85); color: #fff; }
.d8-sep { font-size: 1.5rem; color: #c0b7ac; align-self: center; margin-top: 1.3rem; }
</style>

<p>A 3×3 valley: a central channel falling south, with walls either side. The wall cells drain inward, the channel drains south, and the bottom-centre cell is the outlet (●) where flow leaves.</p>

<v-click>
  <p class="lead accent">Accumulation builds to 9 — every cell — at the outlet. Tiny, deterministic cases like this are how we check the agent's numerical code.</p>
</v-click>

<!--
**Demo background 3 · ~30s. (Cut this slide if short on time.)**

And because the grids are tiny, we can check the whole thing by hand — which is exactly the
point. Here's a three-by-three valley: a channel falling south, walls either side. The wall
cells drain inward to the channel, the channel drains south, and the bottom-centre cell is
the outlet, where water leaves. Follow the accumulation: each wall cell is one, and the
channel builds up — three, six, nine — until the outlet collects all nine cells in the grid.

Hold onto that, because it's the answer to the question the demo ends on. When the agent's
tests pass, "is the science right?" isn't a leap of faith — we have hand-checkable cases like
this to validate against.
-->

---

<div class="eyebrow">Live demo</div>

# Building a package, the right way

<div class="block" style="margin-top: 1.2rem;">
  <span class="tag">Setup</span>
  <p>Start from a scaffolded repo on a fresh branch (<code>demo-live</code> off <code>demo-start</code>). Prompts prepared in <code>docs/d8_prompts.md</code>; the finished package waits on <code>demo-solution</code> as a safety net.</p>
</div>

<ul class="steps">
  <li><strong>Scaffold</strong> — uv package, minimal deps, README, CLAUDE.md / AGENTS.md.</li>
  <li><strong>Source + tests</strong> — agent researches D8, asks questions, proposes a plan and states assumptions <em>before</em> coding.</li>
  <li><strong>Example</strong> — end-to-end CLI script: DEM → route → accumulate → plot.</li>
  <li><strong>Docs</strong> — a short background note.</li>
</ul>

<p class="lead accent">Review the diff, run <code>uv run pytest</code> — the tests pass and the figure looks right. But is the science right?</p>

<!--
[OPTIONAL demo slide — facilitation cues, not a script. The demo builds the d8demo package
live from a clean scaffold, using the staged, well-scoped prompts in docs/d8_prompts.md. Branch
demo-live off demo-start first; demo-solution holds the finished package if you run out of
time or it goes awry.

You won't run all four stages in five minutes — pick one or two that show the workflow. The
scaffold prompt and the source+tests prompt are the richest: the agent researches D8, asks
clarifying questions, proposes a plan and states its assumptions *before* writing code, and
persistent context goes into CLAUDE.md/AGENTS.md up front. Then review the diff and run
`uv run pytest`.

Land the punchline: the tests pass and the plot looks plausible — "but is the science right?"
— and point back to the hand-checkable cases from the previous slide. Debrief in one line:
the agent did real work, fast; we supplied the scoping, the context, and the scientific
judgement. Full script: docs/seminar_notes.md §6.2.]
-->

---
layout: center
class: takeaways
---

<div class="eyebrow">In closing</div>

# Six things to take away

<ul class="steps" style="max-width: 54rem;">
  <li>Agent-driven development is real and useful — for well-scoped tasks with clear criteria.</li>
  <li>Agents are becoming scientific collaborators — propose, check, teach — while decisions stay yours.</li>
  <li>You already have access — ChatGPT Edu and Codex via SSO, with OeRC support.</li>
  <li>The bottleneck moves to task definition, context, and verification.</li>
  <li>Scientific correctness is your responsibility — an agent is a second reviewer, never the only one.</li>
  <li>Use Git as your safety net — branches, commits, diffs.</li>
</ul>

<!--
**Close · ~29:00–31:00.**

Let me bring it together with six things to take away.

One: agent-driven development is real and useful — not hype, not magic — the shift from
answering questions to taking actions, for well-scoped tasks with clear criteria. Two, and
this is the part that's changed most recently: agents are becoming scientific collaborators,
not just coders — they propose approaches, check derivations, catch errors you missed, and
teach — while the decisions stay yours. Three: you already have access — ChatGPT Edu and
Codex through Oxford SSO, with OeRC there to help you start.

Four: the bottleneck doesn't disappear, it moves — to task definition, context, and
verification, and all three need your expertise. Five, and the one I'll keep repeating:
scientific correctness is your responsibility — and verification cuts both ways, so use an
agent as a second reviewer of your own work too; second, never the only one. And six: Git is
your safety net — branches, commits, diffs.

My honest advice is to start small and on something low-stakes — write some tests, scaffold
a project, get an inherited codebase explained to you, have it check a derivation — and
build your intuition before you put an agent anywhere near critical code. With that, let's
open it up.
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
    <p>What scientific decision would you never delegate to an agent — and why?</p>
  </div>
  <div>
    <span class="tag">Sceptical</span>
    <p>What would make you trust agent-written code in a published result?</p>
  </div>
</div>

<!--
[DISCUSSION — facilitation, not scripted; ~20 min, separate from the 30-min talk. Open with
the warm-up to get people talking — "has anyone actually used one of these on real research
code?" — and let a few war stories surface. Then steer toward the conceptual and governance
questions, and make sure the two sceptical ones get aired: the delegation boundary — what
scientific decision would you never hand to an agent, and why? — probes the talk's central
tension directly, and the published-result question tests whether the verification message
landed. If the room is quiet, the CLAUDE.md question ("what would you put in one for your
codebase right now?") is a reliable starter. Full bank of ten questions in
docs/seminar_notes.md §6.3.]
-->

---
class: disclosure
---

<div class="eyebrow">AI disclosure</div>

# How this talk was made

| Tool | How it was used |
| --- | --- |
| **Claude Code** — Claude Opus 4.8, Fable 5 | Slide design & build; content drafting & revision |
| **ChatGPT** — GPT 5.5 Thinking | Research, fact-checking, ideation & structure |
| **OpenAI Codex** — Oxford institutional access, GPT 5.5 | Coding assistance |
| **GitHub Copilot** — in VS Code, Claude Sonnet 4.6, GPT 5.5 | Project scaffolding |

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
[Closing / hand-off slide — show during questions.]

And in the spirit of the talk: this seminar was itself built with these tools. The slides,
the research, and the scaffolding were done with Claude Code, ChatGPT, Codex, and Copilot —
listed here with the models. I directed and verified all of it, and I'm responsible for the
content. It felt only right to practise the disclosure I'd ask of anyone else. Happy to take
questions.
-->
