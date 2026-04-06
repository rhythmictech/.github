# Rhythmic

[Rhythmic](https://rhythmictech.com) is an AWS Advanced Tier Partner specializing in cloud infrastructure, security, and DevOps.

We build and maintain open source Terraform modules for the AWS ecosystem.

## Reusable Workflows

This repository provides reusable GitHub Actions workflows for Terraform module CI:

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
