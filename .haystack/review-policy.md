# Review Policies

## Core slug algorithm changes
- **Paths**: `index.js`
- **Severity**: high
- **Reason**: Small regex or transformation-order changes can subtly alter slug output across many inputs, and AI cannot reliably validate semantic compatibility from tests alone.

## Transliteration and replacements data edits
- **Paths**: `replacements.js`, `overridable-replacements.js`
- **Severity**: high
- **Reason**: Character mapping changes can cause broad output regressions across languages and historical content that automated checks may not fully cover.

## Public API contract files
- **Paths**: `index.d.ts`, `readme.md`
- **Severity**: medium
- **Reason**: API contract drift between docs/types/runtime can ship confusing or incorrect integration guidance even when code passes CI.

## Instructions
- Require human judgment when a PR changes validation strictness (for example, allowing previously rejected inputs/options), since maintainers must decide whether compatibility benefits outweigh contract clarity and failure safety.
- Require human judgment when a PR adds new public options or extension hooks, to confirm the added API complexity is justified by real use cases.
- Require human judgment when regex changes alter separator, decamelization, or contraction behavior, because these edits can intentionally improve output or accidentally regress many edge cases.
