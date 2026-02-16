---
name: bloqade-index
description: This skill should be used when users ask how to use bloqade and the correct generated documentation skill must be selected before going deeper into source code.
---

# bloqade Skills Index

## Route the request
- Classify the request into one of the generated topic skills listed below.
- Prefer abstract, workflow-level guidance for large scientific packages; do not attempt full function-by-function coverage unless explicitly requested.

## Generated topic skills
- `bloqade-build-and-install`: Build and Install (build, installation, compilation, and environment setup)
- `bloqade-developer-guide`: Developer Guide (developer architecture, extension points, and contribution workflow)
- `bloqade-getting-started`: Getting Started (initial setup, quickstarts, and core concepts)
- `bloqade-api-and-scripting`: API and Scripting (language bindings, APIs, and programmatic interfaces)
- `bloqade-simulation-workflows`: Simulation Workflows (simulation setup, execution flow, and runtime controls)
- `bloqade-examples-and-tutorials`: Examples and Tutorials (worked examples, tutorials, and cookbook usage)
- `bloqade-inputs-and-modeling`: Inputs and Modeling (inputs, system setup, models, and physical parameterization)
- `bloqade-advanced-topics`: Advanced Topics (merged low-frequency docs: manifesto and focused visualization/output topics)
- `bloqade-digital`: Digital (documentation grouped under the 'digital' theme)
- `bloqade-analog`: Analog (documentation grouped under the 'analog' theme)
- `bloqade-blog`: Blog (documentation grouped under the 'blog' theme)

## Documentation-first inputs
- `docs`

## Tutorials and examples roots
- `docs/quick_start`
- `docs/digital/examples`
- `docs/digital/tutorials`

## Test roots for behavior checks
- `test`

## Escalate only when needed
- Start from topic skill primary references.
- If those references are insufficient, search `<topic-skill>/references/doc_map.md`.
- If documentation still leaves ambiguity, open `<topic-skill>/references/source_map.md` and inspect the suggested source entry points.
- Use targeted symbol search while inspecting source (e.g., `rg -n "<symbol_or_keyword>" src`).

## Source directories for deeper inspection
- `src`
