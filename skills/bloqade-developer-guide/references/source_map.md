# bloqade source map: Developer Guide

Curated code-entry map for bug-repro and contribution-quality checks.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `minimal reproducible`
- `expected behavior`
- `actual behavior`
- `sim.task`
- `task.run`
- `version`

## Fast source navigation
- `rg -n "Title:|Expected behavior|Actual behavior|Versions|minimal" docs/analog/contributing/reporting-a-bug.md docs/analog/contributing/feature-requests.md`
- `rg -n "sim\\.task|task\\.run|StackMemorySimulator|state_vector" docs/digital/tutorials/circuits_with_bloqade.py docs/quick_start/circuits/index.md`
- `rg -n "def test_|assert" test`

## Suggested source entry points
- `docs/analog/contributing/reporting-a-bug.md`
- `docs/analog/contributing/feature-requests.md`
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/examples/squin/ghz.py`
- `test/test_hello.py`

## Validation checkpoints
- Reproduction snippets include runnable code and exact version metadata.
- Reported behavior can be replayed with one of the listed tutorial/example files.
- At least one targeted test or assertion path is identified for regression coverage.
