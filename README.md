# PRAXO-CORE for OCaml

Native OCaml Core for the PRAXO-CORE agent framework. The main contract and
cross-language sources live in
[axisvela/praxo-core](https://github.com/axisvela/praxo-core).

- `SPEC_VERSION`: `0.2.0`
- Core version: `0.3.0`
- opam package: `praxo-core`
- Module: `Praxo_core`
- License: MIT

OCaml module identifiers cannot contain `-`; `Praxo-Core` is the package name,
and the importable module is `Praxo_core`.

## Install

```bash
opam install praxo-core
```

## API

```ocaml
let node = Praxo_core.parse_json "{\"name\":\"echo\",\"input\":{\"text\":\"hi\"}}"
let raw = Praxo_core.encode_json node
let _call = Praxo_core.parse_tool_call raw
let _paths = Praxo_core.validate_schema (Praxo_core.parse_json "{\"type\":\"string\"}") node
let _manifest = Praxo_core.validate_manifest "{}"
```

## Scope

The Core implements all eleven conformance vector groups: toolcall, JSON Schema,
plugin, memory, event, stream, checkpoint, policy, context, middleware, and the
agent loop. It includes native agent execution, memory, checkpoints, lexical
path policy, context compaction, event sinks, middleware helpers, and tool
selection.

The Core does not call Go or another language runtime. Provider adapters,
process bridges, and plugin hosts are outside the declared Core scope.
Verified with OCaml 4.14.2 bytecode; native `ocamlopt` is not claimed.

## Links

- Main repository: https://github.com/axisvela/praxo-core
- OCaml documentation: https://axisvela.github.io/praxo-core/languages/ocaml/
