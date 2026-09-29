# SCubeLabs

### Engineering the Complete Cloud Contact Center Stack

**SCubeLabs** is an engineering ecosystem for designing, building, testing, and operating a complete cloud contact center platform from first principles.

The landscape spans the full interaction lifecycle: carrier and channel ingress, SIP/WebRTC and media, interaction state, routing and agent delivery, workflow and outbound engagement, recording and transcription, workforce and quality management, customer feedback, analytics and reporting, AI, platform governance, observability, and outside-in customer-experience assurance.

SCubeLabs is intentionally organized around **domain ownership and architectural boundaries**. A repository name does not imply that the domain must become an independently deployed microservice. Boundaries are separated when state ownership, scaling, failure isolation, deployment lifecycle, security, or team ownership justify it.

> **Mission:** Understand and engineer what it takes to build a resilient, observable, testable, carrier-grade CCaaS platform end to end.

---

## Platform Principles

SCubeLabs is built around a few non-negotiable engineering ideas:

- **Explicit state ownership** — every authoritative state has one owning domain.
- **Protocol-neutral interaction model** — SIP, WebRTC, PSTN and digital-channel details remain behind adapters and channel boundaries.
- **Independent signaling and media concerns** — control, signaling and media scale and fail differently.
- **Event-driven integration** — domains publish durable facts instead of sharing databases.
- **Failure is part of the design** — HA, degraded modes, recovery, idempotency and reconciliation are architectural concerns.
- **Observability plus assurance** — internal telemetry is complemented by outside-in synthetic customer journeys.
- **Evidence over claims** — designs, labs and implementations are distinguished from behavior that has actually been executed and verified.
- **Security and compliance by design** — tenant isolation, authorization, auditability, retention and regulated-data handling are platform concerns.
- **Architecture before premature decomposition** — repositories express bounded contexts; deployment topology is earned through engineering requirements.

---

## The SCubeLabs Landscape

```text
Customers / Carriers / Digital Channels
                 |
                 v
+---------------------------------------------------------------+
|                    ENGAGEMENT & CHANNELS                      |
| Voice Edge | Digital | Email | Outbound | Callback | Workflow |
+-------------------------------+-------------------------------+
                                |
                                v
+---------------------------------------------------------------+
|                    INTERACTION & ROUTING                      |
| Interaction Core | Routing Engine | Agent Platform | Realtime |
+-------------------------------+-------------------------------+
                                |
             +------------------+------------------+
             |                                     |
             v                                     v
+----------------------------+        +---------------------------+
|       MEDIA & RECORDING    |        |     CUSTOMER CONTEXT      |
| Media | Recording | VoxOne |        | Profile | Integrations    |
+-------------+--------------+        +-------------+-------------+
              |                                     |
              +------------------+------------------+
                                 |
                                 v
+---------------------------------------------------------------+
|                   INTELLIGENCE & DATA                         |
| Transcription | AI | Analytics | Knowledge | Reporting        |
+-------------------------------+-------------------------------+
                                |
               +----------------+----------------+
               |                                 |
               v                                 v
+----------------------------+       +----------------------------+
| WORKFORCE & EXPERIENCE     |       | PLATFORM FOUNDATION        |
| WFM | QM | Surveys         |       | Identity | Control Plane   |
+----------------------------+       | Contracts | Notifications  |
                                     | Developer | Billing        |
                                     +-------------+--------------+
                                                   |
                                                   v
                                     +----------------------------+
                                     | GOVERNANCE & OPERATIONS    |
                                     | Audit/Compliance           |
                                     | Observability              |
                                     +-------------+--------------+
                                                   |
                                                   v
                                     +----------------------------+
                                     |      CX ASSURANCE          |
                                     | Synthetic Journeys         |
                                     | Voice Test Engine          |
                                     | Load / Performance Test    |
                                     +----------------------------+
```

The important distinction at the bottom is **inside-out observability versus outside-in assurance**. Logs, metrics, traces and protocol telemetry tell us what the platform reports about itself. Synthetic calls and journeys test whether a customer can actually reach the platform, navigate it, get routed, establish media and complete the intended experience.

---

## Repository Landscape

### Public — Architecture, Proof and Engineering Portfolio

| Repository | Responsibility |
|---|---|
| [scubelabs](https://github.com/scubelabs/scubelabs) | Front door, platform landscape and engineering direction |
| [carrier-grade-mini-acd](https://github.com/scubelabs/carrier-grade-mini-acd) | SIP/media/ACD reference implementation and controlled voice lab |
| [sip-troubleshooting-lab](https://github.com/scubelabs/sip-troubleshooting-lab) | SIP, SDP, RTP and failure-diagnosis labs |
| [ccaas-reference-architecture](https://github.com/scubelabs/ccaas-reference-architecture) | End-to-end CCaaS architecture, ownership and resilience model |
| [ccaas-domain-model](https://github.com/scubelabs/ccaas-domain-model) | Canonical CCaaS entities, lifecycle concepts, events and contracts |
| [voxone-showcase](https://github.com/scubelabs/voxone-showcase) | Public architecture and demonstrations for the VoxOne endpoint |

### Private — Core Platform and Foundation

| Repository | Responsibility |
|---|---|
| `ccaas-platform` | Umbrella implementation environment for the evolving CCaaS platform |
| `platform-contracts` | Canonical APIs, events, schemas and versioned cross-domain contracts |
| `platform-control-plane` | Tenant provisioning, configuration, policy and feature management |
| `identity-access-platform` | Authentication, authorization, roles, permissions and service identities |
| `interaction-core` | Authoritative interaction/conversation lifecycle and state ownership |
| `routing-engine` | Queues, skills, priority, eligibility, reservation and assignment |
| `agent-platform` | Agent sessions, presence, operational state and interaction delivery |
| `realtime-gateway` | Authenticated realtime subscriptions and bidirectional platform events |
| `notification-platform` | Platform, agent, administrator and customer notifications |
| `developer-platform` | APIs, SDKs, application registration, webhooks and extensibility |
| `tenant-billing-platform` | Metering, entitlements, quotas and tenant consumption |

### Private — Voice, Media and Engagement

| Repository | Responsibility |
|---|---|
| `voxone` | Cross-platform browser/desktop voice endpoint and diagnostic surface |
| `voice-edge` | Carrier-facing SIP ingress/egress, normalization, security and admission |
| `media-platform` | Media control, conferencing, playback and realtime media services |
| `recording-platform` | Recording orchestration, storage lifecycle, consent and retrieval |
| `digital-channel-platform` | Chat, SMS, messaging and asynchronous channel adapters |
| `email-channel-platform` | Email ingestion, threading, routing and response workflows |
| `outbound-platform` | Campaigns, dialing strategies, pacing, retries and contact policy |
| `callback-platform` | Virtual queue and callback orchestration |
| `workflow-platform` | Versioned IVR, interaction and business-flow orchestration |

### Private — Intelligence, Data and Customer Context

| Repository | Responsibility |
|---|---|
| `transcription-platform` | Streaming/post-interaction transcription, diarization and transcript lifecycle |
| `ai-platform` | Agent assistance, summarization, retrieval, classification and AI orchestration |
| `analytics-platform` | Interaction/speech analytics, topics, classifications and derived insights |
| `reporting-platform` | Historical facts, dimensions, aggregates, metrics and reporting |
| `knowledge-platform` | Runtime knowledge retrieval, recommendations and governed content delivery |
| `customer-profile-platform` | Unified customer identity, attributes, context and interaction history |
| `integration-platform` | CRM, external APIs, webhooks, connectors and data synchronization |

### Private — Workforce, Quality and Feedback

| Repository | Responsibility |
|---|---|
| `workforce-management` | Forecasting, staffing, scheduling, adherence and intraday management |
| `quality-management` | Evaluations, scorecards, calibration, coaching and quality workflows |
| `survey-platform` | Post-interaction feedback, invitations, responses and experience scoring |

### Private — Governance and Operations

| Repository | Responsibility |
|---|---|
| `audit-compliance-platform` | Audit, retention, legal hold, consent and regulated-data governance |
| `observability-platform` | Logs, metrics, traces, SIP/media telemetry, correlation, SLOs and alerting |

### Private — CX Assurance and Performance Engineering

| Repository | Responsibility |
|---|---|
| `cx-assurance-platform` | Synthetic customer journeys, continuous validation and proactive failure detection |
| `voice-test-engine` | Synthetic SIP/PSTN calls, IVR traversal, routing/media validation and diagnostics |
| `load-test-platform` | Distributed CCaaS workload, scale, stress, degradation and capacity testing |

### Private — Engineering Knowledge

| Repository | Responsibility |
|---|---|
| `medha` | Engineering knowledge and mastery system spanning voice, CCaaS, distributed systems, reliability and operations |

---

## Authoritative State Ownership

A central design rule is that derived consumers do not become accidental owners of operational state.

| State | Owning Domain |
|---|---|
| Interaction / conversation lifecycle | Interaction Core |
| Routing request, reservation and assignment | Routing Engine |
| Agent session, presence and operational state | Agent Platform |
| Tenant configuration and feature policy | Platform Control Plane |
| Identity, roles and authorization | Identity & Access Platform |
| Media session/control state | Media Platform |
| Recording metadata and artifact lifecycle | Recording Platform |
| Transcript lifecycle | Transcription Platform |
| Customer profile/context | Customer Profile Platform |
| Workforce forecast/schedule/adherence model | Workforce Management |
| Quality evaluation | Quality Management |
| Survey response | Survey Platform |
| Historical reporting facts | Reporting Platform |
| Audit and governance evidence | Audit & Compliance Platform |

Reporting, analytics, WFM, QM, AI and other consumers may build projections from domain events, but they should not silently become the source of truth for the operational domain that produced those events.

---

## Interaction Lifecycle

A representative voice interaction should eventually be traceable across the platform:

```text
PSTN / Carrier
      |
      v
 Voice Edge
      |
      v
 Media / Call Control
      |
      v
Interaction Core -----> Interaction Created
      |
      v
Routing Engine -------> Eligibility -> Queue -> Skills -> Priority
      |                                  |
      |                                  v
      |                              Reservation
      |                                  |
      v                                  v
Agent Platform <--------------------- Assignment
      |
      v
Realtime Gateway
      |
      v
    VoxOne
      |
      v
Agent Accepts -> Media Connected -> Conversation -> Disposition
      |
      +----> Recording
      +----> Transcription
      +----> Analytics / AI
      +----> Reporting
      +----> QM / WFM
      +----> Survey
      +----> Audit
```

SIP signaling state, media state, interaction state, routing state and agent state are deliberately separate concerns even when they participate in the same customer interaction.

---

## Data and Event Architecture

The intended platform model avoids a shared operational database:

```text
Domain Services
      |
      +---- authoritative operational stores
      |
      +---- domain events
                |
                v
          Event Backbone
                |
       +--------+---------+---------+---------+
       |        |         |         |         |
   Realtime  Reporting Analytics   WFM       AI
       |        |         |         |         |
       +--------+---------+---------+---------+
                |
                +----> QM / Audit / Assurance
```

Different workloads require different persistence characteristics. Operational state, event history, recordings, transcripts, search indexes, analytical projections and reporting facts are therefore treated as distinct data concerns rather than forced into one database model.

---

## Reliability and Failure Engineering

The architecture is evaluated through failure behavior, not only happy-path diagrams.

Key questions include:

- What happens to an interaction if a component fails mid-call?
- Which state must survive process, node, zone or region loss?
- How are duplicate events and retries made safe?
- How are routing reservations fenced and reconciled?
- How are signaling and media drained independently?
- What happens when a carrier, database, event backbone or AI dependency is degraded?
- Which features can brown out while core interaction handling remains available?
- How is an interaction reconstructed across signaling, media, routing, agent and data systems?
- How do we prove the customer journey works when every internal dashboard is green?

---

## Observability and CX Assurance

SCubeLabs treats these as complementary disciplines.

**Observability** provides internal evidence through logs, metrics, distributed traces, SIP ladders, RTP/RTCP statistics, domain events, correlation identifiers, SLOs and alerts.

**CX Assurance** generates external evidence through synthetic calls and digital journeys. A probe should ultimately be able to originate an interaction and validate call establishment, IVR prompts, DTMF/ASR, routing, queue treatment, agent delivery, two-way audio, transfers, disconnect behavior and service quality.

The assurance layer can also exercise controlled load and failure scenarios to establish capacity limits, degradation behavior and release gates.

---

## Engineering Maturity

SCubeLabs deliberately distinguishes:

```text
Architecture
    -> Contract
        -> Implementation
            -> Runnable Lab
                -> Executed Test
                    -> Reproducible Evidence
                        -> Operational Confidence
```

A repository, diagram, test plan or configuration is not itself proof that a production behavior works. Capability claims should advance only when supported by reproducible execution evidence.

---

## Current Direction

The ecosystem is being developed incrementally rather than attempting to implement 42 independent services simultaneously.

Near-term engineering centers on the canonical interaction model, voice/media path, routing semantics, agent delivery, VoxOne endpoint, platform contracts and reproducible protocol evidence. The broader repositories establish the target domain landscape and ownership boundaries so that WFM, QM, surveys, recording, transcription, AI, analytics, reporting, governance and assurance evolve as parts of one coherent platform.

Extraction into independently deployable components should occur only when justified by scaling, failure isolation, consistency, security, ownership or lifecycle requirements.

---

## What SCubeLabs Is About

SCubeLabs is not intended to be a collection of disconnected demos.

It is an attempt to answer a larger engineering question:

> **If we had to build a modern cloud contact center platform from the carrier edge to the customer experience, what would every major domain own, how would those domains communicate, how would the system fail, and what evidence would prove that it works?**

That means studying and engineering the complete system: protocols, state machines, distributed systems, media, routing, data, workforce, AI, security, reliability, operations and customer-experience assurance.

---

**SCubeLabs — engineering the complete contact center stack, from packet to platform to customer experience.**
