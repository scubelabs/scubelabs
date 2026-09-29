# SCubeLabs

### Building the Cloud Contact Center as a System

**SCubeLabs** is a solution-oriented engineering initiative to design and build a modern, multi-tenant **Contact Center as a Service (CCaaS) platform** from the carrier edge through the agent and customer experience.

The goal is not to collect isolated demos. The goal is to engineer the **whole system**: voice and digital ingress, interaction lifecycle, routing, agent delivery, media, recording, workflow, outbound, transcription, AI, analytics, reporting, workforce management, quality management, customer feedback, platform governance, observability, and outside-in experience assurance.

> **North Star:** one coherent CCaaS platform with explicit ownership, stable contracts, measurable failure behavior, and reproducible engineering evidence.

---

## What We Are Building

SCubeLabs treats a contact center as a distributed real-time platform rather than a collection of UI features.

```text
                           SCubeLabs CCaaS Platform
┌─────────────────────────────────────────────────────────────────────────────┐
│                         EXPERIENCE & ENGAGEMENT                             │
│   Voice │ Chat │ Messaging │ Email │ Outbound │ Callback │ Workflow        │
└───────────────────────────────────┬─────────────────────────────────────────┘
                                    │
┌───────────────────────────────────▼─────────────────────────────────────────┐
│                         INTERACTION CONTROL                                 │
│   Interaction Core │ Routing Engine │ Agent Platform │ Realtime Gateway    │
└──────────────────────┬─────────────────────────────────┬────────────────────┘
                       │                                 │
┌──────────────────────▼──────────────────┐   ┌──────────▼────────────────────┐
│            VOICE & MEDIA                │   │       CUSTOMER CONTEXT        │
│ Voice Edge │ Media │ Recording │ VoxOne │   │ Profile │ Integrations        │
└──────────────────────┬──────────────────┘   └──────────┬────────────────────┘
                       └────────────────┬────────────────┘
                                        │
┌───────────────────────────────────────▼─────────────────────────────────────┐
│                          INTELLIGENCE & DATA                                │
│   Transcription │ AI │ Analytics │ Knowledge │ Reporting                   │
└──────────────────────┬─────────────────────────────────┬────────────────────┘
                       │                                 │
┌──────────────────────▼──────────────────┐   ┌──────────▼────────────────────┐
│       WORKFORCE & EXPERIENCE            │   │      PLATFORM FOUNDATION      │
│ WFM │ Quality │ Surveys                 │   │ Identity │ Control │ Contracts│
└─────────────────────────────────────────┘   │ Notifications │ Dev │ Billing │
                                              └──────────┬────────────────────┘
                                                         │
                                              ┌──────────▼────────────────────┐
                                              │   GOVERNANCE & OPERATIONS     │
                                              │ Audit │ Compliance │ Observe  │
                                              └──────────┬────────────────────┘
                                                         │
                                              ┌──────────▼────────────────────┐
                                              │       CX ASSURANCE            │
                                              │ Synthetic │ Voice Test │ Load │
                                              └───────────────────────────────┘
```

The repositories are **bounded engineering domains inside this solution**. A repository boundary does not automatically mean a separately deployed microservice; deployment boundaries are earned through scale, consistency, failure isolation, security, ownership, and lifecycle requirements.

---

## Current Engineering Direction

SCubeLabs is moving from **architecture → contracts → executable vertical slices → failure evidence → platform integration**.

The current implementation path concentrates on the critical real-time spine:

```text
Carrier / Endpoint
       │
       ▼
   Voice Edge
       │
       ▼
 Media / Call Control
       │
       ▼
 Interaction Core
       │
       ▼
 Routing Engine
       │
       ▼
 Agent Platform
       │
       ▼
 Realtime Gateway
       │
       ▼
     VoxOne
```

Around that spine, platform contracts, identity, configuration, recording, transcription, reporting, observability, and assurance establish the shared foundation needed for the rest of the CCaaS landscape.

The broader domain repositories are not a promise that dozens of independent services already exist. They define the target solution boundaries so implementation can grow without losing state ownership, interoperability, or architectural coherence.

---

## One Platform, Four Engineering Tracks

| Track | Purpose | Representative repositories |
|---|---|---|
| **Platform** | Build the runtime CCaaS solution and its bounded domains | `ccaas-platform`, `interaction-core`, `routing-engine`, `agent-platform`, `voice-edge`, `media-platform` |
| **Architecture & Contracts** | Define ownership, canonical models, APIs, events, resilience and deployment rules | `ccaas-reference-architecture`, `ccaas-domain-model`, `platform-contracts` |
| **Validation & Assurance** | Prove protocol behavior, customer journeys, scale and failure handling | `carrier-grade-mini-acd`, `sip-troubleshooting-lab`, `cx-assurance-platform`, `voice-test-engine`, `load-test-platform` |
| **Knowledge** | Capture the engineering knowledge required to design and operate the platform | `medha` |

This distinction is deliberate: **designed**, **implemented**, **lab-proven**, **load-proven**, **failure-proven**, and **production-observed** are different maturity states.

---

## Platform Domains

### Core runtime
`interaction-core` · `routing-engine` · `agent-platform` · `realtime-gateway`

These domains own the canonical interaction lifecycle, queue/routing decisions, reservations and assignment, agent state/capacity, and realtime delivery.

### Voice, media and engagement
`voice-edge` · `media-platform` · `recording-platform` · `digital-channel-platform` · `email-channel-platform` · `outbound-platform` · `callback-platform` · `workflow-platform` · `voxone`

These domains connect customers and agents while keeping transport/protocol behavior behind explicit boundaries.

### Intelligence and data
`transcription-platform` · `ai-platform` · `analytics-platform` · `reporting-platform` · `knowledge-platform` · `customer-profile-platform` · `integration-platform`

These domains turn operational events and customer context into searchable, reportable, assistive, and analytical capabilities without taking ownership away from operational systems.

### Workforce and experience
`workforce-management` · `quality-management` · `survey-platform`

These domains cover forecasting, scheduling, adherence, evaluation, coaching, calibration, and post-interaction feedback.

### Platform foundation
`platform-control-plane` · `identity-access-platform` · `platform-contracts` · `notification-platform` · `developer-platform` · `tenant-billing-platform`

These are shared platform capabilities for multi-tenancy, configuration, identity, contracts, extensibility, notifications, entitlements, and metering.

### Governance, reliability and proof
`audit-compliance-platform` · `observability-platform` · `cx-assurance-platform` · `voice-test-engine` · `load-test-platform`

SCubeLabs separates **inside-out observability** from **outside-in assurance**. Telemetry explains what the platform reports about itself; synthetic journeys test whether customers can actually complete the intended experience.

---

## Public Engineering Surface

These repositories expose the architecture and engineering approach without pretending that design artifacts are production certification.

| Repository | Role |
|---|---|
| [**ccaas-reference-architecture**](https://github.com/scubelabs/ccaas-reference-architecture) | End-to-end system architecture, operational boundaries, state ownership, data topology, HA, scaling, security and migration |
| [**ccaas-domain-model**](https://github.com/scubelabs/ccaas-domain-model) | Canonical CCaaS vocabulary, entities, lifecycles, identifiers, events and bounded contexts |
| [**carrier-grade-mini-acd**](https://github.com/scubelabs/carrier-grade-mini-acd) | Executable voice/ACD engineering path using SIP, media, routing, state, observability and failure testing |
| [**sip-troubleshooting-lab**](https://github.com/scubelabs/sip-troubleshooting-lab) | Protocol-level SIP, SDP and RTP diagnostics and reproducible failure labs |
| [**voxone-showcase**](https://github.com/scubelabs/voxone-showcase) | Public architecture and demonstrations for the cross-platform voice endpoint |
| [**customer-profile-platform**](https://github.com/scubelabs/customer-profile-platform) | Customer identity, context and interaction-history domain surface |

---

## Architectural Rules

1. **One authoritative owner per mutable state.**
2. **Interaction identity is the correlation spine across channels and domains.**
3. **SIP/media state is not business interaction state.**
4. **Routing decisions and agent capacity are explicit, transactional concepts.**
5. **Domains integrate through versioned contracts and durable facts—not shared database ownership.**
6. **Real-time paths do not depend on analytical/reporting queries.**
7. **Retries, idempotency, fencing and reconciliation are first-class design concerns.**
8. **Signaling, media, control and data planes can scale and fail independently.**
9. **Security, tenant isolation, auditability and retention are platform concerns.**
10. **Capability claims require evidence appropriate to their maturity level.**

---

## Authoritative State Ownership

| State | Owning domain |
|---|---|
| Interaction / conversation lifecycle | Interaction Core |
| Queue, routing request, reservation and assignment | Routing Engine |
| Agent session, presence, capacity and operational state | Agent Platform |
| Tenant configuration and feature policy | Platform Control Plane |
| Identity, roles and authorization | Identity & Access Platform |
| Media session/control state | Media Platform |
| Recording metadata and artifact lifecycle | Recording Platform |
| Transcript lifecycle | Transcription Platform |
| Customer profile and context | Customer Profile Platform |
| Forecast, schedule and adherence model | Workforce Management |
| Quality evaluation | Quality Management |
| Survey response | Survey Platform |
| Historical reporting facts | Reporting Platform |
| Audit and governance evidence | Audit & Compliance Platform |

Derived systems may project these facts, but they do not silently become the source of truth.

---

## How a Voice Interaction Traverses the Platform

```text
PSTN / Carrier
      │
      ▼
 Voice Edge ─────────────── signaling admission / normalization
      │
      ▼
 Media Platform ─────────── media control / treatment
      │
      ▼
 Interaction Core ───────── canonical interaction created
      │
      ▼
 Routing Engine ─────────── queue → eligibility → ranking → reservation
      │
      ▼
 Agent Platform ─────────── capacity / offer / assignment
      │
      ▼
 Realtime Gateway ───────── authenticated delivery
      │
      ▼
    VoxOne ──────────────── agent call control and media endpoint
      │
      ├──► Recording
      ├──► Transcription
      ├──► Analytics / AI
      ├──► Reporting
      ├──► QM / WFM
      ├──► Survey
      └──► Audit / Observability / Assurance
```

The same interaction must remain traceable across platform interaction IDs, SIP dialogs, media legs, routing attempts, agent reservations, recordings, transcripts, and reporting facts.

---

## Engineering Maturity Model

```text
Designed
   ↓
Contracted
   ↓
Implemented
   ↓
Runnable
   ↓
Integration-tested
   ↓
Failure-tested
   ↓
Load-tested
   ↓
Reproducibly evidenced
   ↓
Operationally proven
```

This prevents architecture diagrams, source code, and test plans from being presented as stronger evidence than they actually are.

---

## Where to Start

**Understand the system:** [CCaaS Reference Architecture](https://github.com/scubelabs/ccaas-reference-architecture)

**Understand the language and entities:** [CCaaS Domain Model](https://github.com/scubelabs/ccaas-domain-model)

**Follow the executable voice path:** [Carrier-Grade Mini ACD](https://github.com/scubelabs/carrier-grade-mini-acd)

**Study protocol failure behavior:** [SIP Troubleshooting Lab](https://github.com/scubelabs/sip-troubleshooting-lab)

**See the endpoint direction:** [VoxOne Showcase](https://github.com/scubelabs/voxone-showcase)

---

## The Engineering Question

> **If we had to build a modern cloud contact center from the carrier edge to the customer experience, what must every domain own, how should those domains communicate, how should the system behave under failure, and what evidence proves that it works?**

SCubeLabs exists to answer that question in architecture, contracts, code, labs, tests, and measurable system behavior.

---

### SCubeLabs

**From packet → interaction → agent → intelligence → customer experience.**

*Engineering the contact center as one coherent platform.*
