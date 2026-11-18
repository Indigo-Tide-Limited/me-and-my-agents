# MAMA Connections and Participation

This document extends [README.md](README.md) with the proposed model for how a MAMA
relationship actually gets started, who can take part, and what an owner can rely on once they
have. It is as **preliminary** as the rest of this specification.

> **Status: preliminary public definition.** Nothing described below is implemented, running,
> or agreed by any other named third party. It is a starting point for public discussion and
> refinement, not a claim about an existing service.

## Personal MAMA Identifiers and Links

An owner may hold a personal MAMA identifier — a link that can be shared to invite a connection,
for example `https://mama.example/id/alice` (illustrative only; `mama.example` is not a real,
reachable service). The same URL is intended to be understandable two ways: as an ordinary,
human-readable webpage when a person opens it in a browser, and as an agent-readable identifier
when an AI reads or is given it. A nontechnical user might, for instance, supply that same URL
to their AI app as the address of their MCP connector — the identifier does not require a
separate technical form to be useful to either a human or an agent.

**The URL is an identifier only. It is never a credential and never an authorisation grant.**
Possessing or entering it identifies who is being introduced — it does not, by itself, prove
real-world identity, authenticate anyone, or permit any access. Sharing a link is an
introduction: the recipient still has to request a connection, and the owner still decides what,
if anything, to permit.

## Email as a Possible Pilot Identification Approach

One possible way to bootstrap identification during an early pilot is a short-lived email
sign-in link or code, single-use where appropriate. Any such pilot verification token should
expire very quickly, and should be submittable through **either** the MCP route **or** the
website — not website-only — so that neither participation route is disadvantaged during
identification. This proves control of a mailbox at that moment; it is **not conclusive** proof
of a person's real-world or organisational identity. **While valid, the link or code is itself a
secret, bearer-style credential** — whoever presents it is treated as the mailbox holder — **and
must be protected from disclosure accordingly, including in logs and in AI tool/chat
histories.** If a link or code is reused, leaked, or otherwise disclosed, it should be treated
as a potentially compromised credential: the owner can revoke and reissue it, but — consistent
with the Revocation and Trust section of README.md — revoking it **cannot retract** any
information that was already disclosed while it was valid.

## Public Profiles and Owner-Set Defaults

Each owner may hold a small, per-person public profile and a set of reasonable default
permissions applied to *new* connection requests (for example, whether to accept an
introduction at all, or what minimal information to share with it). A default is the owner's
own baseline choice, not blanket or global access, and it composes with — rather than replaces —
the per-relationship scoping described in README.md's Selective Sharing section. Whether, and
how, a changed default should affect permissions already granted on an existing connection is an
open design question, not yet decided — this document does not assert that defaults are
retroactive, and does not assert that they are not. Whatever is eventually decided, an existing
connection's permissions remain Independent, Inspectable, Adjustable, and Revocable (see
Connection Requests and Permissions, below) on their own terms — an owner can always see,
narrow, widen, or revoke what a connection permits — without this document mandating any
particular mechanism by which that happens.

## Connection Requests and Permissions

A personal link or profile can be used to start an individual connection request. Each side's
resulting permissions are:

- **Independent** — one side's grant does not create or imply anything for the other side.
- **Inspectable** — an owner can see what a given connection is currently permitted to do.
- **Adjustable** — an owner can narrow or widen a connection's permissions at any time.
- **Revocable** — an owner can withdraw a connection's permissions at any time, unilaterally.

These properties extend README.md's Bilateral, Independent Permissions and Revocation and Trust
sections; they do not replace them.

## Shared Projects and Activities (Optional)

Beyond a simple one-to-one connection, MAMA proposes an optional, first-class **shared project
or activity**: a named, bounded context with its own participants, information, and permitted
actions, scoped separately from any other project. This is layered on top of ordinary bilateral
relationships — it does not redefine what a "relationship" is. A connection does not
automatically grant access to any shared project, and being part of one project does not grant
access to another.

**Edge case (tentative — not yet decided).** How a shared project's access relates to any
underlying bilateral connection(s) between its participants is still an open design question.
This document does not assume every participant's project access necessarily rests on a single
underlying bilateral connection, and does not assume that revoking any such connection would or
would not cascade to remove that participant's project access, or that it would leave every
other participant's access unaffected — all of that is undecided. Whatever is eventually
decided, each participant's own permissions for the project remain Independent, Inspectable,
Adjustable, and Revocable, scoped separately from any other project or connection.

## One-Time Connection per Environment

An owner is expected to connect a given AI environment or account to MAMA once, rather than
re-authenticating on every single request. Re-authentication is expected when it is actually
needed — for example after a revocation, before a particularly sensitive action, or as part of
an account-recovery flow.

**Edge case.** If a one-time environment connection is revoked or expires while a shared
project is ongoing, that owner's agent loses access to the project until it is
re-authenticated. The project's record and the other participants' access are unaffected, and a
lapsed connection does not delete history or disclose anything new on its own.

## Two Participation Routes

MAMA proposes two, equally-supported ways for an owner to take part:

- **Use an existing AI app.** An ordinary user connects a compatible Claude/ChatGPT-type client
  to the MAMA MCP service. They do not need to build or host anything themselves.
- **Bring an agent system.** A technical owner integrates their own agent framework or MCP
  server with the service through an appropriate client or adapter.

Both routes represent the same owner, relationship, and activity concepts, and the same
independent permissions — they can interoperate without either side needing to adopt the
other's tools. An owner may use both routes at once. Neither route exposes all of an owner's
existing tools or private data by default; connecting an account is not the same as exposing
everything behind it.

## The Hub (Optional, Not Mandatory)

As described in README.md's Protocols and Services section, a **hub** is a potential, separate
coordinating service that could issue personal links, manage profiles and connection/activity
permissions, and relay or queue scoped requests and responses between owners' agents. It is not
part of this specification, is not implied to exist as a running service, and the open MAMA
model does not require any particular hub — self-hosting and federation are separate,
unexplored future options, not a prerequisite for anything described here.

## Browser/MCP Equivalence

Where a hub exists, its core operations are proposed to be available through both a
human-friendly web interface and an agent-friendly MCP interface, backed by one authoritative
service with consistent policy enforcement. An owner could review profiles, connection and
activity requests, permissions, and revocations in a browser even when their AI cannot notify
them. MCP-side operations remain subject to the owner's own delegated permissions,
action-specific approvals, and whatever a given client actually supports — parity here means
equivalent *capability*, not identical presentation, and it never bypasses human approval or
delegated authority. Recipient choices this is proposed to cover equivalently include:
invitation and message eligibility, acceptance, blocking and revocation, what communication is
permitted, rate limits, and abuse controls — all proposed to run through the same backend and
policy regardless of which client is used.

**This is a design goal to investigate and test, not established behaviour.** Whether the same
personal MAMA URL can actually be discovered and onboarded consistently across a human-facing
browser flow and a given AI client's MCP-connector flow — and what client-specific onboarding
steps that requires — is proposed work to be tried and tested, not a standard guarantee that
holds across every client today. Nothing here should be read as claiming this already works
uniformly.

## Capability and Security Boundaries

These boundaries hold regardless of which participation route is used:

- An MCP server existing, by itself, does **not** make a system reachable from outside or able
  to push a notification into it — reachability and notification support depend on the actual
  client and its configuration, and must be checked separately for each environment.
- **Authentication never implies authorisation.** Proving who is acting says nothing about
  what that agent is allowed to do.
- Linking an account or agent system to MAMA does **not** expose all of that owner's existing
  MCP tools or private data — only what is explicitly, scopedly permitted.
- **Revocation stops future access, but it cannot retract information already disclosed.**
  Once something has been shared under a permission that is later revoked, revocation prevents
  further authorised access — it does not and cannot recall what was already seen.

## Hub Baseline Guarantee (Not a Swarm Substitute)

MAMA's hub, where one exists, is intended to guarantee a safe, usable *baseline* level of
participation for any owner, independent of whether they run a swarm (an owner's own
integrated agent framework — what this document's Two Participation Routes section calls
"bring an agent system"). The hub supplies the essential facilities a swarm cannot be
guaranteed to provide on its own — for example, a way to be found and followed up with safely
even without one. This is a baseline guarantee, not a claim that the hub offers every feature a
sophisticated swarm might otherwise provide; a swarm can still do more than the baseline, on
top of it.

## Illustrative Story: Following Up Without a Swarm

*The following is a fictional, generic illustration — no real people, invitations, or outreach
are described, and nothing here represents agreement from any named third party.*

Person A is new to AI agents and uses an off-the-shelf AI app; they have no MAMA account.
Person B already has a MAMA account and a personal swarm. At an event, Person A agrees to
follow up and gives Person B an email address. Person B's swarm submits a MAMA invitation on
Person B's behalf. The hub privately resolves whether that address belongs to a registered or
unregistered owner and sends the invitation email itself when needed, without exposing to the
sender whether an account already exists. Person A can decline, or verify the email and use an
ordinary browser, without ever configuring a swarm; adding an AI app later is optional, and
depends on what that client actually supports and on Person A's own authorisation.

This is a separate, generic illustration from the "Proposed first pilot" paragraph below — it
does not claim any pilot is running, scheduled, or agreed. The hub's first demo is illustrated
here as using hub-mediated email delivery as its one invitation mechanism; this is not a second
mechanism competing with the pilot paragraph's own, more general request/response shape.

This story does not specify hub behaviour for edge cases such as decline, non-response,
bounced email, or rate-limiting being hit — those remain open implementation questions for if
and when a hub is built, not specified or claimed here.

## Email as a Delivery Address, Not a Credential

An invitation email address is a delivery address, not a permission grant or a credential — it
identifies where to send something, not who may be contacted about what. Agreeing to follow up,
or accepting a connection that resulted from an invitation, does not itself permit marketing,
unrestricted agent-to-agent contact, or any sharing of private data. See "Email as a Possible
Pilot Identification Approach", above, for the related but distinct question of pilot sign-in:
very short-lived, single-use verification codes or tokens are themselves secrets while valid,
and proving control of a mailbox is still not the same as verifying a person's real-world
identity.

## Demo Communication and Filtering Scope

The communication and filtering surface covered by the demo is: invitations, accepting or
declining them, blocking, rate limits, and a simple inbox. It does not include any AI-driven
relevance, urgency, or attention filtering. This narrower demo scope does not cancel or narrow
the existing profile, authentication, scopes, revocation, or browser/MCP-parity work described
elsewhere in this document and in README.md.

## Intelligent Attention Management (Optional, Future — Not Authorised)

This describes a possible future, optional, recipient-side capability only — it is not
authorised for implementation, and nothing here commits to building it. If it is ever pursued,
the working assumptions would be: it follows the owner's own preferences; it favours sorting,
digesting, or flagging over silently discarding anything; any filtered item remains explainable
and recoverable by its owner; an AI acting in this role never grants permissions or discloses
data on its own initiative; and no amount of swarm-side filtering sophistication can ever weaken
the hub baseline guarantee described above.

## Illustrative Story and Proposed First Pilot

*The following is a fictional illustration, not a description of an actual event or an actual
pilot. It does not represent agreement from any named third party to anything described here.*

Alice meets Bob at a conference and wants to follow up without handing over her personal
contact details. She shares her MAMA link, `https://mama.example/id/alice`. Bob enters it into
his own AI; his AI explains who the request identifies and what it's for, and asks him what to
permit. Alice's AI, in turn, asks her to approve the new connection and whatever Bob's side has
requested. Each of them decides independently, and either can later adjust or revoke whatever
permissions they each chose to grant.

**Proposed first pilot (illustrative only — fictional, not a description of an actual pilot,
deployment, or confirmed collaboration).** A small, fictional pilot could exercise both
participation routes together: one owner connects an existing AI app to a shared MAMA service
and sends a deliberately non-sensitive request (such as a simple introduction) to a second
owner, who has instead integrated their own agent system through an adapter. Both sides
authenticate, each approves its own side of the connection and permissions independently, the
request and response travel both ways with identifiable attribution, and either side can revoke
access afterwards and show that a later request is then refused. As above, this paragraph
proposes a shape for a pilot — it does not claim one is running, scheduled, deployed, or agreed
by anyone.

Separately, implementation of a technical demonstration of some of these ideas is in progress
under a separate commission. No platform is deployed, this document is not a status report on
that work, and nothing here implies any named participant has agreed to take part.

## Status and Licensing

Like the rest of this repository, this document is a **preliminary public definition**, not an
implemented platform, and does not represent agreement from any named third party. It is
licensed under this repository's existing [CC BY 4.0 license](LICENSE) — no new licence terms
are introduced here.
