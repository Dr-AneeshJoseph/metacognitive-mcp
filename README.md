# Metacognitive MCP

**Epistemic Infrastructure for AI Agents**

A Model Context Protocol (MCP) server that provides structured cognitive tools for AI reasoning. Unlike typical MCPs that fetch external data, this MCP provides *structured cognition*—protocols that help AI agents think more rigorously.

## Overview

The Metacognitive MCP functions as an **epistemic immune system** for AI agents. When an agent is uncertain about its reasoning, instead of hallucinating, it can call these protocols to structure its thinking.

### Available Tools

| Tool | Description |
|------|-------------|
| `grounded_reasoning` | Apply structured epistemic analysis with evidence, confidence calibration, and counter-claims |
| `adversarial_stress_test` | Attack claims from hostile perspectives to find weaknesses |
| `detect_cognitive_biases` | Scan reasoning for confirmation bias, anchoring, false dichotomy, etc. |
| `decompose_question` | Break complex queries into atomic sub-questions with dependencies |
| `validate_inference` | Check logical validity and detect formal/informal fallacies |

### Core Invariant

Every tool response is **epistemically closed**—it contains everything necessary to evaluate its own validity:

```json
{
  "claim": "The central assertion",
  "confidence": 0.75,
  "evidence": [...],
  "uncertainties": [...],
  "inference_chain": [...],
  "counter_claims": [...],
  "epistemic_status": "probable",
  "methodology": "How this analysis was conducted"
}
```

## Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/metacognitive-mcp.git
cd metacognitive-mcp

# Install dependencies
pip install -e .
```

## Usage

### With Claude Desktop

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "metacognitive": {
      "command": "python",
      "args": ["-m", "metacognitive_mcp.server"],
      "cwd": "/path/to/metacognitive-mcp"
    }
  }
}
```

### Standalone

```bash
python -m metacognitive_mcp.server
```

## Project Structure

```
metacognitive-mcp/
├── src/metacognitive_mcp/
│   ├── server.py           # MCP transport layer
│   ├── types.py            # Core data structures
│   ├── registry.py         # Protocol lookup
│   └── protocols/
│       ├── base.py         # Abstract base class
│       ├── grounded.py     # Grounded reasoning
│       ├── adversarial.py  # Adversarial testing
│       ├── bias.py         # Bias detection
│       ├── decomposition.py # Question decomposition
│       └── validation.py   # Inference validation
└── tests/
```

## Design Philosophy

This MCP embodies principles from master programmers:

- **Dijkstra**: Invariant-based design—the `EpistemicResponse` structure enforces completeness
- **Torvalds**: No conditionals in dispatch—all protocols share a uniform interface
- **Hickey**: Essential/incidental separation—epistemic logic is isolated from transport
- **Liskov**: Substitution through contracts—any protocol works where another is expected
- **Pike**: Data over code—the registry is a table of facts, not branching logic

## License

MIT

## Author

Dr. Aneesh Joseph (Conceptual Design)  
Claude (Architectural Design & Implementation Guidance)

---

*"The structure is the proof. The proof is the structure."*
