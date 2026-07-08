# Fork CI Mirror — Coverage vs. Gaps

This fork mirrors a CPU-feasible subset of vllm-project/vllm's real CI so
changes can be validated here before being proposed upstream.

## Mirrored (`fork-ci-mirror-fast.yml`)

- `pre-commit` hooks (ruff, mypy, formatting, shellcheck, actionlint,
  markdownlint) — same hook set as upstream's `pre-commit.yml`, run on
  GitHub-hosted `ubuntu-latest` instead of vLLM's `self-hosted, vllm-runners`
  pool.

## Not mirrored (permanent gap)

- Buildkite GPU test suite (`.buildkite/`) — requires CUDA hardware and
  vLLM-internal Buildkite infra, neither of which this fork has access to.
- The upstream `pre-run-check` label/merge-count gate — an anti-abuse check
  scoped to `vllm-project/vllm`'s own PR history; meaningless on a personal
  fork and dropped here.

Triggering: opens/pushes to a PR run it automatically. On subsequent PRs,
once this workflow exists on the fork's default branch, a `/run-ci-mirror`
comment re-triggers it.
