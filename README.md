# The DevOps Project

This repository is a DevOps starter project focused on automation, continuous integration, and deployment workflows using GitHub Actions. It provides a simple foundation for building and deploying a project through a structured CI/CD pipeline with preview and dev-environment stages.

## Overview

The project currently contains:

- GitHub Actions workflow definitions for CI/CD automation
- A placeholder build directory for generated artifacts
- A dev deployment workflow that uploads and attests build artifacts before deployment
- Dependabot automation for GitHub Actions dependency updates
- A public-domain license for open use

This is a lightweight template repository intended to demonstrate DevOps practices rather than a full application codebase.

## Repository Structure

```text
.
├── .github/
│   ├── dependabot.yml
│   └── workflows/
│       ├── CICD.yml
│       ├── Deploy-to-Dev.yml
│       └── blank.yml
├── build/
│   └── .gitkeep
├── LICENSE
├── README.md
└── .git/
```

## CI/CD Workflow Summary

### 1. CI/CD Pipeline
File: `.github/workflows/CICD.yml`

This workflow runs on pull requests targeting `main` and manually via `workflow_dispatch`.

It performs:

- Build stage (currently a placeholder echo step)
- Test stage with unit, integration, functional, E2E, and exploratory placeholders
- Preview stage for pull requests (currently echo-only; no actual deployment)

The main intent is to validate changes before they are merged and demonstrate a preview stage during the review process.

### 2. Development Deployment
File: `.github/workflows/Deploy-to-Dev.yml`

This workflow is manually triggered and deploys the project to a `dev` environment.

It includes:

- Artifact upload from the `build` directory
- Build provenance attestation using GitHub's attestation support
- Artifact download and deployment steps for the development environment

This demonstrates a production-style deployment pattern: build artifact -> attest -> deploy.

### 3. Basic CI Workflow
File: `.github/workflows/blank.yml`

This file is a simple starter GitHub Actions workflow that checks out the repository and echoes example build messages. It acts as a minimal CI template and is useful as a starting point for extending the pipeline.

## Deployment Model

The project follows a staged DevOps approach:

- CI validation occurs on pull requests
- Test and preview steps run before deployment
- Manual deployment triggers move the artifact into the `dev` environment
- Deployment artifacts are stored in `build/` and treated as release output

## Build Output

The `build/` directory is reserved for generated artifacts. It currently contains a placeholder `.gitkeep` file, which indicates that the folder is ready for compiled output, packaged artifacts, or deployment bundles.

## Security and Maintenance

- Dependabot is configured to check for GitHub Actions updates daily.
- Artifact provenance is attested during the dev deployment flow to improve build traceability.
- Workflow permissions are explicitly defined for deployment and attestation actions.

## License

This project is released under the Unlicense. See [LICENSE](LICENSE) for details.

## Notes

This repository is intentionally lightweight and acts as a DevOps foundation. It does not yet include a runtime application, service code, or infrastructure-as-code components, but it is structured to support those additions as the project evolves.