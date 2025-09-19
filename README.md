# Multi-Branch CI/CD Pipeline

This project demonstrates a multi-branch deployment strategy using GitHub Actions.

## Branch Strategy

| Branch | Environment | Deploy? | Notes |
|--------|-------------|---------|-------|
| `main` | Production | ✅ | Live environment |
| `dev` | QA | ✅ | Test/QA environment |
| `pull_request` | None | ❌ | CI only (lint + test) |

## Workflow Jobs

- **CI**: Runs on all PRs and pushes - linting, testing, and artifact creation
- **Deploy QA**: Deploys to QA environment when pushing to `dev` branch
- **Deploy Production**: Deploys to production when pushing to `main` branch

## Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Run locally:
   ```bash
   npm start
   ```

3. Run tests:
   ```bash
   npm test
   ```

4. Run linting:
   ```bash
   npm run lint
   ```

## API Endpoints

- `GET /` - Welcome message
- `GET /health` - Health check

## Deployment Process

1. Create feature branch from `dev`
2. Make changes and create PR to `dev`
3. CI runs automatically (lint + test)
4. Merge to `dev` triggers QA deployment
5. Create PR from `dev` to `main`
6. Merge to `main` triggers production deployment