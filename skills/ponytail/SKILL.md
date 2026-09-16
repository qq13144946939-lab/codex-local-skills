---
name: ponytail
description: Maintain existing code with small, safe changes. Use for bug fixes, small features, local refactors, or an explicitly requested simple implementation.
license: MIT
---

# Ponytail

Prefer the simplest implementation that satisfies the complete request. Apply this skill to maintenance and small changes within a suitable existing architecture. For new systems, security/database design, major migrations or refactors, or an architecture that causes the problem, evaluate requirements and alternatives first.

## Working approach

- Inspect relevant code and affected callers to understand the actual failure or requested behavior. Fix the root cause without turning every small edit into a whole-repository audit.
- Reuse existing patterns, standard-library features, native platform capabilities, and suitable installed dependencies before adding custom machinery.
- Avoid speculative features, unrelated rewrites, and abstractions without a concrete purpose. Choose clarity and correctness over the fewest lines or files.
- Deliver all requested behavior. Do not silently substitute a reduced version, reject a requirement as speculative, or leave a first draft when integration and verification remain.
- Preserve security checks, validation at trust boundaries, data-loss prevention, accessibility, error handling, and useful hardware calibration. Simplification must not remove these constraints.
- Add a `ponytail:` comment only when a deliberate tradeoff would otherwise be unclear; describe a real limitation and upgrade condition when useful.
- Use relevant existing checks. Add a focused regression test when it catches a meaningful failure; do not manufacture tests for every branch or require a new testing framework. Investigate failures caused by the change and stop repeating passing checks without a reason.

## Intensity and presentation

`/ponytail lite|full|ultra` selects how aggressively to question unnecessary implementation complexity. Default: **full**. Lite may mention a simpler alternative; full chooses the simplest complete solution; ultra challenges speculative complexity without dropping requested behavior or safeguards. Keep the selected level for applicable work until changed; `stop ponytail` or `normal mode` ends the mode.

Report the result, relevant checks, and any material limitations in the user's language. Scale detail to the task; no fixed line limit or mandatory code-first format. This skill does not control unrelated requests or communication style.
