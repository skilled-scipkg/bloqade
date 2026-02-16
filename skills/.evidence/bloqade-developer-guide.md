# Evidence: bloqade-developer-guide

## Primary docs
- `docs/analog/contributing/index.md`
- `docs/background.md`
- `docs/analog/contributing/reporting-a-bug.md`
- `docs/analog/contributing/providing-feedback.md`
- `docs/analog/contributing/feature-requests.md`
- `docs/analog/contributing/documentation-issues.md`
- `docs/analog/contributing/community-slack.md`
- `docs/analog/contributing/asking-a-question.md`

## Primary source entry points
- `skills/bloqade-developer-guide/references/doc_map.md`

## Extracted headings
- Contributing
- Table of Contents
- Background
- Neutral Atom Qubits
- Analog mode Quantum Computing
- Digital Mode
- Reconfigurable architectures and "all to all" connectivity
- Reporting a Bug
- Providing Feedback
- Requesting new Features
- Reporting a Documentation Issue
- Community Slack

## Executable command hints
- $$

## Warnings and pitfalls
- A unique advantage of reconfigurable neutral atom architectures is parallelism: the same laser can effect many lasers by aiming it in the same plane as the atom array. A single global Raman laser can enact the same parallel single-qubit gate on all qubits at the same time, and a single Rydberg laser (technically, two counter-propagating) can enact the same parallel multi-qubit gate on all cliques of qubits in an entangling region of the array. For more details see this paper on a [recent demonstration of reconfigurable architectures](https://www.nature.com/articles/s41586-023-06927-3). For this reason, it is important to represent quantum executions and circuits to be as parallel as possible. In our qasm2 dialect, we have extended qasm to natively include parallelism-- for example, `qasm2.parallel.cx(controls, targets)` represents a parallel CNOT gate between a list of `controls` on a list of `targets`.
- improve the stability of Bloqade. As such, we encourage
