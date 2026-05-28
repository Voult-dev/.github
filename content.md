# Voult `.github` Repository Structure

```txt
.github/
├── profile/
│   └── README.md
├── ISSUE_TEMPLATE/
│   ├── bug_report.yml
│   ├── feature_request.yml
│   └── config.yml
├── PULL_REQUEST_TEMPLATE.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── SECURITY.md
├── SUPPORT.md
├── FUNDING.yml
├── dependabot.yml
└── workflows/
    ├── ci.yml
    ├── codeql.yml
    └── stale.yml
```

---

# 1. profile/README.md

This becomes the public organization homepage on GitHub.

```md
# Voult.dev

Developer-first authentication infrastructure for modern applications.

Voult provides secure, scalable, and easy-to-integrate authentication APIs so developers can focus on building products instead of rebuilding auth systems.

## Features

- Authentication APIs
- Session Management
- OAuth Providers
- Email Verification
- Password Reset Flows
- Magic Links
- JWT Infrastructure
- Security Tooling
- Developer SDKs

## Links

- Website: https://voult.dev
- Documentation: https://docs.voult.dev
- Status Page: https://status.voult.dev

## Repositories

| Repository | Description |
|---|---|
| voult | Main authentication platform |
| voult-landing | Marketing/landing page |
| docs | Documentation |
| sdk-js | JavaScript SDK |
| examples | Example integrations |

## Mission

Build authentication infrastructure developers actually enjoy using.
```

---

# 2. ISSUE_TEMPLATE/bug_report.yml

```yml
name: Bug Report
description: Report a bug or unexpected behavior
title: "[Bug]: "
labels: ["bug"]

body:
  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe the issue clearly.
    validations:
      required: true

  - type: textarea
    id: reproduction
    attributes:
      label: Steps to Reproduce
    validations:
      required: true

  - type: textarea
    id: expected
    attributes:
      label: Expected Behavior

  - type: input
    id: environment
    attributes:
      label: Environment
      placeholder: Node.js version, browser, OS, etc.
```

---

# 3. ISSUE_TEMPLATE/feature_request.yml

```yml
name: Feature Request
description: Suggest a new feature
title: "[Feature]: "
labels: ["enhancement"]

body:
  - type: textarea
    id: problem
    attributes:
      label: Problem
      description: What problem does this solve?
    validations:
      required: true

  - type: textarea
    id: solution
    attributes:
      label: Proposed Solution
```

---

# 4. ISSUE_TEMPLATE/config.yml

```yml
blank_issues_enabled: false

contact_links:
  - name: Security Reports
    url: mailto:security@voult.dev
    about: Please report security vulnerabilities privately.
```

---

# 5. PULL_REQUEST_TEMPLATE.md

```md
## Summary

Describe the changes made.

## Changes

- 
- 
- 

## Testing

- [ ] Tested locally
- [ ] Added/updated tests
- [ ] No breaking changes

## Screenshots (if applicable)

Add screenshots here.
```

---

# 6. CONTRIBUTING.md

````md
# Contributing to Voult

Thank you for contributing.

## Setup

```bash
git clone https://github.com/Voult-dev/voult.git
cd voult
npm install
````

## Branch Naming

* feature/*
* fix/*
* chore/*
* docs/*

## Commit Style

Use conventional commits:

```txt
feat:
fix:
docs:
refactor:
test:
```

## Pull Requests

* Keep PRs focused
* Add tests where applicable
* Ensure linting passes

````

---

# 7. SECURITY.md

```md
# Security Policy

## Reporting Vulnerabilities

Please report security vulnerabilities privately.

Email:
security@voult.dev

Do not open public GitHub issues for security vulnerabilities.

## Supported Versions

| Version | Supported |
|---|---|
| Latest | Yes |
````

---

# 8. CODE_OF_CONDUCT.md

```md
# Code of Conduct

Be respectful and constructive.

Harassment, discrimination, or abusive behavior will not be tolerated.

## Enforcement

Contact:
samuel@voult.dev
```

---

# 9. SUPPORT.md

```md
# Support

## Documentation

https://docs.voult.dev

## Contact

support@voult.dev

## Security

security@voult.dev
```

---

# 10. FUNDING.yml

```yml
github: DevOlabode
```

---

# 11. dependabot.yml

```yml
version: 2

updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
```

---

# 12. workflows/ci.yml

```yml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20

      - run: npm install
      - run: npm run lint
      - run: npm test
```

---

# 13. workflows/codeql.yml

```yml
name: CodeQL

on:
  push:
  pull_request:
  schedule:
    - cron: '0 0 * * 0'

jobs:
  analyze:
    runs-on: ubuntu-latest

    permissions:
      security-events: write

    strategy:
      fail-fast: false
      matrix:
        language: ['javascript']

    steps:
      - uses: actions/checkout@v4

      - uses: github/codeql-action/init@v3
        with:
          languages: ${{ matrix.language }}

      - uses: github/codeql-action/analyze@v3
```

---

# 14. workflows/stale.yml

```yml
name: Mark Stale Issues

on:
  schedule:
    - cron: "0 0 * * *"

jobs:
  stale:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/stale@v9
        with:
          stale-issue-message: "This issue has gone stale."
          days-before-stale: 30
          days-before-close: 7
```

---

# Additional Recommended Repositories

```txt
Voult-dev/
├── voult
├── voult-landing
├── docs
├── sdk-js
├── sdk-node
├── examples
├── playground
└── .github
```

---

# Recommended Organization Settings

## Enable

* Dependabot alerts
* Dependabot security updates
* Secret scanning
* Push protection
* Private vulnerability reporting
* Branch protection rules

## Branch Protection

Protect:

* main
* production

Require:

* PR reviews
* status checks
* no force pushes
* signed commits (optional later)

```
```
