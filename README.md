# PRAXO-CORE OCaml 0.11.0

Standalone Dune/opam source package generated from the canonical repository;
staging alone does not establish opam availability.
See `PROVENANCE.json` for the canonical tag reference, HEAD identity and
hashes of the actual worktree inputs. Worktree files can differ from HEAD
and the tag; a tag reference does not certify the packaged bytes.

## Build and Test

Requires OCaml >= 4.14 and Dune >= 3.0. Tests run in bytecode mode.
The `unix` library ships with OCaml;
it is not a separate opam dependency. Tests are offline and also require
Python 3 (`python` on PATH, or set `PYTHON` to its executable).

```sh
dune build -p praxo-core
dune runtest -p praxo-core
opam install . --with-test
```

To install from this local source directory without registry publication:

```sh
opam pin add praxo-core . --with-test
```

Use `(libraries praxo-core)` in a consumer's Dune library or executable.
The module is `Praxo_core` (the library is unwrapped). Callers supply
provider HTTP transports; no network client or credentials are bundled.

The packaged tests include both canonical test modules and all shared
vectors under `tests/spec/vectors`. `tests/tests/fixtures` preserves the
fixture path used by the unmodified tests when run from the Dune sandbox.
Package-local registry and llms files distinguish source availability from opam publication.

## References

- [Documentation](https://axisvela.github.io/praxo-core/languages/ocaml/)
- [Examples](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples)
- [API interface](https://github.com/axisvela/praxo-core/blob/main/language/ocaml/src/praxo_core.mli)
- [API snapshot](https://github.com/axisvela/praxo-core/blob/main/language/ocaml/api/0.11.0.txt)
- [Canonical source](https://github.com/axisvela/praxo-core/tree/main/language/ocaml)

Licensed under MIT; see `LICENSE`. See `CHANGELOG.md` for source changes.
