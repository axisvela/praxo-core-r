# PRAXO-CORE for R

R implementation of the PRAXO-CORE contract.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxocore` |
| Registry | [r-universe](https://axisvela.r-universe.dev/praxocore) |
| Install | `install.packages("praxocore", repos = "https://axisvela.r-universe.dev")` |
| Source version | `0.9.0` |
| Published version | `0.7.1` |
| Source tag | `r/v0.9.0` |
| Tier | Core |
| Contract | `SPEC_VERSION` `0.2.0` |
| Documentation | https://axisvela.github.io/praxo-core/languages/r/ |
| License | MIT |

## Highlights

- OpenAI-compatible model: native
- Anthropic model: native (transport seam)
- Gemini model: native (transport seam)
- MCP client: native (transport seam)
- Harmovela sink: native
- OpenTelemetry sink: native (transport seam)
- Subagent delegation: native (synchronous seam)
- Retriever: native

## Quick start

Install the published package:

```r
install.packages("praxocore", repos = "https://axisvela.r-universe.dev")
```

See the [full R README](language/r/README.md) for complete installation, build, and verification commands.

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| OpenAI-compatible model | native | `openai_compatible` adapter |
| Anthropic model | native (transport seam) | `anthropic`; caller may supply `transport` |
| Gemini model | native (transport seam) | `gemini`; caller may supply `transport` |
| MCP client | native (transport seam) | `mcp_client`; base R needs caller-supplied transport for stdio |
| Harmovela sink | native | `harmovela_sink` |
| OpenTelemetry sink | native (transport seam) | `otel_sink`; caller supplies OTLP/HTTP transport |
| Subagent delegation | native (synchronous seam) | `subagent_run`; no asynchronous manager |
| Retriever | native | `document`, `func_retriever`, `retriever_retrieve` |

## Examples

Runnable examples live under [`language/r/examples`](language/r/examples).

| Example | What it shows |
| --- | --- |
| [checkpoint](language/r/examples/checkpoint) | This example uses the R Core checkpoint allowlist to encode and decode only registered payload types. |
| [event-sink](language/r/examples/event-sink) | This example uses the R Core sink composition to fan out lifecycle and tool events and filter the tool-only stream. |
| [identity-policy](language/r/examples/identity-policy) | This example binds a trusted principal to policy decisions and rejects missing, inactive, role-mismatched, and tenant-mismatched actions. |
| [mcp](language/r/examples/mcp) | This example uses a caller-owned in-process transport with the R MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/r/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [retry](language/r/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/r/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any R HTTP server. |
| [streaming](language/r/examples/streaming) | This example forwards model deltas through the R Core and checks that the deltas reconstruct the final output. |
| [structured-output](language/r/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Verify

Run the checks from `language/r`:

```bat
Rscript r\conformance\run.R
Rscript r\api-snapshot.R --check
Rscript r\tests\run_tests.R
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/r/README.md`](language/r/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>

## Repository layout

- `language/r/` — implementation source, tests, API snapshot, and examples
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/r
- Registry introduction: `language/r/REGISTRY.md`
- Machine-readable entry: `language/r/llms.txt` and `language/r/llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-r
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical R source. The monorepo remains the source of truth and the release workflow source.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.
