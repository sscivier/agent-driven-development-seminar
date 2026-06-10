# d8demo Prompts

## Scaffolding

````md
@README.md
I am preparing a live seminar demo on agent-driven scientific software development. We are in a cloned empty Git repo that already has:

- a LICENSE
- a placeholder README.md
- a short repository description

I'd like you to create the initial project scaffold for a tiny educational Python package called `d8demo`. The purpose of `d8demo` is to serve as a teaching/demo package for illustrating D8 flow routing and flow accumulation on synthetic digital elevation models (DEMs) in a live seminar. It should be clearly educational and not a production hydrology package.

The scope for this step includes:

- Initialising a `uv` Python package using Python 3.12
- Drafting a brief README.md that describes the project and how to install/run it, but does not include implementation-specific details
- Creating CLAUDE.md and AGENTS.md with concise instructions for future coding agents working in this repository
- Adding minimal runtime dependencies only

Important notes:

- This step is scaffold-only
- Do not create package architecture beyond what is needed for the initial project setup
- Do not create placeholder modules, functions, tests, examples, or implementation files yet
- Do not implement any D8 logic yet
- Keep the repository clean and minimal

Tooling preferences:

- Use `uv init --package`
- Use Python 3.12
- Use pytest for tests
- Use ruff for linting/formatting
- Add minimal runtime dependencies: NumPy and Matplotlib
- Do not add extra scientific, GIS, or hydrology libraries

The README should be short and non-implementation-specific, covering:

- what d8demo is
- that it is intended as a live seminar/demo project
- basic install instructions using uv
- a note that the implementation will be added later

CLAUDE.md and AGENTS.md should include brief guidance for future agents such as:

- Keep code simple, readable, and educational
- Prefer explicit NumPy code over clever abstractions
- Do not add dependencies without asking
- Do not use real datasets
- Use tiny deterministic synthetic arrays in tests
- Write tests before implementation changes
- Run `uv run pytest` after changes
- Run `uv run ruff format . && uv run ruff check .` after changes
- Preserve scientific assumptions in docstrings and comments
- Use Sphinx/ReST style docstrings
- Ask before changing package structure
- Do not implement production-grade hydrology features such as flat resolution, depression filling, nodata handling, or multiple-flow-direction routing unless explicitly requested

Do not introduce implementation details yet in these guidelines.

What I'd like you to do:

1. Inspect the repository briefly.
2. Set up the `uv` package scaffold.
3. Add the minimal runtime dependencies.
4. Write the brief README.md.
5. Create CLAUDE.md and AGENTS.md.
6. Summarise exactly what was added.
````

## Source Code

````md
@CLAUDE.md @pyproject.toml @README.md
I'd like to implement the first version of d8demo.

The goal is a small educational package that demonstrates D8 flow routing and flow accumulation on synthetic digital elevation models (DEMs). D8 flow routing is a method used in hydrology to determine the direction of water flow across a digital elevation model (DEM). It assigns flow from each cell in the DEM to one of its eight neighboring cells based on the steepest descent.

Do not create an example script or Jupyter notebook at this stage. This step is only the source package and tests.

Scope:

- Create the minimal source modules needed for the D8 demo.
- Implement synthetic DEM generation.
- Implement D8 flow routing.
- Implement flow accumulation.
- Add tests using tiny deterministic arrays.

Aspects to consider:

- How to represent the DEM and flow direction/accumulation data structures? (e.g., 2D NumPy arrays)
- What test cases to include for validating the D8 flow routing and accumulation implementations? (e.g., simple slopes, pits, ridges; input validation; edge cases; tests should be clear enough to use in a demo)
- How to handle ties in flow direction (e.g., when multiple neighbors have the same steepest descent)?

Scientific assumptions:

- DEMs are represented as 2D NumPy arrays.
- No flats, no nodata values, no edge wrapping.
- Cells with no lower neighbours are outlets.
- Outlets route flow to themselves.
- Use single flow direction (D8) for routing.

I'd like you to:

- briefly research D8 flow routing and accumulation + explain your understanding of the concepts;
- inspect the repository and instructions;
- ask me questions to clarify the requirements and implementation for the source code;
- propose the package design;
- propose tests;
- state your assumptions;
- propose an implementation plan.

Work in a separate branch, `demo-live`, off `demo-start`. Once the implementation is complete, update the README.md to reflect the implementation of the source code. Finally, summarise what you implemented, where, and how to run the tests; commit and push.
````

## Example

````md
@CLAUDE.md etc...
Now add a small end-to-end example that generates a synthetic DEM, computes flow accumulation, and produces a plot (or plots) suitable for the seminar. The user should be able to specify the dimensions and type of DEM with a CLI flag on the example script. If using cmaps for the flow accumulation and DEM, use `cmcrameri` `navia_r` and the upper 1/2 of `oleron`, respectively. Start by inspecting the repository and the instructions, and then ask me questions to clarify the requirements and implementation for the example. The example should be implemented in the current branch, `demo-live`. After the example is implemented, update the README.md with instructions for running the example. Finally, summarise how to run the example, what the plot shows, files added/changed, and commands run; commit and push.
````

## Docs

````md
@CLAUDE.md etc...
Now that the implementation and example are complete, please add a short background `.md` document explaining the D8 method used in this project. The audience is computational geoscientists who are comfortable with Python but may not be familiar with hydrological flow-routing methods.

Please:
- explain what a DEM is;
- explain D8 flow routing;
- explain flow accumulation;
- describe the assumptions and simplifications used in this implementation;
- explain how this educational implementation differs from production hydrology tools.

Keep the document concise (roughly 500–800 words), scientifically accurate, and consistent with the actual implementation. Add it to the repository in an appropriate location. After inspecting the repository and the instructions, ask me questions to clarify the requirements and implementation for the document, and then write it. Finally, summarise what you added and where; commit and push.
````
