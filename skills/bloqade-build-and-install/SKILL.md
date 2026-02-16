---
name: bloqade-build-and-install
description: This skill should be used when users ask about build and install in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Build and Install

## High-Signal Playbook

### Route conditions
- Use `bloqade-getting-started` for first-program onboarding and migration questions (`docs/index.md`, `docs/analog/home/migration.md`).
- Use `bloqade-digital` for dialect semantics, Cirq interop, and compiler/dialect behavior (`docs/digital/index.md`, `docs/digital/dialects_and_kernels/index.md`).
- Use `bloqade-analog` for analog program physics and hardware-shape waveform constraints (`docs/analog/index.md`, `docs/quick_start/analog/index.md`).
- Use `bloqade-developer-guide` for bug reports, feature requests, and contribution channels (`docs/analog/contributing/index.md`, `docs/contrib.md`).

### Triage questions
- Are you setting up as a user or as a contributor?
- Do you need `bloqade`, `bloqade-circuit`, `bloqade-analog`, or extras (`qasm2`, `stim`, `qbraid`)?
- Is this local simulation only, or do you also need eventual hardware execution paths?
- Do you require strict reproducibility (pinning) because APIs are still evolving?
- Are you trying to use compiler-pass APIs that are still marked under active development?

### Canonical workflow
1. Install base package first: `pip install bloqade` (`docs/install.md`, `docs/index.md`).
2. Add optional capabilities only as needed (`pip install bloqade[qasm2]`, `pip install bloqade[stim]`, `pip install bloqade[qbraid]`) (`docs/install.md`).
3. If analog-only migration is needed, install/use `bloqade-analog` path (`docs/install.md`, `docs/analog/home/migration.md`).
4. For contributor setup, install `uv`, then `uv sync --group dev` or `uv sync --all-groups` (`docs/install.md`).
5. Enable local quality gates: `pre-commit install`, then run `pytest` and docs build with `just doc-build` (`docs/contrib.md`, `docs/install.md`).
6. Smoke-test with a minimal kernel on local simulation before deeper work (`docs/quick_start/circuits/index.md`).
7. Only after baseline works, route into domain skills (`bloqade-digital`, `bloqade-analog`, `bloqade-simulation-workflows`).

### Minimal working example
```bash
pip install bloqade
pip install "bloqade[qasm2]"
python - <<'PY'
from bloqade import squin
from bloqade.pyqrack import StackMemorySimulator

@squin.kernel
def ghz(n: int):
    q = squin.qalloc(n)
    squin.h(q[0])
    for i in range(1, n):
        squin.cx(q[i - 1], q[i])

sim = StackMemorySimulator(min_qubits=4)
print(sim.run(ghz, args=(4,)))
PY
```

### Pitfalls and fixes
- Pitfall: assuming API stability. Fix: pin versions for production workflows (`docs/index.md`).
- Pitfall: directly calling dialect kernels as plain Python. Fix: run through a backend (`sim.run(..., args=...)`) (`docs/digital/dialects_and_kernels/index.md`, `docs/quick_start/circuits/index.md`).
- Pitfall: attempting advanced compiler-pass tuning immediately. Fix: defer until baseline run works (`docs/digital/compilation.md`, `docs/quick_start/circuits/index.md`).
- Pitfall: analog hardware waveforms not starting/ending at zero. Fix: shape waveform with hardware-compatible piecewise segments (`docs/analog/index.md`, `docs/quick_start/analog/index.md`).
- Pitfall: stiff analog ODE failures. Fix: retry with `interaction_picture=True` in emulator runs (`docs/quick_start/analog/index.md`).
- Pitfall: using the wrong dependency set for development. Fix: use `uv sync --group dev` / `--all-groups` and install pre-commit hooks (`docs/install.md`, `docs/contrib.md`).

### Convergence and validation checks
- `pip` installs complete and required extras import without errors (`docs/install.md`).
- A tiny kernel runs on local simulator with `args=(...)` and returns a result (`docs/quick_start/circuits/index.md`).
- Contributor flow passes `pre-commit`, `pytest`, and docs build (`docs/contrib.md`).
- If analog path is used, hardware-shape waveform constraints are validated before submission (`docs/analog/index.md`, `docs/quick_start/analog/index.md`).

### Source-code entry links (behavior details)
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/scripts/gen_ref_nav.py`
- `test/test_hello.py`
- `src/bloqade/README.md`

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/analog/index.md`
- `docs/digital/index.md`
- `docs/quick_start/analog/index.md`
- `docs/install.md`
- `docs/contrib.md`
- `docs/digital/compilation.md`
- `docs/analog/reference/standard.md`
- `docs/analog/home/quick_start.md`
- `docs/analog/home/gotchas.md`
- `docs/analog/contributing/design-philosophy-and-architecture.md`
- `docs/analog/contributing/code-of-conduct.md`

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
- Use `docs/quick_start/circuits/index.md` as first executable smoke-test baseline.
- Use `docs/digital/examples/squin/ghz.py` and `docs/digital/examples/qasm2/ghz.py` for runnable behavior baselines.
- Use `docs/digital/tutorials/circuits_with_bloqade.py` for task/backend lifecycle patterns.
- Use `docs/quick_start/analog/index.md` for analog installation-to-execution handoff checks.
- Use `test/test_hello.py` as minimal repository sanity baseline.
- Keep targeted search available: `rg -n "<symbol_or_keyword>" docs test src`.
