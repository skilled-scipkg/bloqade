# Evidence: bloqade-getting-started

## Primary docs
- `docs/index.md`
- `docs/analog/reference/overview.md`
- `docs/digital/dialects_and_kernels/squin.md`
- `docs/analog/home/migration.md`
- `docs/blog/posts/2023/bloqade-release.md`

## Primary source entry points
- `skills/bloqade-getting-started/references/doc_map.md`

## Extracted headings
- Installation
- Getting Started
- Contributing
- License
- Builder Overview
- this is strictly pseudocode
- note the dots!
- Syntax Motivations
- Visual Guides
- Structural Quantum Instructions dialect
- Squin overview
- Standard library for gate applications

## Executable command hints
- python -m bloqade.analog.migrate <path_to_old_json_file1> <path_to_old_json_file2> ...
- python -m bloqade.analog.migrate --help
- Python is one of the most widely used programming languages, especially in the quantum computing community and broader scientific communities. By extending Bloqade to Python, we are opening doors to a broader audience, enabling more developers, researchers, and organizations to harness the power of Neutral Atom quantum computing.

## Warnings and pitfalls
- !!! warning
- Bloqade is currently in the early stages of development. The APIs and features are subject to change. While we do not promise stability and backward compatibility at the moment, we will try to minimize breaking changes as much as possible. If you are concerned about the stability of the APIs, consider pin the version of Bloqade in your project.
- Note, that you could equivalently write the depolarization error in the above as
