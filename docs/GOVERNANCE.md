# Aegis Governance Model

This document covers the trust, signing, replay, and audit machinery of the Convergence Protocol.

## 1. Identity

Every agent and human operator has a DID: `did:neuruh:<handle>`. Root of trust is the Neuruh signing key, stored in the Neuruh Credential Map (never here).

## 2. Rule File Signing

- `aegis/rules/v0_1.yaml` is signed with a detached signature `v0_1.yaml.sig`
- Router loads both. If signature is missing, invalid, or signed by a non-authorized DID, Router refuses to start.
- Key rotation events are themselves provenance records signed by the outgoing key.

## 3. Provenance Ledger

- Append-only log persisted via `ether-layer`
- One record per Router decision (classify + route + compose)
- Schema: `contracts/provenance-record@0.1.0.schema.json`
- Replayable via `aegis compose --replay-from=<decision_id>`

## 4. Content-Addressed Node Releases

- Every tagged node release includes `artifact_sha256` in `node.yaml`
- Worlds pin `<node>@<semver>@sha256:<hash>` — not just semver
- Router refuses to compose if any pinned hash cannot be verified

## 5. Dual Control

- Any operation with `capabilities.destructive: true` requires 2 signatures
- Signatures stored alongside the provenance record
- Configuration lives in `rules/governance.yaml` (which operators hold destructive authority)

## 6. Replay Determinism

- `aegis compose --replay-from=<decision_id>` must produce byte-equal manifest
- Any divergence is a governance incident: logged, signed, escalated
- CI runs 100 random replay assertions against a reference ledger on every commit

## 7. SOC2 Mapping (Preview)

| SOC2 Criterion | Covered By |
|----------------|-----------|
| CC6.1 (logical access) | Rule file signing + DID auth |
| CC6.7 (restricted transmission) | Capability `network_egress` whitelist |
| CC7.2 (system monitoring) | Provenance ledger + replay determinism |
| CC8.1 (change management) | Content-addressed releases + changesets |
| A1.2 (availability) | FFDB quorum writes + Gray Code reversible state |
