# Personal CRM — HumanwareOS wedge spec

Status: draft for product review, 2026-08-08. Owner: Ariel. Surface: `humanwareos.com/personal-crm/`.

## Product call

Personal CRM is a focused doorway into HumanwareOS, not a separate product or brand. The narrow promise is: **stay close to the people you care about without maintaining a database about them.**

The wedge is timely because agents can now do the work that made earlier personal CRMs decay: extract relationship evidence from ordinary communication, propose updates, surface the right person at the right moment, and learn from corrections. The human should never become a data-entry clerk.

## User and job

The first user is a relationship-dense individual who already has contacts, email, and calendars across Apple or Google but cannot reliably remember promises, follow-ups, context, and important dates.

When people pass through my life, help me remember who matters, what we share, and what I owe—without turning the relationship into sales software.

## Core loop

1. Connect Apple or Google contacts, calendar, and email with explicit scopes.
2. HumanwareOS resolves people into one relationship graph and shows provenance for every inferred fact.
3. Agents propose meaningful updates: a promise, changed role, important date, last contact, introduction, or next step.
4. The human confirms, corrects, ignores, or makes a field private.
5. Buzz surfaces a small daily or weekly relationship brief and lets the human act in the original ecosystem.
6. Outcomes and corrections improve future suggestions.

## Product principles

- **Relationships, not leads.** No pipeline language, engagement scores, or gamified friendship.
- **Propose, do not silently profile.** Sensitive facts require human confirmation before becoming durable memory.
- **Evidence over assertion.** Every durable fact retains source, date, confidence, and visibility.
- **Private by default.** A person's private notes are not exposed merely because that person joins a shared Buzz space.
- **Play well with ecosystems.** Apple and Google remain systems of interaction; HumanwareOS is the coordination and meaning layer.
- **Agents operate the system.** Humans speak, review, and decide; agents reconcile and maintain.

## Minimum useful product

### In scope

- Import and reconcile contacts from one Apple or Google account.
- Person pages with identity, relationship, important dates, open loops, last meaningful contact, notes, and evidence.
- Natural-language capture: “I promised Maya the deck Friday” or a longer voice dump.
- Proposed facts and commitments with confirm/correct controls.
- “Who needs attention?” brief with visible reasoning.
- Search and ask: “Who do I know at Block?” or “What did I promise Emma?”
- One shared relationship or household space to test multiplayer permissions.

### Not in scope

- Replacing Contacts, Gmail, Mail, Calendar, Messages, or Beeper.
- Automated outbound communication without per-action permission.
- Sales pipelines, mass outreach, contact enrichment, or scraped dossiers.
- A universal enterprise CRM.

## Object model

- **Person:** stable HumanwareOS identity plus linked ecosystem identities.
- **Relationship:** the human's context with that person; never assumed symmetric.
- **Evidence:** message, event, note, file, or explicit human statement supporting a fact.
- **Fact:** confirmed or proposed attribute with provenance and visibility.
- **Commitment:** something promised by or to a person, with lifecycle state.
- **Moment:** dated interaction or meaningful event.
- **Space:** private or shared context with members, agents, and permissions.

The Buzz/Nostr contact list (`kind:3`) is a useful follow-list primitive, but it is not this ontology. HumanwareOS needs richer relationship, evidence, commitment, and visibility objects above it.

## Multiplayer and permissions

Multiplayer is core architecture, not a later collaboration feature.

- A person can be invited to the HumanwareOS community through Buzz's current relay invite flow.
- Spaces define membership and agent access.
- Every fact and evidence item has an owner and visibility: private, shared with named people, or shared to a space.
- Sharing a person record never shares private notes by default.
- Agents receive scoped access by space and action, with auditable writes.
- Cross-person inferences require consent from the owner of each private source.

## Connector strategy

### First

- Google Contacts, Google Calendar, Gmail.
- Apple Contacts and Calendar through local EventKit/Contacts frameworks on macOS/iOS.
- Apple Mail through a local adapter or standards-based mail access where available.

### Later

- Messages and third-party communications through explicit local or provider connectors.
- Work identity sources such as Slack, LinkedIn exports, and company directories.

Connectors ingest the minimum required fields, store cursors and source identifiers, expose revocation, and never make cloud copies the canonical HumanwareOS record.

## Buzz feasibility — current read

### Available now

- Relay-level invite links with bounded expiry and use counts.
- Community membership and private-channel invitations.
- First-class human and agent public-key identities.
- NIP-02 contact lists with petnames through the SDK and CLI.
- Signed events, channels, DMs, search, and auditable agent activity.

### Product work required

- A richer relationship schema above the NIP-02 follow list.
- Per-object visibility for relationship facts and evidence.
- Apple and Google connector services and consent UX.
- Person resolution across public keys, email addresses, phone numbers, and provider IDs.
- A human-friendly person page, proposals inbox, and relationship brief inside Buzz.
- Clear shared-space permission and revocation UX.

Verdict: Buzz already supplies the identity, invitation, multiplayer, conversation, and agent substrate. It does not yet supply a personal CRM; that can be built as a HumanwareOS capability without bending Buzz into an office suite.

## Demand test

The landing page tests one promise: **remember the relationship, not the database.**

Primary signal: a visitor opens a pre-filled GitHub alpha request and submits it. Secondary signal: they can accurately describe the person or promise they currently lose track of. Page traffic alone is not validation.

The first concierge test uses a small contact set and a weekly brief before building continuous inbox ingestion. Success is at least five target users completing setup, returning for three briefs, and confirming that one surfaced commitment or relationship would otherwise have been missed.

## Risks

- The trust cost of a wrong or creepy inference is much higher than in a task manager.
- Ecosystem permissions can make onboarding too heavy before value is visible.
- A broad contact graph can become surveillance software through careless defaults.
- Apple integrations may require native clients and entitlements, while Google can start server-side.
- “Personal CRM” is legible but carries sales-software baggage; the landing page should use it as category context, not emotional promise.

## Decision after the test

Proceed only if people return for the brief and act on it. If they merely import contacts or praise the idea, keep the relationship graph as HumanwareOS infrastructure rather than a standalone wedge.
