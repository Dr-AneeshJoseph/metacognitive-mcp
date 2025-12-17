# Security Policy

## Scope

The Metacognitive MCP is an epistemic reasoning tool for AI agents. While it does not handle sensitive user data directly, security considerations apply to:

1. **Protocol Integrity**: Ensuring reasoning protocols cannot be manipulated
2. **Input Validation**: Preventing malformed inputs from causing unexpected behavior
3. **Dependency Security**: Managing risks from third-party packages
4. **Deployment Security**: Safe operation in production environments

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 0.1.x   | :white_check_mark: |

## Reporting a Vulnerability

### Where to Report

**Do NOT report security vulnerabilities through public GitHub issues.**

Instead, please report them via:
- Email: aneeshjoseph1091@gmail.com
- GitHub Security Advisories (preferred): Navigate to Security → Advisories → New draft security advisory

### What to Include

Please include:

1. **Description**: Clear explanation of the vulnerability
2. **Impact**: What an attacker could achieve
3. **Reproduction**: Step-by-step instructions to reproduce
4. **Affected Components**: Which files/functions are involved
5. **Suggested Fix**: If you have one (optional)

### Response Timeline

- **Acknowledgment**: Within 48 hours
- **Initial Assessment**: Within 7 days
- **Resolution Target**: Within 30 days for critical issues

### What to Expect

1. We will acknowledge receipt of your report
2. We will investigate and assess the impact
3. We will work on a fix and coordinate disclosure timing with you
4. We will credit you in the security advisory (unless you prefer anonymity)

## Security Considerations

### Input Handling

The MCP accepts queries from AI agents. Consider:

```python
# All inputs should be validated
Query(content="...")  # Validated in __post_init__

# Protocols should not execute arbitrary code from inputs
# Protocols should handle malformed inputs gracefully
```

### Protocol Security

Epistemic protocols should:

1. **Never execute code** derived from query content
2. **Validate all inputs** before processing
3. **Return errors gracefully** rather than crashing
4. **Not leak internal state** in error messages

### Dependency Management

- Pin dependency versions in `pyproject.toml`
- Regularly audit dependencies with `pip-audit`
- Use only well-maintained, reputable packages

### Deployment Recommendations

When deploying the Metacognitive MCP:

1. **Run with minimal privileges**: Don't run as root
2. **Isolate the service**: Use containers or VMs
3. **Monitor logs**: Watch for unusual patterns
4. **Rate limit**: Prevent abuse from excessive calls
5. **Keep updated**: Apply security patches promptly

## Known Security Considerations

### Pattern Matching in Bias/Fallacy Detection

The bias and fallacy detection protocols use regex pattern matching. While these cannot execute arbitrary code, carefully crafted inputs could potentially:

- Cause excessive processing time (ReDoS)
- Trigger false positives/negatives

**Mitigation**: Input length limits and pattern timeouts are recommended for production use.

### No Authentication

The MCP protocol itself does not include authentication. Access control must be implemented at the transport layer:

- Use Claude Desktop's built-in security model
- Implement authentication in any custom MCP client
- Restrict network access to the MCP server

## Security Best Practices for Contributors

When contributing code:

1. **Never log sensitive data**: Avoid logging full query contents in production
2. **Validate inputs**: Check types and ranges
3. **Handle errors safely**: Don't expose internal details
4. **Avoid dynamic code execution**: No `eval()`, `exec()`, or similar
5. **Review dependencies**: Check security status before adding new deps

## Acknowledgments

We thank security researchers who responsibly disclose vulnerabilities. Contributors will be acknowledged in security advisories unless they prefer otherwise.

---

*Security is a shared responsibility. Thank you for helping keep this project safe.*
