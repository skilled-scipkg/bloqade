---
name: bloqade-developer-guide
description: This skill should be used when users ask about developer guide in bloqade; it prioritizes documentation references and then source inspection only for unresolved details.
---

# bloqade: Developer Guide

## High-Signal Playbook

### Route conditions
- Use `bloqade-build-and-install` if the blocker is environment setup, lint/test tooling, or docs build (`docs/install.md`, `docs/contrib.md`).
- Use `bloqade-digital`, `bloqade-analog`, or `bloqade-simulation-workflows` once the issue is narrowed to runtime behavior.
- Keep this skill for contribution channels, report quality, architecture orientation, and communication paths (`docs/analog/contributing/index.md`).

### Triage questions
- Is this a bug report, feature request, doc issue, feedback item, or general question?
- Can the user provide a minimal reproducible example?
- Are expected behavior and observed behavior explicitly separated?
- Which versions are involved (Bloqade, Python, OS)?
- Which area is impacted (analog, digital, simulator/task API, docs)?
- Is GitHub issue/discussion, Slack, or feedback form the right channel?

### Canonical workflow
1. Classify request type first: bug, feature, docs, discussion, or feedback (`docs/analog/contributing/index.md`).
2. For bugs/features, collect the required metadata (title, details, minimal example, versions) (`docs/analog/contributing/reporting-a-bug.md`, `docs/analog/contributing/feature-requests.md`).
3. For documentation issues, include exact page path and proposed correction (`docs/analog/contributing/documentation-issues.md`).
4. For architecture/context requests, summarize the compiler-stack model and AST/lowering terms (`docs/analog/contributing/design-philosophy-and-architecture.md`).
5. For broad product experience feedback, route to the feedback form (`docs/analog/contributing/providing-feedback.md`).
6. For open-ended Q&A, use GitHub Discussions; for community chat, use Slack (`docs/analog/contributing/asking-a-question.md`, `docs/analog/contributing/community-slack.md`).
7. If behavior cannot be explained from docs, jump to concrete examples/tests and then inspect source entry points.

### Minimal working example
```text
Title: <short descriptive title>
Area: <analog|digital|simulator|docs>
Expected behavior: <what should happen>
Actual behavior: <what happened>
Minimal repro (python): from bloqade import squin
Versions: bloqade=<...>, python=<...>, os=<...>
```

```python
from bloqade import squin
from bloqade.pyqrack import StackMemorySimulator

@squin.kernel
def repro():
    q = squin.qalloc(2)
    squin.h(q[0])
    squin.cx(q[0], q[1])
    return squin.broadcast.measure(q)

print(StackMemorySimulator(min_qubits=2).run(repro, args=()))
```

### Pitfalls and fixes
- Pitfall: issue filed without versions. Fix: always include Bloqade/Python/OS versions (`docs/analog/contributing/reporting-a-bug.md`).
- Pitfall: no reproducible snippet. Fix: reduce to minimal runnable kernel (`docs/analog/contributing/reporting-a-bug.md`).
- Pitfall: feature request states only outcome, not gap. Fix: include current workaround attempt and why it fails (`docs/analog/contributing/feature-requests.md`).
- Pitfall: doc issue is vague. Fix: include exact page link and concrete correction (`docs/analog/contributing/documentation-issues.md`).
- Pitfall: using issue tracker for open-ended help. Fix: route to Discussions/Slack (`docs/analog/contributing/asking-a-question.md`, `docs/analog/contributing/community-slack.md`).
- Pitfall: architecture feedback without context. Fix: anchor request in builder/AST/lowering model terms (`docs/analog/contributing/design-philosophy-and-architecture.md`).

### Convergence and validation checks
- Request has the right channel plus complete required metadata.
- Repro snippet runs locally (or fails deterministically) with explicit `args` signature where needed.
- Expected vs actual behavior is explicit and testable.
- Routing to downstream technical skill is clear once report quality is sufficient.

### Source-code entry links (behavior details)
- `docs/digital/tutorials/circuits_with_bloqade.py`
- `docs/digital/examples/interop/noisy_ghz.py`
- `docs/scripts/gen_ref_nav.py`
- `test/test_hello.py`
- `src/bloqade/README.md`

## Scope
- Handle questions about developer architecture, extension points, and contribution workflow.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/analog/contributing/index.md`
- `docs/background.md`
- `docs/analog/contributing/reporting-a-bug.md`
- `docs/analog/contributing/providing-feedback.md`
- `docs/analog/contributing/feature-requests.md`
- `docs/analog/contributing/documentation-issues.md`
- `docs/analog/contributing/community-slack.md`
- `docs/analog/contributing/asking-a-question.md`

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
- Use `docs/analog/contributing/reporting-a-bug.md` for required reproducibility metadata and issue quality gates.
- Use `docs/digital/tutorials/circuits_with_bloqade.py` for real task/device lifecycle examples.
- Use `docs/digital/examples/interop/noisy_ghz.py` when interop/noise-model behavior is relevant.
- Use `docs/digital/examples/squin/ghz.py` and `test/test_hello.py` for minimal runnable and test baselines.
- Keep targeted search available: `rg -n "<symbol_or_keyword>" docs test src`.
