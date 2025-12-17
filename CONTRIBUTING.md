# Contributing to Metacognitive MCP

Thank you for your interest in contributing to the Metacognitive MCP project. This document provides guidelines for contributions.

## Project Philosophy

Before contributing, please understand the core principles that guide this project:

1. **Structure over Behavior**: The architecture enforces correctness through data structures, not runtime checks
2. **Epistemic Closure Invariant**: Every output must be self-evaluating—containing everything needed to assess its validity
3. **Separation of Concerns**: Transport logic (MCP) is strictly separated from epistemic logic (protocols)

## How to Contribute

### Reporting Issues

- **Bug Reports**: Include minimal reproduction steps, expected vs actual behavior, and your environment
- **Feature Requests**: Describe the use case, proposed solution, and how it aligns with project philosophy
- **Documentation Issues**: Point to specific sections that are unclear or incorrect

### Code Contributions

#### Before You Start

1. Check existing issues and PRs to avoid duplicate work
2. For significant changes, open an issue first to discuss the approach
3. Read the architecture documents in `/docs` to understand the design

#### Development Setup

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/metacognitive-mcp.git
cd metacognitive-mcp

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install in development mode
pip install -e ".[dev]"

# Run tests
pytest
```

#### Code Standards

**All code must:**

1. **Maintain the invariant**: Every `EpistemicResponse` must have all required fields populated
2. **Use type hints**: Full type annotations compatible with mypy
3. **Include docstrings**: Explain what, why, and how
4. **Follow existing patterns**: Match the style of surrounding code

**For new protocols:**

1. Inherit from `BaseProtocol`
2. Implement `name`, `description`, and `execute()`
3. Return complete `EpistemicResponse` for all inputs
4. Never return confidence of exactly 0.0 or 1.0
5. Include at least 2 uncertainties and 1 counter-claim

#### Commit Messages

Use conventional commits:

```
feat: add new protocol for temporal reasoning
fix: correct confidence calibration in bias detection
docs: clarify invariant requirements in CONTRIBUTING
refactor: simplify inference chain construction
test: add edge case tests for decomposition protocol
```

#### Pull Request Process

1. **Fork** the repository
2. **Create a branch** from `main`: `git checkout -b feat/your-feature`
3. **Make changes** following the code standards
4. **Test thoroughly**: Run `pytest` and verify invariants
5. **Update documentation** if needed
6. **Submit PR** with clear description of changes

#### PR Checklist

- [ ] Code follows project style and philosophy
- [ ] All tests pass
- [ ] New code has appropriate test coverage
- [ ] Documentation updated if needed
- [ ] Commit messages follow conventions
- [ ] PR description explains the change and motivation

### Adding New Protocols

New epistemic protocols are welcome! To propose one:

1. **Open an issue** describing:
   - The cognitive/epistemic function it serves
   - How it differs from existing protocols
   - Proposed algorithm specification
   
2. **Get feedback** before implementing

3. **Implement** following the existing protocol structure:
   ```python
   class YourProtocol(BaseProtocol):
       @property
       def name(self) -> str:
           return "your_protocol_name"
       
       @property
       def description(self) -> str:
           return "What this protocol does"
       
       def execute(self, query: Query) -> EpistemicResponse:
           # Your implementation
           pass
   ```

4. **Register** in `registry.py`

5. **Document** with a MODULE specification document

### Documentation Contributions

Documentation improvements are highly valued:

- Fix typos and clarify confusing passages
- Add examples and use cases
- Improve the theory of operation document
- Translate documentation (coordinate via issue first)

## Code of Conduct

### Our Standards

- Be respectful and inclusive
- Focus on constructive feedback
- Assume good intentions
- Acknowledge different perspectives and experiences

### Unacceptable Behavior

- Harassment, discrimination, or personal attacks
- Trolling or inflammatory comments
- Publishing others' private information
- Other conduct inappropriate in a professional setting

### Enforcement

Violations may be reported to the maintainers. All complaints will be reviewed and investigated, resulting in appropriate response.

## Recognition

Contributors will be recognized in:
- The CONTRIBUTORS file
- Release notes for significant contributions
- Academic citations where appropriate (see CITATION.cff)

## Questions?

- Open a GitHub Discussion for general questions
- Open an Issue for specific problems
- Contact maintainers for sensitive matters

---

*Thank you for helping build epistemic infrastructure for AI agents.*
