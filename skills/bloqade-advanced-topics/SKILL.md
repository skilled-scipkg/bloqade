---
name: bloqade-advanced-topics
description: This skill should be used when users ask about low-frequency bloqade topics that were previously single-doc skills, including manifesto-level guidance and focused visualization/output notes.
---

# bloqade: Advanced Topics

## Scope
- Handle low-frequency or highly specific topics that are too narrow for standalone routing skills.
- Keep answers compact and route back to core skills when the request becomes operational.

## Route the request
- Use this skill for project-level design framing (`docs/manifesto.md`).
- Use this skill for analog visualization-only questions (`docs/analog/home/visualization.md`).
- Route to `bloqade-analog` for analog build/run/debug workflows.
- Route to `bloqade-simulation-workflows` for backend/task execution and validation.
- Route to `bloqade-digital` for circuit dialect/interoperability behavior.

## Primary documentation references
- `docs/manifesto.md`
- `docs/analog/home/visualization.md`

## Workflow
- Start from the primary references above.
- If details are missing, inspect `references/doc_map.md` for full inventory in this merged topic.
- Use concrete examples from quick-start/tutorial files when user needs runnable behavior.
- If ambiguity remains, inspect `references/source_map.md` for targeted code-entry points.
- Cite exact documentation file paths in responses.

## Rapid simulation hand-off
- For noise and fidelity behavior reproduction, run `python docs/digital/examples/interop/noisy_ghz.py`.
- For depth/parallelism comparisons, run `python docs/digital/tutorials/auto_parallelism.py`.
- For control-flow/QEC-oriented checks, run `python docs/digital/examples/qasm2/repeat_until_success.py` or `python docs/digital/examples/tsim/magic_state_distillation.py`.
- Validate on small qubit and shot counts first, then scale only after outputs are stable.

## Tutorials and examples
- `docs/quick_start`
- `docs/digital/examples`
- `docs/digital/tutorials`

## Test references
- `test`

## Optional deeper inspection
- `src`

## Source entry points for unresolved issues
- `docs/quick_start/analog/index.md`
- `docs/digital/tutorials/auto_parallelism.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
