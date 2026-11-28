# PRAXO-CORE for OCaml

PRAXO-CORE is an embeddable, MIT-licensed AI agent framework. This package is its native OCaml Core with source tag `ocaml/v0.11.1`. It passes all eleven vector groups on OCaml 4.14.2 bytecode and includes the native agent loop, memory store, checkpoint allowlist, lexical path policy, context compaction, event sinks, middleware helpers, tool selection, streaming OpenAI-compatible, Anthropic, and Gemini model adapters, and an optional process plugin host. It does not call Go or another language Core and has no cross-language process bridge.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo-core` |
| Registry | [opam (pending)](https://github.com/axisvela/praxo-core-ocaml) |
| Build | Source checkout: language/ocaml (see README build instructions) |
| Source version | `0.11.1` |
| Published version | not published |
| Publication status | not published; replacement submission pending |
| Canonical source tag | [`ocaml/v0.11.1`](https://github.com/axisvela/praxo-core/tree/ocaml/v0.11.1) |
| Tier | Core |
| Contract | `SPEC_VERSION` `0.2.0` |
| Documentation | https://axisvela.github.io/praxo-core/languages/ocaml/ |
| License | MIT |

## Highlights

- OpenAI-compatible model: native (transport seam)
- Anthropic model: native (transport seam)
- Gemini model: native (transport seam)
- MCP client: native (transport seam)
- Process plugin host: native (JSON Lines)
- Harmovela sink: native (transport seam)
- OpenTelemetry sink: native (transport seam)
- Subagent delegation: native (synchronous seam)
- Retriever: native

## Quick start

No published package is available. Follow the source build instructions in [`language/ocaml/README.md`](https://github.com/axisvela/praxo-core/blob/main/language/ocaml/README.md).

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| OpenAI-compatible model | native (transport seam) | Caller supplies `transport`; no bundled HTTP client; SSE streaming reassembly |
| Anthropic model | native (transport seam) | `anthropic_model`; caller supplies transport; `anthropic_generate_stream` reassembles Anthropic SSE |
| Gemini model | native (transport seam) | `gemini_model`; caller supplies transport; `gemini_generate_stream` reassembles Gemini SSE |
| MCP client | native (transport seam) | `mcp_client`; caller supplies transport |
| Process plugin host | native (JSON Lines) | `start_plugin_process`, `invoke_plugin_process`, `stop_plugin_process`; caller owns the executable |
| Harmovela sink | native (transport seam) | `harmovela_sink`; caller supplies transport |
| OpenTelemetry sink | native (transport seam) | `otel_sink_new` and `otel_emit`; caller supplies OTLP/HTTP transport |
| Subagent delegation | native (synchronous seam) | `subagent_run`; no asynchronous manager |
| Retriever | native | `document` and `retrieve_documents` |

## Examples

Runnable examples live under [`language/ocaml/examples`](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples).

| Example | What it shows |
| --- | --- |
| [advanced-delegation](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/advanced-delegation) | Application-level parent/child delegation plus six governance negative checks. |
| [checkpoint](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/checkpoint) | This example uses the OCaml Core checkpoint allowlist for a registered payload round trip. |
| [consumer](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/consumer) | This starter uses the repository OCaml Core with a deterministic model. It does not require a network connection, credentials, or a model service. |
| [event-sink](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/event-sink) | This example uses OCaml Core sink composition to fan out events and filter the tool-only stream. |
| [hitl](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [identity-policy](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/identity-policy) | This example binds a trusted principal to policy decisions and rejects missing, role-mismatched, and tenant-mismatched actions. |
| [live-model](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/live-model) | This example wires the OCaml Core OpenAI-compatible adapter (`openai_model`) to `PRAXO_BASE_URL`, registers a low-risk `get_time` tool, and restricts the run to `get_time` with... |
| [mcp](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/mcp) | This example uses a caller-owned in-process transport with the OCaml MCP client. |
| [provider-fallback](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [representative-chain](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/representative-chain) | Deterministic representative chain covering MCP record, final-argument authorization, governed child delegation, OTel/Harmovela events, and an edited denial with zero effects. |
| [retry](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/service) | This example defines a transport-neutral request handler with health, principal, and run cases. |
| [session-checkpoint](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/session-checkpoint) | This example saves and restores a conversation history across two agent turns. It uses `session`, `run_agent`, `message_wire`, and the Core checkpoint allowlist with a teaching... |
| [streaming](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/streaming) | This example accumulates streamed chunks and checks that they reconstruct the final output. |
| [structured-output](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Scenario Tutorials

Scenario-oriented tutorials live under `language/ocaml/Tutorial`. Planning context: [Tutorial Plan](https://axisvela.github.io/praxo-core/getting-started/tutorial-plan/), [100 candidate agent scenarios](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), and [Tutorial Catalog](https://axisvela.github.io/praxo-core/getting-started/tutorial-catalog/).

| Path | What it shows |
| --- | --- |
| [Tutorial](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/Tutorial) | ﻿# OCaml Tutorials |
| [architecture-graph](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/Tutorial/architecture-graph) | A bounded first slice of OG-01, not an enterprise-architecture control plane. It compares a fixed application/API graph with stated standards and drafts review-only change findi... |
| [bom-review](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/Tutorial/bom-review) | A bounded first slice of [IN-05](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), not CAD/BIM parsing or engineering certification. It reads a fixed parsed drawing, reports one clearance conflict, and drafts a review-only BOM. No CAD access or live model. |
| [code-review](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/Tutorial/code-review) | A bounded first slice of [SE-05](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), not a full security or license audit. It reads a fixed diff and dependency manifest, flags a high-severity unsafe-shell rule and a missing test, and drafts a review-only comment set. This uses the source OCaml Core through the `ocaml` toplevel; no network, credentials or packages beyond OCaml are required. |
| [contract-review](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/Tutorial/contract-review) | A bounded first slice of [FC-05](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), not legal advice or an e-signature system. It compares fixed contract clauses to a redline set and drafts review-only redlines. No document store or live model. |
| [static-diagnostics](https://github.com/axisvela/praxo-core/tree/main/language/ocaml/Tutorial/static-diagnostics) | A bounded static-analysis review tutorial. It parses structured diagnostic lines, counts high/low rules and returns source locations. Core chooses a review level from the actual... |

## Reference Applications

No accepted end-to-end reference application is recorded for this language yet. Candidate goals are tracked in the [Reference Application Portfolio](https://axisvela.github.io/praxo-core/project/roadmap/#reference-application-portfolio).

## Verify

Run the checks from `language/ocaml`:

```bash
python language/ocaml/run-tests.py
python language/ocaml/api-snapshot.py --check
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/ocaml/README.md`](https://github.com/axisvela/praxo-core/blob/main/language/ocaml/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>
- LinkedIn: <https://www.linkedin.com/company/axisvela/>
- Facebook: <https://www.facebook.com/profile.php?id=61596905732406>
- YouTube: <https://www.youtube.com/@axisvela>
- Discord: <https://discord.com/channels/1575163993767809064/1575164343148875977>
- GitHub Discussions: <https://github.com/axisvela/praxo-core/discussions>
- GitHub Issues: <https://github.com/axisvela/praxo-core/issues>
- Documentation: <https://axisvela.github.io/praxo-core/>
- Architect: <https://axisvela.architect.pub>

## Repository layout

- `language/ocaml/` — implementation source, tests, API snapshot, and examples
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/ocaml
- Registry introduction: `language/ocaml/REGISTRY.md`
- Machine-readable entry: `language/ocaml/llms.txt` and `language/ocaml/llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-ocaml
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical OCaml source. The monorepo remains the source of truth and the release workflow source. The mirror's `main` branch tracks current source, not a release snapshot. Source tags refer to the canonical monorepo and are not necessarily present in this mirror; syncing the branch does not publish mirror tags or registry packages.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.
