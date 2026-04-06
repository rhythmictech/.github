# Contributing to Rhythmic Open Source

Thank you for your interest in contributing. We welcome pull requests from the community.

## Getting Started

1. **Fork** the repository.
2. **Clone** your fork locally.
3. **Create a branch** from `master` using the naming convention `<type>/<short-description>` (e.g., `fix/output-name`, `feat/add-tags-variable`).
4. **Make your changes** and commit using [Conventional Commits](https://www.conventionalcommits.org/) format.
5. **Open a pull request** against `master`.

## Development Workflow

### Prerequisites

- Install pre-commit hooks.
- Do not bypass them.
- Test code before shipping, AI slop submissions will be rejected without review.
- For projects where test suites are available, ensure appropriate tests are created.
- 
### Documentation

DO update any documentation impacted by your changes.

Do not manually edit automatically generated content, such as between the `<!-- BEGIN_TF_DOCS -->` and `<!-- END_TF_DOCS -->` markers for terraform repos. The CI pipeline will regenerate and commit documentation automatically on PR.

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

Open an issue or reach out to the maintainers at opensource@rhythmictech.com.
