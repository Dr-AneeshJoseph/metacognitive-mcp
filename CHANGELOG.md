# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Evidence integration with external knowledge bases
- Domain-specific protocol variants
- Multi-agent epistemic coordination
- Confidence calibration feedback loops

## [0.1.0] - 2024-12-17

### Added
- **Core Types** (`types.py`)
  - `EpistemicResponse` dataclass with full epistemic closure
  - `Query`, `Evidence`, `InferenceStep`, `CounterClaim` data structures
  - `EpistemicStatus` enum (verified, probable, contested, unknown, unfalsifiable)
  - Validation in `__post_init__` for all data structures

- **Protocol Infrastructure**
  - `BaseProtocol` abstract base class defining uniform interface
  - `ProtocolRegistry` for conditional-free tool dispatch
  - MCP server shell with stdio transport

- **Epistemic Protocols**
  - `grounded_reasoning`: Structured epistemic analysis with evidence, inference chains, and counter-claims
  - `adversarial_stress_test`: Attack claims from hostile perspectives
  - `detect_cognitive_biases`: Scan for confirmation bias, anchoring, availability heuristic, false dichotomy, appeal to authority, sunk cost fallacy
  - `decompose_question`: Break complex queries into atomic sub-questions with dependency mapping
  - `validate_inference`: Detect formal fallacies (affirming consequent, denying antecedent, undistributed middle) and informal fallacies (ad hominem, straw man, red herring, circular reasoning)

- **Documentation**
  - Theory of Operation explaining architectural principles
  - Module specifications for distributed development
  - Contributing guidelines
  - Security policy

### Design Principles
- Epistemic closure invariant: every output contains everything needed to evaluate its validity
- Structural enforcement: data structures make incomplete outputs impossible
- Uniform protocol interface: all protocols share Query → EpistemicResponse signature
- Separation of concerns: transport, registry, and protocol layers are independent

---

## Version History Summary

| Version | Date | Highlights |
|---------|------|------------|
| 0.1.0 | 2024-12-17 | Initial release with 5 epistemic protocols |

[Unreleased]: https://github.com/YOUR_USERNAME/metacognitive-mcp/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/YOUR_USERNAME/metacognitive-mcp/releases/tag/v0.1.0
