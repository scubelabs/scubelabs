# SCube Labs

### Voice Platforms • Distributed Systems • Contact Center Engineering

Welcome to **SCube Labs** — an engineering workspace focused on building, understanding, and operating resilient real-time communications and distributed platforms.

The projects here explore the engineering behind carrier-grade voice systems: SIP signaling, media processing, contact-center routing, WebRTC, high availability, observability, failure handling, and cloud-native infrastructure.

---

## 🔬 Current Lab Focus

- **Carrier-Grade Voice Platforms** — SIP routing, signaling, RTP/media, carrier connectivity and resiliency
- **Contact Center / ACD Engineering** — queues, agent state, skills-based routing, IVR and call distribution
- **Kamailio & FreeSWITCH** — scalable SIP proxy and media/application architectures
- **WebRTC** — browser-based real-time communications and agent endpoints
- **Distributed Systems** — state management, event-driven design, failover and horizontal scaling
- **Observability** — SIP tracing, metrics, logs, dashboards and production troubleshooting

---

## 🧰 Technology Stack

**Voice & Real-Time Communications**  
SIP • SDP • RTP/RTCP • WebRTC • DTMF • TLS/SRTP

**Voice Infrastructure**  
Kamailio • FreeSWITCH • SIP Trunks • SBC Concepts • Media Services

**Platform & Data**  
Docker • Kubernetes • Redis • PostgreSQL • REST APIs • Event-Driven Architecture

**Observability & Troubleshooting**  
Wireshark • sngrep • Prometheus • Grafana • SIP Ladder Analysis

---

## Projects

| Repository | Purpose | Current evidence |
|---|---|---|
| [VoxOne](https://github.com/scubelabs/voxone) | Shared call-control core, browser SIP/WebRTC adapter and desktop shell | Source, unit tests and build workflow; real SIP/media interoperability remains unverified |
| [Carrier-Grade Mini ACD](https://github.com/scubelabs/carrier-grade-mini-acd) | Local SIP edge and media/queue lab | M1 configuration and runbook; two-way RTP and end-to-end agent delivery require a verified local run |
| [SIP Troubleshooting Lab](https://github.com/scubelabs/sip-troubleshooting-lab) | Directional SIP/SDP/RTP failure investigation | Nine drafted guides; controlled before/after captures are not published |
| [CCaaS Domain Model](https://github.com/scubelabs/ccaas-domain-model) | Canonical entities, events and data contracts | Schemas, fixtures and CI contract validation; no runtime service |
| [CCaaS Reference Architecture](https://github.com/scubelabs/ccaas-reference-architecture) | Service ownership, routing, media, reporting and resilience design | Architecture and proof plans; no executable platform |
| Medha | Private learning and curriculum project | Access depends on repository permissions |

These projects deliberately distinguish a design, a runnable lab and verified behavior. Repository names express direction, not production certification.

---

## 🧭 Engineering Philosophy

The goal of SCube Labs is not to collect sample applications. Each project is intended to answer engineering questions such as:

- What happens when a component fails during an active call?
- How do signaling and media scale independently?
- Where should call state live?
- How do we prevent a SIP proxy or media server from becoming a bottleneck?
- How do we diagnose a voice problem from packet capture to application state?
- How should a contact-center platform behave during carrier, region or dependency failures?

Projects will include architecture diagrams, runnable configurations, call flows, failure scenarios, tests and troubleshooting documentation wherever practical.

---

## Roadmap

Prove the Mini ACD end-to-end voice path, expand the troubleshooting lab with sanitized captures, connect VoxOne to a controlled SIP test environment, and evolve the shared domain contracts from observed behavior. Publish tests and failure evidence alongside capability claims.

---

> **SCube Labs** — exploring how reliable real-time communication systems are designed, built, scaled and operated.
