---
name: bloqade-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Inputs and Modeling

## High-Signal Playbook

### Route conditions
- Keep this skill for geometry, physical parameters, and model-input selection.
- Use `bloqade-analog` when the question becomes full analog workflow execution.
- Use `bloqade-simulation-workflows` when backend/task APIs are the primary blocker.

### Canonical workflow
1. Start with geometry and capability docs (`docs/analog/home/geometry.md`, `docs/analog/reference/hardware-capabilities.md`).
2. Choose concrete parameter patterns from quick-start examples (`docs/quick_start/analog/index.md`).
3. Run a compact parameterized modeling script:
```bash
python docs/digital/examples/qasm2/pauli_exponentiation.py
```
4. For parameterized ansatz tuning patterns, inspect:
```bash
python docs/digital/examples/qasm2/qaoa.py
```
5. Before large sweeps, verify parameter units/ranges and hardware constraints with small inputs.

### Validation checkpoints
- Geometry, waveform, and model parameters are explicit and dimensionally consistent.
- At least one modeling example runs with small fixed parameters.
- Any sweep plan documents input ranges and expected invariants before execution.

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/analog/reference/hardware-capabilities.md`
- `docs/analog/home/geometry.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

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
- `docs/analog/home/quick_start.md`
- `docs/analog/home/geometry.md`
- `docs/analog/reference/hardware-capabilities.md`
- `docs/digital/examples/qasm2/pauli_exponentiation.py`
- `docs/digital/examples/qasm2/qaoa.py`
