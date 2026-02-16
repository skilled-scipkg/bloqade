---
name: bloqade-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Examples and Tutorials

## High-Signal Playbook

### Route conditions
- Keep this skill for example-first onboarding and runnable pattern selection.
- Route to `bloqade-digital` when questions shift to dialect semantics.
- Route to `bloqade-simulation-workflows` when backend/task mechanics become the main blocker.

### Canonical workflow
1. Start from `docs/digital/examples/index.md` and choose one minimal example matching the user goal.
2. Run one SQUIN and one QASM2 baseline:
```bash
python docs/digital/examples/squin/ghz.py
python docs/digital/examples/qasm2/ghz.py
```
3. For noise/interoperability goals, run:
```bash
python docs/digital/examples/interop/noisy_ghz.py
```
4. For high-shot/QEC sampling goals, inspect and run:
```bash
python docs/digital/examples/tsim/magic_state_distillation.py
```
5. If results are unclear, use `references/source_map.md` to jump directly to function definitions and samplers.

### Validation checkpoints
- At least one example returns concrete output (measurements, emitted circuit, or samples).
- Parameterized examples are run with explicit small inputs before scaling.
- File-level symbols used in the answer are cross-checked in the corresponding example source.

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/digital/examples/index.md`
- `docs/digital/dialects_and_kernels/qasm2.md`

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
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/squin/deutsch_squin.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/digital/examples/qasm2/qft.py`
- `docs/digital/examples/qasm2/pauli_exponentiation.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`
