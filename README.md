# rhythmictech/.github

Org-level GitHub configuration — reusable CI workflows for supply chain security.

## Reusable Workflows

| Workflow | What | Fails on |
|----------|------|----------|
| `supply-chain-gate` | Registry config, SHA pinning, Dockerfile FROM | Missing/wrong .npmrc, public PyPI refs, tag-pinned actions |
| `vuln-scan` | Grype + osv-scanner (parallel, independent runners) | High/critical vulnerabilities |
| `secret-scan` | TruffleHog (full history, verified secrets only) | Verified secrets in git history |

### Usage

Add to any repo's CI workflow:

```yaml
# .github/workflows/ci.yml
name: CI
on: [pull_request]

jobs:
  supply-chain-gate:
    uses: rhythmictech/.github/.github/workflows/supply-chain-gate.yml@main
    with:
      nexus_hostname: nexus.rhythmic.tools

  vuln-scan:
    uses: rhythmictech/.github/.github/workflows/vuln-scan.yml@main

  secret-scan:
    uses: rhythmictech/.github/.github/workflows/secret-scan.yml@main
```

All three run in parallel. No secrets needed.

### Self-hosted runners

All workflows accept a `runs_on` input (default: `ubuntu-latest`):

```yaml
  vuln-scan:
    uses: rhythmictech/.github/.github/workflows/vuln-scan.yml@main
    with:
      runs_on: cicd
```

### Pre-commit (detect-secrets)

For local secret detection, add to each repo:

```bash
pip install pre-commit detect-secrets
```

Create `.pre-commit-config.yaml`:

```yaml
repos:
  - repo: https://github.com/Yelp/detect-secrets
    rev: v1.5.0
    hooks:
      - id: detect-secrets
        args: ['--baseline', '.secrets.baseline']
```

Then:

```bash
detect-secrets scan > .secrets.baseline
pre-commit install
```

## Related

- [rhythmic-security](https://github.com/rhythmictech/rhythmic-security) — IaC for Cloudflare, device posture, Datadog
- [CI/CD Supply Chain Security Architecture](https://github.com/rhythmictech/rhythmic-security/blob/main/cicd-architecture-design.md) — full design doc
