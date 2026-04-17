# aegis CLI v0.1 (spec)

Stub spec. Implementation lands in v0.2.

## Commands

### classify
```bash
aegis classify --brief "SOC2 compliant AI runtime for 500-person fintech"
# -> { domain: enterprise, compliance: soc2, budget_band: enterprise, ... }
```

### route
```bash
aegis route --input-shape=shape.json
aegis route --input-shape=shape.json --explain   # human-readable decision narrative
# -> world=NATL + trace
```

### compose
```bash
aegis compose --world=NATL
aegis compose --world=NATL --replay-from=01H...ULID    # deterministic replay
# -> manifest with hash-pinned nodes + cogs + signed provenance record
```

### inspect
```bash
aegis inspect worlds
aegis inspect nodes
aegis inspect capabilities
aegis inspect rule-file
```

### cogs
```bash
aegis cogs --world=NATL --volume=100000
# -> { per_request_usd: 0.041, per_month_p99_usd: 4100, margin_pct: 83.1, floor_rec: 249 }
```

### verify
```bash
aegis verify rules       # checks signature on rules/v0_1.yaml
aegis verify node ffdb   # checks artifact_sha256 matches installed binary
aegis verify replay <decision_id>   # re-runs decision, asserts byte-equal manifest
```
