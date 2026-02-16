# bloqade source map: Inputs and Modeling

Curated modeling-entry map for parameterization and physical input checks.
Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `Honeycomb`
- `lattice_spacing`
- `piecewise_linear`
- `batch_assign`
- `get capabilities`
- `pauli_exponential`

## Fast source navigation
- `rg -n "Honeycomb|Square|Chain|lattice_spacing|piecewise_linear|batch_assign|run_async" docs/quick_start/analog/index.md docs/analog/home/quick_start.md docs/analog/home/geometry.md`
- `rg -n "Hardware Capabilities|Programmatic Access|Aquila|capabilities" docs/analog/reference/hardware-capabilities.md`
- `rg -n "pauli_exponential|zzzz_gadget|pauli_basis_change|qaoa_" docs/digital/examples/qasm2/pauli_exponentiation.py docs/digital/examples/qasm2/qaoa.py`

## Suggested source entry points
- `docs/quick_start/analog/index.md`
- `docs/analog/home/quick_start.md`
- `docs/analog/home/geometry.md`
- `docs/analog/reference/hardware-capabilities.md`
- `docs/digital/examples/qasm2/pauli_exponentiation.py`
- `docs/digital/examples/qasm2/qaoa.py`

## Validation checkpoints
- Geometry and waveform parameters are explicitly set before execution.
- Hardware-capability constraints are checked before choosing durations/frequencies.
- Modeling examples are run with small, fixed parameters before parameter sweeps.
