# Evidence: bloqade-digital

## Primary docs
- `docs/digital/dialects_and_kernels/index.md`
- `docs/digital/cirq_interop/index.md`
- `docs/digital/cirq_interop/squin_to_cirq.md`
- `docs/digital/dialects_and_kernels/stim.md`

## Primary source entry points
- `skills/bloqade-digital/references/doc_map.md`

## Extracted headings
- Dialects and kernels
- Available dialects
- [squin](./squin.md)
- [qasm2](./qasm2.md)
- [stim](./stim.md)
- Interoperability with cirq
- TL;DR
- Converting squin to Cirq
- Basic usage
- Customizing qubits
- Limitations
- Stim

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- !!! warning "Note"
- It is important to understand that when you are writing a kernel function in a dialect you are generally **not writing Python** code, even though it looks a lot like it.
- Think of this as trying to execute another programming language with the Python interpreter: of course, that will error.
- For quantum error correction applications, you may want to use this dialect.
- * Quantum error correction.
- !!! warning
- [Stim](https://github.com/quantumlib/Stim) is a library for simulating and analyzing quantum stabilizer codes and quantum error correction circuits.
