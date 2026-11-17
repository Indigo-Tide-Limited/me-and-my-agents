# Me and My Agents (MAMA)

**Me and My Agents (MAMA)** is a proposed, human-centred model for how people — and the
software agents acting on their behalf — can meet, recognise each other, and collaborate
across ownership and organisation boundaries, while each person (or organisation) keeps
control of their own identity, information, relationships, and decisions.

> **Status: preliminary public definition.** MAMA is not an established standard, not an
> implemented platform, and this document does not represent agreement from any
> other named third party. It is a starting point for public discussion and refinement.

## Why this exists

As more people delegate day-to-day tasks to software agents, those agents increasingly need
to interact with *other people's* agents — to schedule something, share a document, request
a quote, or coordinate a plan. MAMA describes the boundaries that should hold in that
situation, so that delegation to an agent never means losing control over who you are, what
you share, who you're connected to, or what gets decided in your name.

## Relationships

A relationship in MAMA is an explicit, bounded connection between two owners (people or
organisations), established through their agents. A relationship is scoped to a purpose and a
set of permissions — it is not a blanket link that exposes everything either party has.
Owners can have many relationships, each with its own boundaries, and nothing about one
relationship is implied by another.

## Selective Sharing

Owners choose what information is exposed, to whom, and in what context. Sharing is scoped
per relationship, not global: information shared with one counterparty is not automatically
visible to another, and an owner can share different things with different relationships
without those relationships being aware of each other.

## Authentication vs Authorisation

MAMA treats these as two distinct, separable concerns:

- **Authentication** answers "who (or which agent, acting for whom) is this?" — proving the
  identity of the acting agent and the owner it represents.
- **Authorisation** answers "what is this authenticated agent allowed to do, on whose
  behalf?" — the specific permissions granted for a specific relationship or action.

An agent being successfully authenticated says nothing about what it is authorised to do.
Authorisation is always scoped, explicit, and granted independently of authentication.

## Human and Agent Identity, and Consent

An agent acts under its owner's identity and with its owner's consent — the agent is not an
independent party with its own standing. Agent identity (which agent, running where, acting
for whom) is tracked distinctly from the owner's identity, but is always bound back to that
owner. Consent for an agent to act is explicit and can be scoped to particular kinds of
actions or relationships, not assumed to be unlimited just because an agent exists.

## Bilateral, Independent Permissions

Every relationship in MAMA has two sides, and each side grants and can revoke its own
permissions independently. One party authorising something does not create, imply, or
require a matching authorisation from the other party. Neither side needs to adopt the
other's trust model, permission structure, or technology to participate.

## Human Decision and Financial Boundaries

Certain classes of decisions — committing money, agreeing to binding terms, or taking
irreversible real-world actions — remain human-in-the-loop by design. An agent may prepare,
recommend, or negotiate towards such a decision, but MAMA does not delegate the decision
itself to an agent unless its owner has explicitly and narrowly authorised that specific
action.

## Revocation and Trust

Permissions and relationships are revocable at any time, by either side, without needing the
other party's agreement. Trust in MAMA is not a one-time grant that lasts forever — it is
established, observed, and, where appropriate, re-established over time. Revocation should be
as easy and as unilateral as granting was.

## Examples

These are clean, conceptual illustrations only — no real people, organisations, or private
data are described.

- Alice's agent and Bob's agent negotiate a shared meeting slot without either agent seeing
  the other's full calendar — only free/busy information scoped to that one relationship is
  exchanged.
- Two agents co-draft a shared document, each able to edit only the sections their respective
  owner was given write access to, under a relationship scoped to that document.
- An agent is authorised to request a quote from another owner's agent and to negotiate terms,
  but any resulting payment requires its own owner's explicit confirmation before it is
  committed.

## Protocols and Services (Potential, Not Deployed)

MAMA is a model, not a product. Where concrete technologies are mentioned, they describe
*possible* building blocks for implementing MAMA-shaped systems — not evidence of a deployed
solution:

- **A2A** (agent-to-agent communication) is described as a *potential* interaction protocol
  agents could use to exchange the kinds of messages a relationship requires.
- **MCP** (Model Context Protocol) is described as a *possible* client/tool interface an agent
  could use to reach tools or services on its owner's behalf.
- A **brokerage** is described as a *potential*, separate service that could help owners'
  agents discover and establish relationships with each other — it is not part of this
  specification and is not implied to exist as a running service.

## Status

This document is a **preliminary public definition** of a proposed model. It is not an
established standard, not an implemented platform, and does not represent agreement from
Erik or any other named third party. Feedback and conceptual refinement are welcome — see
[CONTRIBUTING.md](CONTRIBUTING.md).

## License

The specification/documentation text in this repository is licensed under
[CC BY 4.0](LICENSE). Software code, if and when added to this repository, will be licensed
separately and explicitly — CC BY 4.0 does not cover code.
