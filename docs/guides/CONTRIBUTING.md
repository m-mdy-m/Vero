# Contributing to Vero

Thank you for your interest in contributing to Vero! This document provides guidelines for contributing.

## [Code of Conduct](./CODE_OF_CONDUCT.md)

## Getting Started

__NOT_YET_CREATE__

## Development Workflow

### Branch Naming

- `feature/description` - New features
- `fix/description` - Bug fixes
- `docs/description` - Documentation
- `refactor/description` - Code refactoring
- `test/description` - Adding tests
- `chore/description` - Maintenance tasks

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
type(scope): description

[optional body]

[optional footer]
```

**Types:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation
- `style` - Formatting
- `refactor` - Code restructuring
- `test` - Adding tests
- `chore` - Maintenance

**Examples:**
```bash
git commit -m "feat(auth): add email verification"
git commit -m "fix(content): resolve markdown rendering issue"
git commit -m "docs(readme): update installation steps"
```

## Testing

__NOT_YET_CREATE__

## Code Style

### TypeScript

- Use TypeScript strict mode
- Add types for all parameters and return values
- Avoid `any` type unless absolutely necessary

```typescript
// Good
async function getUser(id: string): Promise<User> {
  // ...
}

// Avoid
async function getUser(id) {
  // ...
}
```

### Formatting

```bash
# Format code
npm run format

# Lint
npm run lint
```

Configuration:
- ESLint for linting
- Prettier for formatting
- Pre-commit hooks with Husky

## 🔍 Code Review

### Before Submitting PR

- [ ] Code follows style guidelines
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] All tests passing
- [ ] No linting errors
- [ ] Self-reviewed changes

### PR Guidelines

1. Keep PRs focused (one feature/fix per PR)
2. Write clear descriptions
3. Link related issues
4. Add screenshots for UI changes
5. Respond to review comments promptly

## Documentation

### Update Documentation

- Add JSDoc comments for functions
- Update README if needed
- Create/update ADRs for major decisions
- Update API documentation

### Writing ADRs

See [ADR template](../ADR/template.md) for guidance.

## Reporting Bugs

1. Check existing issues first
2. Use the [bug report template](../../.github/ISSUE_TEMPLATE/bug_report.yml)
3. Include reproduction steps
4. Provide error logs and screenshots

## Suggesting Features

1. Check existing feature requests
2. Use the [feature request template](../../.github/ISSUE_TEMPLATE/feature_request.yml)
3. Explain the problem and proposed solution
4. Consider offering to implement it

## Getting Help

- **Questions:** Open a [question issue](../../.github/ISSUE_TEMPLATE/question.yml)
- **Discussions:** Use GitHub Discussions
- **Email:** bitsgenix@gmail.com

## Security

- Report security issues via email: bitsgenix@gmail.com
- Do not create public issues for vulnerabilities
- Wait for confirmation before disclosing

## Thank You

Every contribution, no matter how small, is valuable!

---

**Questions?** Feel free to reach out:
- Email: bitsgenix@gmail.com
- GitHub: [@m-mdy-m](https://github.com/m-mdy-m)
- Website: [m-mdy-m.github.io](https://m-mdy-m.github.io)