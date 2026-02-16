# bloqade source map: Digital

Curated code-entry map for targeted digital behavior checks.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `@squin.kernel`
- `qasm2.extended`
- `cirq_utils.emit_circuit`
- `load_circuit`
- `compile_sampler`
- `depolarize`

## Fast source navigation
- `rg -n "@squin\\.kernel|qasm2\\.extended|stim\\.main" docs/digital`
- `rg -n "emit_circuit|load_circuit|cirq|noise\\.transform_circuit" docs/digital/cirq_interop docs/digital/examples docs/digital/tutorials`
- `rg -n "compile_sampler|compile_detector_sampler|set_detector|set_observable" docs/digital/examples docs/quick_start/circuits/index.md`

## Suggested source entry points
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/squin/deutsch_squin.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`

## Validation checkpoints
- Kernel IR and emitted circuits match intended gate/control-flow structure.
- Simulator runs succeed with explicit `args` tuples.
- Sampler workflows return non-empty outputs for small shot counts.
