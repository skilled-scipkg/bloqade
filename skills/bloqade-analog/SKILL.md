---
name: bloqade-analog
description: This skill should be used when users ask about analog in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Analog

## High-Signal Playbook

### Route conditions
- Use `bloqade-inputs-and-modeling` for geometry/hardware-capability specifics (`docs/analog/reference/hardware-capabilities.md`, `docs/analog/home/geometry.md`).
- Use `bloqade-build-and-install` for installation/migration environment blockers.
- Use `bloqade-simulation-workflows` for generic task/device execution semantics.
- Keep this skill for analog-mode concepts, Hamiltonian controls, waveform intent, and emulator-vs-hardware framing.

### Triage questions
- Is the request conceptual (physics/Hamiltonian) or operational (API/workflow)?
- Is the target emulator-only, hardware submission, or both?
- Which controls are needed: detuning, Rabi amplitude, phase, and local vs uniform modulation?
- Are waveforms symbolic/functional, sliced, or parameter-swept?
- Is this migrated legacy analog code (`bloqade` -> `bloqade.analog`)?
- Are there solver/runtime symptoms (e.g., stiff ODE warnings)?

### Canonical workflow
1. Map problem to analog-mode Hamiltonian terms (`Omega`, `Delta`, `phi`) and local-control context (`docs/analog/home/background.md`).
2. For runnable usage, prefer quick-start/index docs because waveform, submission, and emulation pages are currently placeholders (`docs/analog/home/waveforms.md`, `docs/analog/home/submission.md`, `docs/analog/home/emulation.md`, `docs/quick_start/analog/index.md`, `docs/analog/index.md`).
3. Define geometry and waveform with builder syntax, then validate structure/intent (`docs/analog/reference/overview.md`, `docs/quick_start/analog/index.md`).
4. Run locally first; if solver stiffness appears, retry with `interaction_picture=True` (`docs/quick_start/analog/index.md`).
5. Before hardware submission, enforce hardware-shape constraints (notably waveform edge conditions and discretization of arbitrary functions) (`docs/analog/index.md`, `docs/quick_start/analog/index.md`).
6. Use `.run_async` and task-status fetch for hardware queue visibility (`docs/quick_start/analog/index.md`).
7. Validate via report outputs and parameter sweep consistency (`docs/quick_start/analog/index.md`).

### Minimal working example
```python
from math import pi
from bloqade.analog.atom_arrangement import Honeycomb

geometry = Honeycomb(2, lattice_spacing=10.0)
program = (
    geometry.rydberg.rabi.amplitude.uniform
    .constant(value=pi / 2, duration=1.0)
)
result = program.bloqade.python().run(100)
print(result.report().counts())
```

```python
from math import pi

hardware_program = (
    geometry.rydberg.rabi.amplitude.uniform
    .piecewise_linear(values=[0, pi / 2, pi / 2, 0], durations=[0.06, 1.0, 0.06])
)
async_results = hardware_program.braket.aquila().run_async(100)
print(async_results.fetch())
```

### Pitfalls and fixes
- Pitfall: relying on placeholder pages for full procedure. Fix: use quick-start/index docs as executable source of truth (`docs/analog/home/waveforms.md`, `docs/analog/home/submission.md`, `docs/analog/home/emulation.md`, `docs/quick_start/analog/index.md`, `docs/analog/index.md`).
- Pitfall: hardware waveform violates start/end constraints. Fix: use compatible piecewise construction (`docs/analog/index.md`, `docs/quick_start/analog/index.md`).
- Pitfall: custom function waveforms expected to serialize fully. Fix: account for serialization limitation (`docs/quick_start/analog/index.md`).
- Pitfall: slicing creates invalid hardware tail. Fix: use `.record(...)` and a terminating segment (`docs/quick_start/analog/index.md`).
- Pitfall: ODE stiffness during emulation. Fix: run with `interaction_picture=True` (`docs/quick_start/analog/index.md`).
- Pitfall: migration regressions after package split. Fix: switch to `bloqade.analog` imports and/or run migrate tool (`docs/analog/home/migration.md`).

### Convergence and validation checks
- Control terms and modulation choices are explicitly mapped to intended physics.
- Local emulation run completes and report statistics are sane before hardware submission.
- Hardware-intended waveforms satisfy edge/discretization constraints.
- Parameter sweeps (`batch_assign`) return ordered, analyzable result sets.

### Source-code entry links (behavior details)
- `src/bloqade/README.md`
- `docs/quick_start/analog/index.md`
- `docs/analog/home/quick_start.md`
- `docs/scripts/gen_ref_nav.py`

## Scope
- Handle questions about documentation grouped under the 'analog' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/analog/home/background.md`
- `docs/analog/home/waveforms.md`
- `docs/analog/home/submission.md`
- `docs/analog/home/emulation.md`

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
- Use `docs/quick_start/analog/index.md` and `docs/analog/home/quick_start.md` for concrete runnable analog snippets.
- Use `docs/analog/home/geometry.md` and `docs/analog/reference/hardware-capabilities.md` for parameter and hardware-limit checks.
- Use `docs/analog/home/migration.md` for JSON/import migration behavior.
- Keep targeted search available: `rg -n "<symbol_or_keyword>" docs test src`.
