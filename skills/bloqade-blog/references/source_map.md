# bloqade source map: Blog

Curated blog-to-code map for reproducible simulation checks.
Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `GeminiOneZoneNoiseModel`
- `GeminiTwoZoneNoiseModel`
- `transform_circuit`
- `parallelize`
- `repeat-until-success`
- `magic state distillation`

## Fast source navigation
- `rg -n "GeminiOneZoneNoiseModel|GeminiTwoZoneNoiseModel|transform_circuit|fidelity" docs/blog/posts/2025/the-noise-strikes-back.md docs/digital/examples/interop/noisy_ghz.py`
- `rg -n "parallelize|log-depth|GHZ|Steane|QAOA" docs/digital/tutorials/auto_parallelism.py`
- `rg -n "repeat_until_success|qasm2\\.extended|compile_detector_sampler" docs/blog/posts/2025/a-new-journey.md docs/digital/examples/qasm2/repeat_until_success.py docs/digital/examples/tsim/magic_state_distillation.py`

## Suggested source entry points
- `docs/blog/posts/2025/the-noise-strikes-back.md`
- `docs/blog/posts/2025/a-new-journey.md`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/tutorials/auto_parallelism.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`

## Validation checkpoints
- Every blog claim is traceable to at least one runnable example file.
- Noise-model reproductions run with small qubit counts before scaling.
- Control-flow and QEC examples emit or sample without signature/import errors.
