# bloqade source map: Getting Started

Curated code-entry map for first-run simulation checks.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `@squin.kernel`
- `sim.run`
- `args=`
- `bloqade.analog.migrate`
- `state_vector`
- `StackMemorySimulator`

## Fast source navigation
- `rg -n "@squin\\.kernel|sim\\.run|state_vector|args=" docs/quick_start/circuits/index.md docs/digital/examples/squin/ghz.py docs/digital/tutorials/circuits_with_bloqade.py`
- `rg -n "bloqade\\.analog\\.migrate|from bloqade\\.analog" docs/analog/home/migration.md docs/quick_start/analog/index.md`
- `rg -n "piecewise_linear|run_async|interaction_picture|batch_assign" docs/quick_start/analog/index.md docs/analog/home/quick_start.md`

## Suggested source entry points
- `docs/quick_start/circuits/index.md`
- `docs/quick_start/analog/index.md`
- `docs/digital/examples/squin/ghz.py`
- `docs/digital/examples/qasm2/ghz.py`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/analog/home/migration.md`
- `test/test_hello.py`

## Validation checkpoints
- First digital kernel run succeeds with explicit `args`.
- At least one analog quick-start snippet is adapted with concrete numeric inputs.
- Migration command paths are validated before modifying legacy JSON files.
