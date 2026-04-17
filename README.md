# aegis

**NEURUH ROUTER + Convergence Protocol world-composer.**

Heterogeneous inputs funnel to aligned terminal states. Aegis is the selection engine that maps input shape to a world and assembles the required atomic nodes on demand.

## What This Is

The flagship node of the Neuruh system. Every seeder repo (StormStack, REI-X, DISPATCH-IQ, AXON, PMLA, TaxShield, etc.) is an on-ramp. Aegis is the merge geometry that funnels any input to the correct destination world.

## Core Concepts

- **Input Shape** — typed classification of any incoming brief (domain, volume, compliance, urgency, budget)
- **Atomic Node** — single-purpose primitive with a stable typed contract
- **Layer** — tier of nodes at the same abstraction level (L0 Substrate through L5 Surface)
- **World** — named terminal destination state that selects a specific subset of nodes
- **Router** — the selection engine (this repo)
- **Seed** — an on-ramp, any seeder repo that produces a valid input shape

## Six Layers

| # | Layer | Nodes |
|---|-------|-------|
| L0 | Substrate | ether-layer |
| L1 | State | gray-code-state, ffdb |
| L2 | Memory | mucs, spc |
| L3 | Security | nsec, ether-rbac |
| L4 | Orchestration | ipp-mcb, pmla-cap |
| L5 | Surface | world package |

## Five Worlds

| World | Destination |
|-------|-------------|
| NATL | Compliant enterprise runtime |
| AXIOM | White-labeled AI-CTO delivery |
| Signal-IQ | Real-estate intelligence feed |
| TaxShield | Tax + audit compliance state |
| Aegis | Meta: composes new worlds from input shapes |

## Usage

```bash
# Classify an input
aegis classify --brief "SOC2 compliant AI runtime for 500-person fintech"
# Output: { domain: enterprise, compliance: soc2, budget: enterprise }

# Route to world
aegis route --input-shape=shape.json
# Output: world=NATL

# Compose runtime stack
aegis compose --world=NATL
# Output: manifest with ether-layer@0.1.0, gray-code-state@0.1.0, ffdb@0.1.0, ...
```

## Spec

Canonical spec lives in Notion: NEURUH ROUTER — Convergence Protocol Spec v0.1.
Obsidian mirror: `~/neuruh-vault/04-INTELLIGENCE/convergence-protocol/SPEC.md`.
This repo carries the executable version.

## Status

v0.1 MVP scaffold. Rules file at `rules/v0_1.yaml`. Node registry at `nodes/registry.yaml`. Demo CLI TBD.

## License

Apache 2.0
