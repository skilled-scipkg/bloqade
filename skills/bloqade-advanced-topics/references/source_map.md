# bloqade source map: Advanced Topics

Curated code-entry map for merged single-doc topics.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `report.show`
- `visualization`
- `parallelize`
- `GeminiOneZoneNoiseModel`
- `compile_detector_sampler`
- `hardware-oriented programming`

## Fast source navigation
- `rg -n "report\\.show|visualize|visualization" docs/quick_start/analog/index.md docs/analog/home/visualization.md`
- `rg -n "GeminiOneZoneNoiseModel|transform_circuit|fidelity" docs/digital/examples/interop/noisy_ghz.py docs/digital/tutorials/auto_parallelism.py`
- `rg -n "compile_sampler|compile_detector_sampler|set_detector|set_observable" docs/digital/examples/tsim/magic_state_distillation.py`

## Suggested source entry points
- `docs/quick_start/analog/index.md`
- `docs/digital/tutorials/auto_parallelism.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`

## Validation checkpoints
- Visualization/report examples identify explicit plotting or report API calls.
- Noise-model examples run at least one small-qubit case without import errors.
- Detector/sampler paths produce non-empty samples for small shot counts.
