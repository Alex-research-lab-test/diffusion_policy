# Research project instructions

## Diffusion Policy test adoption

- This checkout is the public lab collaboration test. Its original source is
  `real-stanford/diffusion_policy`, baseline
  `5ba07ac6661db573af695b419a7947ecb704690f`. Preserve the upstream MIT license.
- This task adds governance files only. Existing uncommitted Franka adaptations
  and experiment data remain outside this test checkout and are not published.
- Do not run legacy `tests/` as a whole: camera/robot and data-writing scripts
  exist there. This adoption does not authorize training, evaluation or hardware.
- Keep the historical training stack unchanged. Collaboration tools use a
  separate Python 3.11+ environment; CI uses Python 3.12 without training packages.
- `origin` identifies the lab organization Fork; `upstream` is the official
  repository and has a disabled push URL. Never create PRs against upstream for
  this infrastructure rollout.

## Scope and evidence

- Read the task and applicable existing project instructions before editing.
  Preserve local changes, Git history, datasets, checkpoints and experiment logs.
- Before changing established architecture, interfaces, training or experiment
  procedures, search the available research knowledge base using targeted terms.
- For paper implementation, use the `research-reproduction` skill, primary
  sources and the paper-to-implementation map. Separate adaptations from claims
  of faithful reproduction. Never fabricate citations, results or successful runs.
- Infrastructure-only tasks must not modify core algorithms or training defaults.

## Verification and execution

- Inspect `.pre-commit-config.yaml` for the project's selected governance scope.
  Run `pre-commit run --all-files --show-diff-on-failure` and
  `python tools/lab/check_codex.py` using the collaboration tooling environment.
- Baseline collaboration checks do not prove algorithm correctness. For code
  changes, identify and execute the affected modules' suitable tests.
- Do not run the whole test directory without inspecting hardware/data effects.
  Do not run training, data conversion or hardware without the task's authorized
  procedure, inputs, output location and resource budget.
- Before publication, inspect explicitly staged paths and the diff. This test
  rollout requires confirmation before remote creation, pushes or access changes.

## Review

When independent review is requested, ask the parent to invoke project-native
`scientific_reviewer` for methodology/evidence and `code_reviewer` for code risks.
Give the base/head SHA and primary materials. Both return read-only findings;
they do not edit, run experiments or publish comments. Their permissions inherit
from the parent session; choose parent read-only permissions when required.

## Code Review Rules

- Flag changes to data splits, normalization, camera/state/action semantics or
  evaluation metrics that lack a documented rationale and supporting validation.
- Flag CI or scripts that access real hardware, mutate experiment data or execute
  PR code with privileged tokens. Prefer isolated CPU checks and synthetic inputs.
- Flag unsupported reproduction claims and AI/CI success claims without evidence
  covering the current head SHA. Mechanical formatting is checked in CI.
