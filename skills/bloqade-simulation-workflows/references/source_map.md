# bloqade source map: Simulation Workflows

Curated code-entry map for targeted runtime and sampling checks.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `StackMemorySimulator`
- `sim.task`
- `task.run`
- `state_vector`
- `compile_sampler`
- `compile_detector_sampler`

## Fast source navigation
- `rg -n "StackMemorySimulator|sim\\.task|task\\.run|state_vector|args=" docs/quick_start/circuits/index.md docs/digital/tutorials/circuits_with_bloqade.py docs/digital/examples/squin/ghz.py`
- `rg -n "compile_sampler|compile_detector_sampler|set_detector|set_observable" docs/quick_start/circuits/index.md docs/digital/examples/tsim/magic_state_distillation.py`
- `rg -n "Gemini|transform_circuit|DensityMatrixSimulator" docs/digital/examples/interop/noisy_ghz.py`

## Suggested source entry points
- `docs/quick_start/circuits/index.md`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/simulator_device/tasks.md`
- `test/test_hello.py`

## Validation checkpoints
- Both direct `run` and explicit `task.run()` paths work for a tiny kernel.
- Sampler and detector-sampler outputs are non-empty for small shot counts.
- State-vector or density-matrix diagnostics match expected correlations.
