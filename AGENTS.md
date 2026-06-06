# Agent-Driven Development Seminar — Project Context

## What this project is

A 30–40 minute seminar (+ ~20 min discussion) on agent-driven software development
for computational geoscientists at the University of Oxford. Audience: PhD students,
postdocs, RSEs, faculty. Experienced scientific programmers; most not advanced AI users.

## Repository structure

- `seminar_notes.md` — the full seminar content: all talking points, tool details,
  Oxford-specific access info, workflows, failure modes, demo script, and discussion
  questions. This is the source of truth. **Read this before writing any slides.**
- `slides/` — Slidev presentation. Entry point: `slides/slides.md`.
  Additional slide files can go in `slides/pages/`. Code snippets in `slides/snippets/`.

## Slidev setup

- Framework: [Slidev](https://sli.dev) v52, using the `seriph` theme
- Install dependencies: `cd slides && npm install`
- Dev server: `cd slides && npm run dev` (opens at localhost:3030)
- Build static: `cd slides && npm run build`
- Export PDF: `cd slides && npm run export`
- Package manager: npm (a pnpm-workspace.yaml exists from scaffolding but npm works fine)

## Seminar structure and target timings

| Segment | Duration |
|---|---|
| 1. Real-world impact + conceptual shift | 5 min |
| 2. Ecosystem — tools, pricing, Oxford access | 8 min |
| 3. Practical workflows | 8 min |
| 4. Codex and Codex deep dives | 7 min |
| 5. Cost, failure modes, risks | 7 min |
| 6. Live demo (optional) | 5 min |
| Discussion | 20 min |

## Slide structure (from seminar_notes.md §6.1)

- Slide 1: Title
- Slides 2–5: Conceptual shift (open with Anthropic 80%/800 stat; chat vs agent diagram;
  task decision framework; "capable junior collaborator" mental model)
- Slides 6–11: Ecosystem (landscape diagram; Oxford access; Codex; Copilot/VS Code;
  Cursor/Devin; decision tree)
- Slides 12–16: Practical workflows (scoping; context/AGENTS.md; context management;
  safe Git workflow; verifying outputs)
- Slides 17–20: Deep dives (Codex features; Codex features; cost management;
  cost comparison table)
- Slides 21–24: Failure modes (scientific correctness; other risks; security/governance;
  summary when-to-use)
- Slide 25: Live demo introduction
- Slide N: Discussion questions

## Style conventions for slides

- Keep text minimal — bullet points, not paragraphs; aim for one key idea per slide
- Use `---` to separate slides in slides.md
- Use `layout: two-cols` or `layout: center` where helpful
- Prefer `<v-click>` progressive reveals over putting everything on screen at once
- Code examples: use fenced code blocks with language tag
- Tables: markdown tables are fine for small comparison tables
- Diagrams: prefer simple ASCII/text diagrams or Mermaid (`mermaid` fenced blocks) over
  external images; avoid requiring internet at presentation time
- The frontmatter duration is 35min; keep that set

## Key content notes (do not omit these)

- The Anthropic 80%/800 stat is the intended **opening impact statement** (slide 2)
- Oxford access section must clearly cover: ChatGPT Edu (free via SSO), Codex (consent
  forms required), OeRC AI Competency Centre resources
- GitHub Copilot new sign-up pause (April–June 2026) should be noted
- Windsurf → Devin Desktop rebrand should be mentioned explicitly
- Scientific correctness is the most important failure mode for this audience; give it
  its own slide and appropriate emphasis
- Student training nuance: agents as learning tools as well as productivity tools

## What you should NOT do

- Do not invent pricing, features, or product details — use only what is in seminar_notes.md
- Do not use external image URLs that require internet access during the presentation
- Do not add slides for content not in seminar_notes.md without flagging it
- Do not modify seminar_notes.md unless asked

## Suggested approach for a multi-step agent session

1. Read seminar_notes.md in full (plan mode first)
2. Propose a slide-by-slide outline for approval before writing any content
3. Implement one section at a time; commit after each section passes review
4. Use a feature branch for each section: `git checkout -b slides/section-name`
