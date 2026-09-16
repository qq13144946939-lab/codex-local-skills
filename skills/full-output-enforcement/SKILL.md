---
name: full-output-enforcement
description: Deliver complete files or exhaustive multi-part content when the user requests unabridged output. Prevent placeholders from replacing requested content and preserve progress across long deliverables.
---

# Full-Output Enforcement

## Baseline

Complete the content the user requested. If the user asks for a full file, deliver the full file; if they ask for 5 components, deliver 5 components. Keep explanations concise when appropriate. A complete file saved to the workspace can be delivered with a link and a short summary unless the user requested its contents inline.

## Banned Output Patterns

Do not use the following patterns to stand in for requested implementation or content. Preserve legitimate language syntax, quoted source, and user-requested illustrative snippets.

**In code blocks:** `// ...`, `// rest of code`, `// implement here`, `// TODO`, `/* ... */`, `// similar to above`, `// continue pattern`, `// add more as needed`, bare `...` standing in for omitted code

**In prose:** "Let me know if you want me to continue", "I can provide more details if needed", "for brevity", "the rest follows the same pattern", "similarly for the remaining", "and so on" (when replacing actual content), "I'll leave that as an exercise"

**Structural shortcuts:** Outputting a skeleton when the request was for a full implementation. Showing the first and last section while skipping the middle. Replacing repeated logic with one example and a description. Describing what code should do instead of writing it.

## Execution Process

1. **Scope** — Identify the requested deliverables and adjust them when the user changes the request.
2. **Build** — Complete each requested deliverable. Drafts are appropriate when the user requests a draft.
3. **Cross-check** — Before output, re-read the original request. Compare your deliverable count against the scope count. If anything is missing, add it before responding.

## Handling Long Outputs

For long deliverables, write complete local files when that fits the request, verify them, and link to them. Do not deliberately stop authorized work merely to ask for "continue". If an actual tool or context limit prevents completion, state what is complete and record the exact remaining work and restart point without claiming success. Respect a user's request for inline output or staged delivery.

## Quick Check

Before delivering exhaustive content, verify:
- No placeholder replaces requested content
- Every item the user requested is present and finished
- Code blocks contain actual runnable code, not descriptions of what code would do
- Concise explanations have not removed a requested deliverable
