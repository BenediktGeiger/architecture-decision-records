# 3. Standardize Docker Image Tagging Strategy

Date: 2024-03-20

## Status

Accepted

## Labels
general,main

## Context

Our teams are using inconsistent Docker image tagging practices, resulting in:
- Uncertainty about image contents and versions
- Difficulty tracking deployments
- Challenges with rollbacks
- Inefficient image cleanup processes
- Risk of deploying wrong versions

## Decision

We will implement a standardized Docker image tagging strategy across all projects:

Format: `<service-name>:<version>-<environment>-<build-hash>`

Components:
- `service-name`: Application/service identifier
- `version`: Semantic version (x.y.z)
- `environment`: Target environment (dev/stage/prod)
- `build-hash`: First 7 characters of git commit hash

Examples:
- `user-service:1.2.3-prod-a1b2c3d`
- `payment-api:2.0.0-stage-7890xyz`
- `auth-service:0.9.1-dev-q1w2e3r`

Additional Tags:
- Latest successful production build tagged as `<service-name>:latest`
- Release candidates tagged as `<service-name>:rc-<version>`
- Development builds tagged as `<service-name>:develop`

## Consequences

### Positive
- Clear image versioning and traceability
- Simplified deployment and rollback processes
- Easier automation of CI/CD pipelines
- Improved artifact management
- Better disaster recovery capability

### Negative
- More complex tagging process
- Additional storage requirements
- Need to update existing build pipelines

### Mitigation
- Automate tagging in CI/CD pipelines
- Implement regular cleanup of old images
- Create shared build scripts
- Document tagging strategy in developer onboarding