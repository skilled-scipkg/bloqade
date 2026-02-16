# bloqade source map: Build and Install

Curated code-entry map for targeted environment and smoke-test checks.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `pip install bloqade`
- `uv sync`
- `pre-commit install`
- `StackMemorySimulator`
- `@squin.kernel`
- `run_async`

## Fast source navigation
- `rg -n "pip install|uv sync|pre-commit|pytest|just doc-build" docs/install.md docs/contrib.md`
- `rg -n "StackMemorySimulator|@squin\\.kernel|sim\\.run|state_vector" docs/quick_start/circuits/index.md docs/digital/examples/squin/ghz.py`
- `rg -n "run_async|interaction_picture|piecewise_linear" docs/quick_start/analog/index.md docs/analog/home/quick_start.md`

## Suggested source entry points
- `docs/quick_start/circuits/index.md`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/quick_start/analog/index.md`
- `test/test_hello.py`

## Validation checkpoints
- Install commands complete and imports succeed for selected extras.
- At least one digital kernel runs on local simulator with explicit `args`.
- Project smoke test (`pytest`) runs without collection/import failures.
