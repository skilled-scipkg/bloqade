---
name: bloqade-simulation-workflows
description: This skill should be used when users ask about simulation workflows in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Simulation Workflows

## High-Signal Playbook

### Route conditions
- Use `bloqade-digital` when the blocker is dialect semantics rather than execution backend mechanics.
- Use `bloqade-build-and-install` for missing simulator extras/dependencies.
- Use `bloqade-analog` for analog-emulation/hardware submission specifics.
- Keep this skill for backend selection, task lifecycle, and validation strategy.

### Triage questions
- Which kernel dialect is being executed (`squin`, `qasm2`, `stim`)?
- Do you need one-shot `run` or explicit task lifecycle (`device.task(...).run()`) ?
- Is full state access required (`state_vector`) or only measurement outputs?
- What shot scale is needed (hundreds vs millions/billions)?
- Are detector/observable annotations needed (QEC workflows)?
- Is user expecting remote/hardware execution from this API today?

### Canonical workflow
1. Start from a minimal kernel and confirm it lowers correctly (`docs/quick_start/circuits/index.md`).
2. Choose backend: PyQrack device for local simulation (`docs/digital/simulator_device/simulator_device.md`).
3. Execute with explicit args tuple via `run` or explicit `task` object (`docs/digital/simulator_device/tasks.md`).
4. Pull richer simulator-only diagnostics as needed (`state_vector`) (`docs/digital/simulator_device/simulator_device.md`).
5. For high-shot QEC, use STIM/TSIM `Circuit(...).compile_sampler(...)` paths (`docs/quick_start/circuits/index.md`).
6. Validate result semantics and sampling assumptions before scaling up.
7. Keep current limitation explicit: task docs currently describe local simulation devices (`docs/digital/simulator_device/tasks.md`).

### Minimal working example
```python
from bloqade.pyqrack import StackMemorySimulator
from bloqade import squin

@squin.kernel
def main():
    q = squin.qalloc(2)
    squin.gate.h(q[0])
    squin.gate.cx(q[0], q[1])
    return q

sim = StackMemorySimulator(min_qubits=2)
task = sim.task(main)
print(task.run())
```

```python
from bloqade.tsim import Circuit

circuit = Circuit(main)
sampler = circuit.compile_sampler()
print(sampler.sample(shots=10_000, batch_size=1_000))
```

### Pitfalls and fixes
- Pitfall: forgetting `args=(...)` for parameterized kernels. Fix: always pass explicit `args` tuple (`docs/quick_start/circuits/index.md`).
- Pitfall: assuming decorated kernel is directly callable Python. Fix: execute via simulator/task API (`docs/digital/dialects_and_kernels/index.md`, `docs/digital/simulator_device/tasks.md`).
- Pitfall: expecting remote hardware task objects in this workflow immediately. Fix: keep to current local simulation constraints (`docs/digital/simulator_device/tasks.md`).
- Pitfall: using low-shot APIs for QEC-scale sampling. Fix: move to STIM/TSIM compiled samplers (`docs/quick_start/circuits/index.md`).
- Pitfall: misreading state-vector availability as hardware parity. Fix: treat state vector as simulator-only diagnostic (`docs/digital/simulator_device/simulator_device.md`).
- Pitfall: over-optimizing with immature compiler-pass UX too early. Fix: establish baseline run first (`docs/quick_start/circuits/index.md`).

### Convergence and validation checks
- Minimal kernel runs reproducibly via both direct `run` and explicit task path.
- Result type matches kernel return contract.
- State-vector sanity checks (where used) agree with expected entanglement/correlation patterns.
- Sampler workflows return stable aggregate behavior at scaled shot counts.

### Source-code entry links (behavior details)
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `test/test_hello.py`

## Scope
- Handle questions about simulation setup, execution flow, and runtime controls.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/quick_start/circuits/index.md`
- `docs/digital/simulator_device/simulator_device.md`
- `docs/digital/simulator_device/tasks.md`

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
- Use `docs/digital/examples/squin/ghz.py` for baseline simulator behavior and noise-injection patterns.
- Use `docs/digital/tutorials/circuits_with_bloqade.py` for task orchestration and backend object lifecycle.
- Use `docs/digital/examples/tsim/magic_state_distillation.py` for detector/sampler-heavy QEC flows.
- Use `docs/digital/examples/interop/noisy_ghz.py` for noise-model pipeline behavior.
- Keep targeted search available: `rg -n "<symbol_or_keyword>" docs test src`.
