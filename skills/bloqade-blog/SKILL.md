---
name: bloqade-blog
description: This skill should be used when users ask about blog in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Blog

## High-Signal Playbook

### Route conditions
- Keep this skill for extracting and validating claims made in Bloqade blog posts.
- Route to `bloqade-digital` or `bloqade-simulation-workflows` once the user asks to implement or debug the underlying workflow.

### Canonical workflow
1. Identify the specific claim and section in the post (`noise model`, `parallelism`, or `hybrid control-flow`).
2. Open the matching runnable source file from `references/source_map.md`.
3. Reproduce with compact commands:
```bash
python docs/digital/examples/interop/noisy_ghz.py
python docs/digital/examples/qasm2/repeat_until_success.py
```
4. For larger experiments, downscale qubits/shots first, then scale up after outputs look sane.
5. Tie conclusions back to exact post passages and exact code paths.

### Validation checkpoints
- Blog assertions are backed by a runnable example file.
- Reproduction run completes without import/signature errors.
- Reported metrics/trends (for example fidelity-depth tradeoffs) are directionally consistent.

## Scope
- Handle questions about documentation grouped under the 'blog' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/blog/index.md`
- `docs/blog/posts/2025/a-new-journey.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `docs/quick_start`
- `docs/digital/examples`
- `docs/digital/tutorials`

## Test references
- `test`

## Optional deeper inspection
- `src`

## Source entry points for unresolved issues
- `docs/blog/posts/2025/the-noise-strikes-back.md`
- `docs/blog/posts/2025/a-new-journey.md`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/digital/tutorials/auto_parallelism.py`
- `docs/digital/examples/qasm2/repeat_until_success.py`
- `docs/digital/examples/tsim/magic_state_distillation.py`
