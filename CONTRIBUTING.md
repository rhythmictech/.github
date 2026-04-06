# Contributing to Rhythmic Terraform Modules

Thank you for your interest in contributing. We welcome pull requests from the community.

## Getting Started

1. **Fork** the repository.
2. **Clone** your fork locally.
3. **Create a branch** from `main` using the naming convention `<type>/<short-description>` (e.g., `fix/output-name`, `feat/add-tags-variable`).
4. **Make your changes** and commit using [Conventional Commits](https://www.conventionalcommits.org/) format.
5. **Open a pull request** against `main`.

## Development Workflow

### Prerequisites

- [Terraform](https://www.terraform.io/downloads) (version specified in the module)
- [TFLint](https://github.com/terraform-linters/tflint)
- [terraform-docs](https://terraform-docs.io/)

### Before Submitting

1. **Format:** Run `terraform fmt -recursive` to ensure consistent formatting.
2. **Validate:** Run `terraform init -backend=false && terraform validate` to check syntax.
3. **Lint:** Run `tflint` with the config from this repo's `configs/.tflint-module.hcl`.
4. **Test:** If the module includes tests, run `terraform test`.

### Documentation

README files are **auto-generated** by terraform-docs. Do not manually edit content between the `<!-- BEGIN_TF_DOCS -->` and `<!-- END_TF_DOCS -->` markers. The CI pipeline will regenerate and commit documentation automatically on PR.

To preview locally, copy `configs/.terraform-docs.yml` to your module root and run:

```bash
terraform-docs markdown table --config .terraform-docs.yml .
```

### Shared Configs

Reference configs are available in the [`configs/`](./configs/) directory:

- `.tflint-module.hcl` -- Standard TFLint configuration with AWS plugin
- `.terraform-docs.yml` -- terraform-docs output settings
- `.checkov.yml` -- Checkov security scanning defaults

## Pull Request Guidelines

- All PRs require at least one review before merging.
- Keep PRs focused on a single concern.
- CI checks must pass before merge.
- Write clear descriptions: what changed, why, and how to test.

## Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(module): add support for custom tags
fix(outputs): correct ARN output reference
docs: update examples for v3
chore: update provider version constraint
```

## Questions?

Open an issue or reach out to the maintainers listed in `CODEOWNERS`.
