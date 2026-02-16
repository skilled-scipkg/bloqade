# bloqade source map: API and Scripting

Curated code-entry map for targeted API behavior checks.
Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `@squin.kernel`
- `load_circuit`
- `emit_circuit`
- `transpile`
- `noise.transform_circuit`
- `compile_sampler`
- `compile_detector_sampler`

## Fast source navigation
- `rg -n "@squin\\.kernel|StackMemorySimulator|state_vector|task\\(" docs/digital/tutorials/circuits_with_bloqade.py docs/digital/examples/squin/ghz.py`
- `rg -n "load_circuit|emit_circuit|transpile|parallelize|noise\\.transform_circuit" docs/digital/tutorials docs/digital/examples/interop`
- `rg -n "qasm2\\.extended|compile_sampler|compile_detector_sampler" docs/digital/examples/qasm2 docs/digital/examples/tsim`

## Suggested source entry points
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/qasm2/pauli_exponentiation.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`

## Validation checkpoints
- `StackMemorySimulator(...).run(kernel, args=(...))` returns without signature errors.
- `load_circuit` and `emit_circuit` round-trip produces a valid Cirq circuit object.
- `compile_sampler` or `compile_detector_sampler` can sample with small shot counts.
