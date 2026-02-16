# bloqade source map: Analog

Curated code-entry map for targeted analog behavior checks.
Use this map after exhausting `doc_map.md`.

## Topic query tokens
- `Honeycomb`
- `piecewise_linear`
- `interaction_picture=True`
- `batch_assign`
- `run_async`
- `bloqade.analog.migrate`

## Fast source navigation
- `rg -n "Honeycomb|Square|Chain|rydberg|piecewise_linear|batch_assign|run_async" docs/quick_start/analog/index.md docs/analog/home/quick_start.md docs/analog/home/geometry.md`
- `rg -n "interaction_picture|stiff|ode" docs/quick_start/analog/index.md docs/analog/home/quick_start.md`
- `rg -n "migrate|bloqade\\.analog\\.migrate" docs/analog/home/migration.md`

## Suggested source entry points
- `docs/quick_start/analog/index.md`
- `docs/analog/home/quick_start.md`
- `docs/analog/home/geometry.md`
- `docs/analog/reference/standard.md`
- `docs/analog/reference/hardware-capabilities.md`
- `docs/analog/home/migration.md`

## Validation checkpoints
- Geometry parameters and units are explicit before waveform construction.
- Waveforms satisfy start/end constraints before hardware submission.
- Migration commands are tested on at least one small JSON artifact copy.
