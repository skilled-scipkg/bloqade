---
name: bloqade-api-and-scripting
description: This skill should be used when users ask about api and scripting in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: API and Scripting

## High-Signal Playbook

### Route conditions
- Use `bloqade-digital` for dialect semantics and compiler behavior questions.
- Use `bloqade-simulation-workflows` for backend/task lifecycle and shot-scaling decisions.
- Use `bloqade-build-and-install` when imports or extras fail before API usage.

### Canonical workflow
1. Start with API docs (`docs/reference/index.md`) to identify the expected symbol and namespace.
2. Pick one runnable behavior file from `references/source_map.md` before reasoning abstractly.
3. Run a minimal simulator smoke test:
```bash
python - <<'PY'
from bloqade import squin
from bloqade.pyqrack import StackMemorySimulator

@squin.kernel
def bell():
    q = squin.qalloc(2)
    squin.h(q[0])
    squin.cx(q[0], q[1])
    return squin.broadcast.measure(q)

print(StackMemorySimulator(min_qubits=2).run(bell, args=()))
PY
```
4. Run a minimal Cirq interop smoke test:
```bash
python - <<'PY'
import cirq
from bloqade.cirq_utils import load_circuit, emit_circuit

circuit = cirq.Circuit(cirq.H(cirq.LineQubit(0)))
kernel = load_circuit(circuit, kernel_name="h1", register_as_argument=False, return_register=True)
print(emit_circuit(kernel, ignore_returns=True))
PY
```
5. If behavior diverges from docs, inspect exact symbols with `rg` commands from `references/source_map.md`.

### Validation checkpoints
- Kernel execution works with explicit `args=(...)` and expected return type.
- Cirq round-trip (`load_circuit` then `emit_circuit`) returns a valid circuit object.
- Final guidance cites exact file paths used for function-level verification.

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/reference/index.md`
- `docs/digital/cirq_interop/cirq_to_squin.md`
- `docs/blog/posts/2025/the-noise-strikes-back.md`

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
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/qasm2/pauli_exponentiation.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
