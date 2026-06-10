# Agent-Driven Software Development for Computational Geoscientists

Materials for a 30–40 minute seminar (plus ~20 minutes of discussion) on
agent-driven software development, given at the University of Oxford. The
audience is PhD students, postdoctoral researchers, research software
engineers, and faculty in computational geoscience.

## Repository contents

- [`slides/`](slides/) — the presentation, built with [Slidev](https://sli.dev).
  Entry point: [`slides/slides.md`](slides/slides.md).
- [`docs/seminar_notes.md`](docs/seminar_notes.md) — the full seminar notes:
  talking points, tool details, Oxford-specific access information, workflows,
  failure modes, demo script, and discussion questions.
- [`docs/d8_prompts.md`](docs/d8_prompts.md) — the staged prompts used in the
  live demo.

## Viewing the slides

```bash
cd slides
npm install
npm run dev      # dev server at http://localhost:3030
npm run build    # static build
npm run export   # export to PDF
```

## Live demo

The seminar includes an optional live demo that builds
[`d8demo`](https://github.com/sscivier/d8demo) — a tiny educational Python
package for D8 flow routing and flow accumulation on synthetic digital
elevation models — from a clean scaffold, using the staged prompts in
[`docs/d8_prompts.md`](docs/d8_prompts.md). The demo starts from that
repository's `demo-start` branch, with the finished package on
`demo-solution` as a safety net. `d8demo` is intentionally minimal and
educational; it is not a production hydrology package.

## AI disclosure

In the spirit of the talk, these materials were themselves built with the
tools they describe: Claude Code, ChatGPT, OpenAI Codex, and GitHub Copilot.
AI generated substantial portions of the design and text; the author directed
and supervised the work throughout, curated and verified all outputs, and is
responsible for the final content. See the disclosure slide at the end of the
deck for details.

## License

Licensed under the [Apache License 2.0](LICENSE). You are welcome to reuse
and adapt these materials for your own teaching, with attribution.
