# Contributing to UTMS

Thank you for your interest in improving the Urban Traffic Management System! This document outlines how to contribute effectively.

---

## Ways to Contribute

- **Bug reports** — Open a GitHub Issue with reproduction steps
- **Feature requests** — Describe the use case and expected behavior
- **Code contributions** — Submit a Pull Request (see workflow below)
- **Documentation** — Fix typos, improve examples, translate content
- **Research** — Share traffic engineering papers or dataset sources

---

## Development Workflow

### 1. Fork & Clone

```bash
git clone https://github.com/YOUR_USERNAME/urban-traffic-management.git
cd urban-traffic-management
git remote add upstream https://github.com/your-org/urban-traffic-management.git
```

### 2. Create a Feature Branch

Use the naming convention:

| Type | Pattern | Example |
|---|---|---|
| Feature | `feature/short-description` | `feature/adaptive-signal-v2` |
| Bug fix | `fix/issue-number-description` | `fix/42-heartbeat-timeout` |
| Documentation | `docs/topic` | `docs/api-authentication` |
| Refactor | `refactor/module-name` | `refactor/sensor-manager` |

```bash
git checkout -b feature/your-feature-name
```

### 3. Set Up Development Environment

```bash
python -m venv venv
source venv/bin/activate         # Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install -e ".[dev]"
```

### 4. Make Your Changes

Follow our coding standards:

- **Python**: PEP 8, type hints on all public functions, docstrings (Google style)
- **Commits**: Conventional Commits format (`feat:`, `fix:`, `docs:`, `test:`, `refactor:`)
- **Tests**: Every new function should have at least one corresponding test

### 5. Run Tests & Linting

```bash
# Lint
ruff check src/ tests/
black src/ tests/
mypy src/ --ignore-missing-imports

# Tests
pytest tests/ -v --cov=src

# Security scan
bandit -r src/ -ll
```

All checks must pass before submitting a PR.

### 6. Open a Pull Request

- Use a clear, descriptive title
- Reference any related issues: `Closes #42`
- Fill out the PR template (auto-populated)
- Ensure CI is green before requesting review

---

## Code Standards

### Docstrings

```python
def compute_optimal_phase(self, state: IntersectionState) -> PhaseDecision:
    """
    Compute the optimal next signal phase and duration.

    Args:
        state: Current intersection sensor reading.

    Returns:
        PhaseDecision with recommended phase, duration, and confidence.

    Raises:
        RuntimeError: If no state has been loaded via update_state().
    """
```

### Commit Messages

```
feat: add multi-phase signal coordination for 4-way intersections
fix: prevent heartbeat timeout on initial sensor registration
docs: update API authentication section with JWT examples
test: add integration tests for emergency vehicle override
refactor: extract Webster cycle formula into utility module
```

---

## Reporting Security Issues

**Do not open public Issues for security vulnerabilities.**

Email `security@utms.dev` with:
- Description of the vulnerability
- Steps to reproduce
- Potential impact assessment

We aim to respond within 48 hours and provide a fix within 14 days.

---

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to uphold a welcoming and respectful community.

---

## Questions?

Open a [Discussion](https://github.com/your-org/urban-traffic-management/discussions) or email `dev@utms.dev`.
