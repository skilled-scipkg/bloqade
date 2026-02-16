---
name: bloqade-getting-started
description: This skill should be used when users ask about getting started in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Getting Started

## High-Signal Playbook

### Route conditions
- Use `bloqade-build-and-install` for dependency/extras/environment failures (`docs/install.md`, `docs/contrib.md`).
- Use `bloqade-digital` for dialect-specific semantics and Cirq interoperability (`docs/digital/dialects_and_kernels/squin.md`).
- Use `bloqade-analog` for analog Hamiltonian/waveform/hardware constraints (`docs/analog/reference/overview.md`, `docs/analog/home/migration.md`).
- Use `bloqade-simulation-workflows` for device/task lifecycle and sampler strategy.

### Triage questions
- Is the user starting with digital circuits, analog programs, or both?
- Is the user migrating old (`<=0.15`) code or JSON artifacts?
- Does the user need local simulation only, or a future hardware path?
- Are they trying to call kernels like normal Python functions?
- Do they need a stable pinned setup due to ongoing API changes?
- Do they need interop with Cirq from day one?

### Canonical workflow
1. Install baseline package (`pip install bloqade`) and confirm imports (`docs/index.md`, `docs/install.md`).
2. Pick one first path: digital quick start or analog quick start (`docs/index.md`, `docs/quick_start/circuits/index.md`, `docs/quick_start/analog/index.md`).
3. Write a tiny kernel/program and run it on local simulator first (`docs/quick_start/circuits/index.md`).
4. Inspect IR early (`main.print()`) to confirm dialect lowering assumptions (`docs/digital/dialects_and_kernels/squin.md`).
5. If coming from old analog package layout, update imports or run migration tool for JSON files (`docs/analog/home/migration.md`).
6. Once first run succeeds, route to deeper topic skill (digital, analog, or simulation workflows).

### Minimal working example
```python
from bloqade import squin
from bloqade.pyqrack import StackMemorySimulator

@squin.kernel
def ghz(n: int):
    q = squin.qalloc(n)
    squin.h(q[0])
    for i in range(1, n):
        squin.cx(q[i - 1], q[i])
    return squin.broadcast.measure(q)

sim = StackMemorySimulator(min_qubits=4)
print(sim.run(ghz, args=(4,)))
```

```bash
python -m bloqade.analog.migrate <old_1.json> <old_2.json>
python -m bloqade.analog.migrate --help
```

### Pitfalls and fixes
- Pitfall: assuming APIs are stable. Fix: pin versions for projects requiring reproducibility (`docs/index.md`).
- Pitfall: calling decorated kernels directly. Fix: execute through backend (`sim.run(..., args=...)`) (`docs/digital/dialects_and_kernels/index.md`, `docs/quick_start/circuits/index.md`).
- Pitfall: old analog import paths after package restructuring. Fix: switch to `bloqade.analog` imports (`docs/analog/home/migration.md`).
- Pitfall: forgetting explicit `args` when running parameterized kernels. Fix: pass `args=(...)` (`docs/quick_start/circuits/index.md`).
- Pitfall: expecting full hardware path from digital quickstart today. Fix: treat hardware section as future-facing and focus on local simulation first (`docs/quick_start/circuits/index.md`).
- Pitfall: custom analog function waveforms expected to serialize cleanly. Fix: note serialization limitation and save results accordingly (`docs/quick_start/analog/index.md`).

### Convergence and validation checks
- Import + first-run smoke test passes on local simulation.
- Kernel IR prints and aligns with intended control flow.
- Legacy analog code imports or JSON migration runs without tooling errors.
- User can name which downstream skill to use for next-level depth.

### Source-code entry links (behavior details)
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/scripts/gen_ref_nav.py`
- `src/bloqade/README.md`

## Scope
- Handle questions about initial setup, quickstarts, and core concepts.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/index.md`
- `docs/analog/reference/overview.md`
- `docs/digital/dialects_and_kernels/squin.md`
- `docs/analog/home/migration.md`
- `docs/blog/posts/2023/bloqade-release.md`

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
- Use `docs/quick_start/circuits/index.md` and `docs/quick_start/analog/index.md` for first-pass runnable snippets.
- Use `docs/digital/examples/squin/ghz.py` for minimal executable digital patterns.
- Use `docs/digital/tutorials/circuits_with_bloqade.py` for end-to-end kernel/task usage.
- Use `docs/digital/examples/qasm2/ghz.py` for QASM2-based starter paths.
- Use `docs/analog/home/migration.md` for legacy JSON/import migration checks.
- Use `test/test_hello.py` as quick repository sanity signal.
- Keep targeted search available: `rg -n "<symbol_or_keyword>" docs test src`.
