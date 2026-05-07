# CAPSULA: Zero-Trust Mesh Transport Protocol

A binary-first, cryptographically verified transport layer engineered for distributed data meshes and edge computing environments.

## ⚙️ System Architecture

CAPSULA is a custom protocol designed to solve the overhead and unreliability of standard HTTP/JSON APIs when moving heavy analytical payloads (like Apache Parquet files) across unstable edge networks (e.g., WireGuard/ZeroTier meshes). 

Written in Rust for memory safety and zero-cost abstractions, it provides a rigid, strongly-typed envelope for bidirectional communication between Core orchestrators and remote Edge nodes.

### Core Engineering Principles:

* **Cryptographic Integrity by Default:** Every message envelope automatically computes and verifies a SHA-256 checksum of its payload. This ensures zero data corruption during transit over unpredictable or lossy network layers.
* **Binary-First Serialization:** While metadata is structured in fast, easily parsed JSON, the actual payloads are strictly binary. This bypasses the base64-encoding bloat typically associated with moving Parquet files or compiled models over REST APIs.
* **Deterministic Routing & State:** The protocol strictly defines message directionality (`CoreToEdge` vs `EdgeToCore`) and encapsulates specific distributed operations (e.g., `FetchCandles`, `RunWalkerSim`). This prevents edge-node hallucination and ensures the state machine remains predictable.
* **Asynchronous Callback Telemetry:** The envelope structure natively supports execution telemetry (processing time, rows affected, exact error traces), allowing the central orchestrator to monitor remote node health and trigger self-healing routines if an edge node stalls.

## 📦 Protocol Implementation

This repository contains the core library (`lib.rs`) detailing the data structures and cryptographic verification methods. 

* `CapsulaMeta`: The routing and operational metadata envelope.
* `Capsula`: The full payload containing the metadata, raw binary data, and integrity hashes.

---
*Note: This repository abstracts the core transport structures. Specific network listeners (e.g., Tokio TCP/UDP handlers) and proprietary algorithmic payloads have been omitted for security and compliance.*
