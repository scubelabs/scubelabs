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

## 🚧 Projects Under Development

### ☎️ Carrier-Grade Mini ACD
A working Automatic Call Distributor built around Kamailio and FreeSWITCH, progressively implementing agent state, queues, routing strategies, call control, resiliency and observability.

**Planned stack:** Kamailio • FreeSWITCH • WebRTC • Redis • PostgreSQL • Docker

### 🔎 SIP Troubleshooting Lab
Hands-on SIP/RTP failure scenarios with packet captures, SIP ladders, symptoms, root-cause analysis and fixes.

Topics will include NAT, one-way audio, authentication failures, SIP retransmissions, codec negotiation, SDP problems and RTP troubleshooting.

### 🏗️ CCaaS Reference Architecture
A production-oriented reference architecture for modern Contact Center as a Service platforms covering carrier ingress, SIP edge, media, IVR, ACD, agent connectivity, data, observability, security, high availability and disaster recovery.

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

## 🗺️ Roadmap

`Mini ACD` → `SIP Troubleshooting Lab` → `CCaaS Reference Architecture` → `WebRTC Agent` → `Voice Platform Observability` → `Multi-Carrier Routing`

---

> **SCube Labs** — exploring how reliable real-time communication systems are designed, built, scaled and operated.
