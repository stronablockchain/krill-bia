# KRILL — Bio-Inspired Architecture for IoT Consensus

> Decentralized IoT consensus without blockchain — inspired by ant colonies, immune systems & chemical diffusion.

---

## What is KRILL?

**The problem:** Blockchain doesn't work for IoT. It's too heavy, too slow, and too expensive for devices running on batteries with 32KB of RAM. IoT needs to answer "What is the physical state of the world?" — not "Who has how much money?"

**The solution:** KRILL replaces blockchain with 9 mechanisms borrowed from biology:

| Mechanism | Biological inspiration | What it does |
|---|---|---|
| Stigmergic Consensus | Ant pheromone trails | Nodes "deposit" readings like ants deposit pheromones. Truth emerges from convergence, not voting. |
| Pentastratic Immune System | Human immune layers | 5-layer anomaly detection: skin (format check) → innate (statistical) → adaptive (learned) → NK audit → autoimmune suppression. |
| Metabolic State | Cell metabolism | Data has a "half-life" — old readings decay and die automatically. No infinite ledger. |
| Entropic Data Valuation | Thermodynamic entropy | Network autonomously decides which data is worth storing based on information theory. |
| Quorum Sensing | Bacterial quorum sensing | Nodes detect local density and switch modes (solo → quorum → swarm) without any coordinator. |
| Horizontal Gene Transfer | Bacterial gene sharing | Firmware updates spread node-to-node like genes between bacteria. No update server needed. |
| Morphogenetic Topology | Embryonic development | Network self-organizes its topology using reaction-diffusion (Turing patterns). |
| Thymic Tolerance | T-cell training in thymus | System learns what "normal" looks like to avoid false alarms. |
| Immunological Memory | Vaccine/antibody memory | Once the network detects an attack pattern, it "vaccinates" all nodes. |

**The result:**
- **1000x less energy** than blockchain consensus
- Runs on a **$2 ESP32** microcontroller (240KB RAM)
- Works with **intermittent connectivity** (mesh, BLE, LoRa, WiFi)
- **No miners, no staking, no tokens** — consensus is grounded in physical reality
- Scales to **millions of nodes** without coordinator

**Status:** Research paper + engineering specification. No working implementation yet.

---

## Documents

| Document | Description |
|---|---|
| [Research Paper (HTML)](KRILL-BIA-Research-Paper.html) | Full academic paper — mathematical formalizations, energy analysis, novelty assessment, risk analysis. 20 sections. Open in browser → Print → Save as PDF. |
| [Engineering Specification (HTML)](KRILL-BIA-Engineering-Spec.html) | Implementation reference — byte-level wire formats, state machines, pseudocode, test vectors, transport layers. Ready to code from. |

Source files (Markdown):
- [`krill-bioinspired-architecture.md`](krill-bioinspired-architecture.md) — Research paper
- [`krill-bia-engineering-spec.md`](krill-bia-engineering-spec.md) — Engineering spec

---

## Architecture at a Glance

```
┌─────────────────────────────────────────────────────────┐
│                    KRILL Node (ESP32)                    │
├──────────┬──────────┬──────────┬──────────┬─────────────┤
│ Stigmer- │ Immune   │ Metabolic│ Quorum   │ Morpho-     │
│ gic      │ System   │ State    │ Sensing  │ genetic     │
│ Consensus│ (5-layer)│ (decay)  │ (modes)  │ Topology    │
├──────────┴──────────┴──────────┴──────────┴─────────────┤
│              Transport: BLE mesh / WiFi / LoRa          │
├─────────────────────────────────────────────────────────┤
│         PUF Identity + Ed25519 Enrollment               │
└─────────────────────────────────────────────────────────┘
```

---

## MVP — Where to Start

If you want to implement KRILL, start with these 4 subsystems (the rest can be added later):

1. **ES-13** — Cryptographic enrollment (PUF + Ed25519 identity)
2. **ES-12** — Transport layer (BLE mesh for local, WiFi for bridging)
3. **ES-1** — Core data types and wire formats
4. **ES-3** — Stigmergic Consensus (the core algorithm)
5. **ES-10** — Main event loop and message dispatch

Target hardware: **ESP32** (Nano node) + **nRF52840** (Dust node, optional)

---

## Why Not Blockchain?

| | Blockchain (e.g. Ethereum) | KRILL-BIA |
|---|---|---|
| **Consensus energy** | ~50 Wh/tx (PoW) or ~0.01 Wh/tx (PoS) | ~0.00001 Wh/tx |
| **Minimum RAM** | 512MB+ | 32KB (Dust), 240KB (Nano) |
| **State growth** | Infinite (append-only) | Bounded (data decays) |
| **Offline tolerance** | Minutes before fork | Days (pheromone half-life) |
| **Hardware cost** | $50+ SBC | $2 ESP32 |
| **Finality** | Probabilistic (blocks) | Convergent (pheromone field) |

---

## Key Innovation: Physical-World Consensus Grounding

Unlike blockchain where consensus is purely computational, KRILL grounds consensus in **physical reality**:

- Sensor readings must be **physically plausible** (a thermometer can't jump 50C in 1 second)
- Nodes that are **physically closer** have more weight (radio signal strength = distance proxy)
- The **laws of physics** constrain what values are possible — this is a defense layer that doesn't exist in financial systems

This means an attacker must not only compromise the software but also **defeat physics** — a fundamentally harder problem.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to get involved.

Areas where help is most needed:
- **Rust/C firmware** for ESP32 (core protocol implementation)
- **Simulation** — model pheromone convergence with 100-10,000 virtual nodes
- **Hardware testing** — BLE mesh range, LoRa timing, PUF enrollment on real chips
- **Security review** — formal verification of immune system thresholds
- **Documentation** — diagrams, tutorials, translations

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Supporting This Work

If KRILL is useful to your research or organization, consider supporting further development:

**ETH / ERC-20 / Base / Arbitrum / Polygon:**
```
0x0BC290355c0B16B5B247701B7BC9AB2E1e61ffa7
```

Funds go toward:
- Reference firmware for ESP32 + nRF52840
- Hardware test beds (100-node BLE mesh)
- Independent security audits
- Bug bounty program for protocol vulnerabilities

Code contributions are equally welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).
