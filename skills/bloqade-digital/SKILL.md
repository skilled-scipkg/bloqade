---
name: bloqade-digital
description: This skill should be used when users ask about digital in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Digital

## High-Signal Playbook

### Route conditions
- Use `bloqade-simulation-workflows` for backend/task execution strategy and shot-scaling guidance.
- Use `bloqade-build-and-install` when blockers are extras/dependencies (`qasm2`, `stim`, etc.) (`docs/digital/index.md`, `docs/install.md`).
- Use `bloqade-api-and-scripting` for API-reference-first scripting questions.
- Use `bloqade-developer-guide` for reporting limitations/bugs after a minimal repro is produced.

### Triage questions
- Which dialect is needed: `squin`, `qasm2`, or `stim`?
- Do you need control flow or strict QASM2 compatibility?
- Is Cirq interop required (`cirq -> squin`, `squin -> cirq`, or both)?
- Are you targeting plain simulation, noise modeling, or QEC sampling workflows?
- Are custom qubit types/ordering requirements involved?
- Is the issue in kernel authoring, lowering/IR, or backend execution?

### Canonical workflow
1. Choose dialect by use case (general/control-flow: SQUIN; strict assembly compatibility: QASM2; stabilizer/QEC: STIM) (`docs/digital/dialects_and_kernels/index.md`).
2. Define kernel with correct decorator and inspect IR early (`docs/digital/dialects_and_kernels/squin.md`, `docs/digital/dialects_and_kernels/stim.md`).
3. If interoperability is needed, convert using `cirq_utils` functions and verify round-trip assumptions (`docs/digital/cirq_interop/index.md`, `docs/digital/cirq_interop/squin_to_cirq.md`).
4. Run on local simulator/task backend with explicit `args` tuple (`docs/digital/simulator_device/simulator_device.md`, `docs/digital/simulator_device/tasks.md`).
5. For high-shot workflows, move to TSIM/STIM samplers (`docs/quick_start/circuits/index.md`).
6. For strict QASM2 emission paths, keep constructs compatible with mode limits (`docs/digital/compilation.md`).
7. Escalate to concrete example files and then source-entry links if docs are insufficient.

### Minimal working example
```python
from bloqade import squin
from bloqade.pyqrack import StackMemorySimulator

@squin.kernel
def main():
    q = squin.qalloc(2)
    squin.h(q[0])
    squin.cx(q[0], q[1])
    return squin.broadcast.measure(q)

sim = StackMemorySimulator(min_qubits=2)
print(sim.run(main, args=()))
```

```python
from bloqade import squin, cirq_utils

@squin.kernel
def bell():
    q = squin.qalloc(2)
    squin.h(q[0])
    squin.cx(q[0], q[1])

print(cirq_utils.emit_circuit(bell))
```

### Pitfalls and fixes
- Pitfall: treating kernel body as standard Python execution. Fix: run through dialect backend (`docs/digital/dialects_and_kernels/index.md`).
- Pitfall: direct kernel invocation instead of backend run. Fix: use device/task APIs (`docs/digital/simulator_device/tasks.md`).
- Pitfall: Cirq emission from control-flow-heavy kernels. Fix: simplify kernel or avoid unsupported control-flow patterns (`docs/digital/cirq_interop/squin_to_cirq.md`).
- Pitfall: passing too few custom qubits to emit function. Fix: provide sufficient qubit list length (`docs/digital/cirq_interop/squin_to_cirq.md`).
- Pitfall: assuming all QASM2 constructs map to strict standard mode. Fix: separate `qasm2.main`/`qasm2.gate` expectations from extended mode (`docs/digital/compilation.md`).
- Pitfall: relying on immature compiler-pass UX in early debugging. Fix: skip optimization stage initially (`docs/quick_start/circuits/index.md`, `docs/digital/compilation.md`).

### Convergence and validation checks
- IR printout matches intended gate/control-flow structure.
- Simulator run works with explicit `args` and expected result type.
- If Cirq interop is used, emitted circuit semantics are validated on a tiny example.
- For sampler workflows, shot throughput and detector/observable outputs are consistent with chosen sampler type.

### Source-code entry links (behavior details)
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`

## Scope
- Handle questions about documentation grouped under the 'digital' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/digital/dialects_and_kernels/index.md`
- `docs/digital/cirq_interop/index.md`
- `docs/digital/cirq_interop/squin_to_cirq.md`
- `docs/digital/dialects_and_kernels/stim.md`

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
- Use `docs/digital/examples/squin/ghz.py` for baseline kernel + simulator patterns.
- Use `docs/digital/examples/qasm2/repeat_until_success.py` for control-flow-heavy QASM2 kernels.
- Use `docs/digital/examples/interop/noisy_ghz.py` for Cirq + noise-model pipelines.
- Use `docs/digital/examples/tsim/magic_state_distillation.py` for detector/sampler QEC workflows.
- Use `docs/digital/tutorials/circuits_with_bloqade.py` for broader end-to-end orchestration patterns.
