# Contributing

Contributions are welcome through focused issues and pull requests.

## Development setup

1. Read the README and the issue you plan to address.
2. Fork or branch from the default branch using a short, descriptive branch name.
3. Keep changes scoped to one problem and avoid committing credentials or production data.
4. Document any new environment variable with a safe example value.

Runtime-specific setup commands will be added with the v0.1 implementation.

## Code style

- Use the formatter and linter selected by the repository.
- Prefer explicit, versioned contracts at service boundaries.
- Keep logs structured and free of secrets, raw proxy lists, and unnecessary IP data.
- Add comments for policy or compatibility decisions, not for obvious code.

## Pull requests

- Link the relevant issue.
- Describe behavior, compatibility, security, and operational impact.
- Keep generated files reproducible and identify the source.
- Update CHANGELOG.md for user-visible changes.
- Request review before merging.

## Testing

- Add unit tests for new behavior and regression tests for fixes.
- Add contract tests when a schema or message changes.
- Run all checks documented by the repository and report anything skipped.
- Never use live credentials, private proxy lists, or production endpoints in tests.

## Documentation

Update README, configuration tables, examples, and cross-repository links in the same pull request as the behavior they describe.
