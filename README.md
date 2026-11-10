# PRAXO-CORE for R

Dedicated repository for the R implementation of PRAXO-CORE: an embeddable,
MIT-licensed agent execution kernel with policy controls, human-in-the-loop
approval, checkpoints, events, and tool calling.

- Package: `praxocore` on r-universe (CRAN is not published)
- Documentation: https://axisvela.github.io/praxo-core/languages/r/
- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/r
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical R source. The monorepo
remains the source of truth and the release workflow source. Shared conformance
vectors are included under `spec/`.

## Install

```r
install.packages("praxocore", repos = "https://axisvela.r-universe.dev")
```

## Verify

From `language/r`:

```sh
Rscript conformance/run.R
Rscript tests/run_tests.R
Rscript api-snapshot.R --check
```

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety
controller. Do not infer exactly-once execution, complete sandbox isolation,
production security certification, live-provider behavior, or physical safety
from this package.

MIT licensed.
