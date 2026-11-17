# Contributing to Me and My Agents (MAMA)

This repository holds a **preliminary public specification**, not an implemented product.
Contributions are proposals for discussion and refinement of the conceptual model — thank you
for taking the time.

## What counts as "non-trivial"

- **Open an issue first** for anything that changes a core model definition or boundary —
  for example, proposing a new MAMA principle, or revising the authentication/authorisation
  distinction, the human decision/financial boundary, or the bilateral-permissions model.
  These deserve discussion before a PR is written.
- **Go straight to a pull request** for small, self-contained changes — wording fixes, typo
  corrections, clarifying an existing sentence, or adding/refining an illustrative example.

When in doubt, open an issue — it costs little and avoids wasted drafting effort.

## Keep the boundaries intact

When proposing or reviewing edits, make sure the change still:

- Preserves each owner's control of their own identity, information, relationships, and
  decisions — don't introduce language that implies an agent can act independently of its
  owner's consent.
- Keeps **authentication** (who is acting) and **authorisation** (what they may do)
  distinct — don't merge or blur these into a single concept.
- Keeps human decision and financial boundaries human-in-the-loop by default.
- Keeps permissions bilateral and independently revocable — avoid implying one party's grant
  creates an obligation on the other.

## Examples

Any example added to the specification must be clean and conceptual: illustrative scenarios
only, with no real people's private data, real organisations' internal details, or private
conversation content.

## Licensing

By contributing, you agree that your contribution to the specification/documentation text is
licensed under this repository's [CC BY 4.0 license](LICENSE). The repository's copyright
line names the project and its owning organisation collectively; individual contributors are
not added to the copyright line unless they explicitly request it in their pull request
description.

## How to propose a change

1. For non-trivial changes, open an issue describing the proposed change and why.
2. For small changes, open a pull request directly.
3. Keep PRs focused — one conceptual change or fix per PR, where practical.

No CLA, no issue templates beyond this guidance — keep it simple.
