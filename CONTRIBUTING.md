# Contributing to KRILL

Thanks for your interest in KRILL. This project is at the research/specification stage — there is no working implementation yet. That means **every contribution matters**.

## How to Contribute

### 1. Read the documents first

- [Research Paper](docs/KRILL-BIA-Research-Paper.pdf) — understand the "why" and the theory
- [Engineering Spec](docs/KRILL-BIA-Engineering-Spec.pdf) — understand the "how" and the byte-level details

### 2. Pick an area

| Area | Skills needed | Priority |
|---|---|---|
| **Core firmware** | Rust or C, embedded development, ESP32/nRF52 | Highest |
| **Simulation** | Python/Rust, agent-based modeling | High |
| **Security review** | Cryptography, formal methods | High |
| **Hardware testing** | ESP32/nRF52 boards, BLE/LoRa experience | Medium |
| **Documentation** | Technical writing, diagrams | Medium |
| **Translations** | Any language + technical understanding | Welcome |

### 3. Start with an Issue

- Check [existing issues](../../issues) before starting work
- For new ideas, open an issue first to discuss before writing code
- Issues labeled `good first issue` are specifically scoped for newcomers

### 4. Submit a Pull Request

- Fork the repo
- Create a feature branch (`git checkout -b feature/pheromone-field`)
- Keep PRs focused — one feature or fix per PR
- Include tests where applicable
- Reference the relevant Engineering Spec section (e.g., "Implements ES-3.2")

## MVP Implementation Roadmap

If you want to build the first working KRILL node, here's the suggested order:

```
1. ES-13  Cryptographic enrollment (PUF + Ed25519)
2. ES-12  Transport layer (BLE mesh)
3. ES-1   Core data types and wire formats
4. ES-3   Stigmergic Consensus (core algorithm)
5. ES-10  Main event loop
6. ES-4   Immune System (basic innate layer)
7. ES-5   Metabolic State (pheromone decay)
8. ES-7   Quorum Sensing
```

Steps 1-5 give you a working node that can participate in consensus. Steps 6-8 add resilience.

## Code Style

- **Rust** preferred for firmware (no_std compatible for nRF52)
- **C** acceptable for ESP-IDF targets
- **Python** for simulations and tooling
- Follow existing style in the repo
- Comment non-obvious logic, especially anything referencing the spec

## Reporting Bugs / Security Issues

- Regular bugs: open a GitHub issue
- **Security vulnerabilities**: email privately first (do NOT open a public issue). Contact details in the issue template.

## Code of Conduct

Be respectful. Be constructive. Focus on the work. We're building something that doesn't exist yet — disagreement is expected and welcome, hostility is not.

## Questions?

Open a [Discussion](../../discussions) thread. No question is too basic.
