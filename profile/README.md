# Rhythmic

[Rhythmic](https://rhythmictech.com) is an AI and cloud infrastructure company specialized in complex, autonomous systems. We build and maintain a variety of public projects, including IaC modules/libraries, demonstration projects, helper tools and libraries, and services that are relevant to anyone building modern systems.

## Reusable Workflows

This repository provides reusable GitHub Actions workflows for IaC CI:

| Workflow | Purpose |
|----------|---------|
| `module-pr.yml` | All-in-one PR checks for Terraform modules |
| `terraform-module-ci.yml` | Format, validate, lint, and test |
| `terraform-docs.yml` | Auto-generate and commit module documentation |
| `terraform-security.yml` | Checkov + Trivy security scanning |
| `lint-general.yml` | Misspell, YAML lint, Action lint, Markdown lint |
| `secret-scan.yml` | TruffleHog verified secret detection |
| `dependency-review.yml` | GitHub dependency review |
| `scorecard.yml` | OpenSSF Scorecard |

### Usage

Add a single workflow to your Terraform module repo:

```yaml
# .github/workflows/ci.yml
name: CI
on: [pull_request]
jobs:
  checks:
    uses: rhythmictech/.github/.github/workflows/module-pr.yml@main
```

See the [configs/](configs/) directory for recommended `.tflint.hcl`, `.terraform-docs.yml`, and `.checkov.yml` files.
