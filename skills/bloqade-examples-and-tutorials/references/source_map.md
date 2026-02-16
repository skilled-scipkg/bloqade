# bloqade source map: Examples and Tutorials

Curated runnable-entry map for example-first simulation checks.
Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `ghz_linear`
- `noisy_linear_ghz`
- `qasm2.extended`
- `parallelize`
- `compile_sampler`
- `compile_detector_sampler`

## Fast source navigation
- `rg -n "@squin\\.kernel|StackMemorySimulator|state_vector|depolarize" docs/digital/examples/squin docs/digital/tutorials/circuits_with_bloqade.py`
- `rg -n "qasm2\\.main|qasm2\\.extended|repeat_until_success|pauli_exponential|qaoa_" docs/digital/examples/qasm2`
- `rg -n "Gemini|transform_circuit|parallelize|compile_sampler|compile_detector_sampler" docs/digital/examples/interop docs/digital/examples/tsim docs/digital/tutorials/auto_parallelism.py`

## Suggested source entry points
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/squin/deutsch_squin.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/digital/examples/qasm2/qft.py`
- `docs/digital/examples/qasm2/pauli_exponentiation.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/tutorials/auto_parallelism.py`

## Validation checkpoints
- At least one SQUIN and one QASM2 example execute without import errors.
- Example outputs include either sampled results, emitted circuits, or plotted fidelity metrics.
- Parameterized examples run with explicit input values before larger sweeps.
