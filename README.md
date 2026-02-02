# Project Template

> **Balancing Rock** - Universal project template for secure, fast development

[![CI](https://github.com/ShawnOwen/project-template/actions/workflows/pull-request-ci.yml/badge.svg)](https://github.com/ShawnOwen/project-template/actions/workflows/pull-request-ci.yml)

## Overview

This is a **production-ready project template** designed for solo developers working with AI agents. It provides:

- **Trunk-based workflow** with protected `main` branch
- **Automated CI/CD pipelines** for every stage
- **Security scanning** built into every PR
- **CODEOWNERS** for automatic review assignment
- **Environment promotion** from Dev → Staging → Production

## Quick Start

### 1. Create Your Project

1. Click **"Use this template"** (green button above)
2. Name your repository
3. Choose Public or Private
4. Click **"Create repository from template"**

### 2. Configure Branch Protection

Go to **Settings → Branches → Add rule** for `main`:

- [x] Require a pull request before merging
- [x] Require status checks to pass
- [x] Require conversation resolution
- [x] Do not allow bypassing
- [x] Restrict deletions

### 3. Update CODEOWNERS

Edit `.github/CODEOWNERS` and replace `@YOUR-USERNAME` with your GitHub username.

### 4. Start Building

```bash
git clone https://github.com/YOUR-USERNAME/your-new-repo.git
cd your-new-repo
git checkout -b feature/initial-setup
# Make your changes
git push -u origin feature/initial-setup
# Open a PR to main
```

## Repository Structure

```
.
├── .github/
│   ├── CODEOWNERS              # Code ownership rules
│   └── workflows/
│       ├── feature-branch-ci.yml    # Fast checks on feature branches
│       ├── pull-request-ci.yml      # Full validation for PRs
│       ├── deploy-dev.yml           # Auto-deploy to Dev on merge
│       ├── release-staging.yml      # Deploy to Staging on tag
│       └── release-production.yml   # Manual production deploy
├── docs/
│   └── ENGINEERING-WORKFLOW.md      # Full workflow documentation
└── README.md
```

## Workflow

### Development Flow

```
┌─────────────────────────────────────────────────────────────────┐
│  1. Create feature branch from main                             │
│  2. Make changes, commit, push                                  │
│  3. Open PR to main                                            │
│  4. CI runs: lint, test, security scan                         │
│  5. Get code review (CODEOWNERS auto-assigned)                 │
│  6. Squash merge when all checks pass                          │
└─────────────────────────────────────────────────────────────────┘
```

### Release Flow

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│     DEV      │ ──▶ │   STAGING    │ ──▶ │  PRODUCTION  │
│              │     │              │     │              │
│ Auto-deploy  │     │ Tag v1.0.0   │     │   Manual     │
│  on merge    │     │  triggers    │     │  approval    │
└──────────────┘     └──────────────┘     └──────────────┘
```

## CI/CD Pipelines

| Workflow | Trigger | Purpose |
|----------|---------|----------|
| Feature Branch CI | Push to `feature/*` | Fast feedback (lint, test, security) |
| Pull Request CI | PR to `main` | Full validation gate |
| Deploy Dev | Merge to `main` | Auto-deploy to development |
| Release Staging | Tag `v*.*.*` | Deploy to staging + release notes |
| Release Production | Manual | Production deploy with approval |

## Security Features

- **Gitleaks** - Secret detection in code
- **Trivy** - Vulnerability scanning
- **Dependency Review** - Checks for vulnerable dependencies
- **npm audit** - Node.js security audit

## Branch Protection Rules

The `main` branch is protected with:

- No direct pushes
- Required PR reviews from CODEOWNERS
- All CI checks must pass
- Conversation resolution required
- No force pushes or deletions

## Documentation

- [Engineering Workflow Standard](docs/ENGINEERING-WORKFLOW.md) - Complete workflow guide

## License

This template is provided for use by Balancing Rock projects.

---

*Built for speed, security, and scalability.*
