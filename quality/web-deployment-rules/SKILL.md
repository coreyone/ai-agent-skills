---
name: web-deployment-rules
description: Use when configuring web build tools, Docker containers, multi-stage builds, CI/CD pipelines, zero-downtime releases, CDNs, and database migrations.
---

# 🚀 Core Philosophy: Software is not real until it is running in production for real users.

## When to use

Use this skill when writing Dockerfiles, configuring GitHub Actions or GitLab CI configs, managing static assets, caching configurations on CDN Edge (Stale-While-Revalidate), designing zero-downtime deployments (Blue-Green, Canary), and executing zero-downtime database migrations.

## When not to use

Do not use this skill for frontend UI state logic, visual theme layout, or unit test mock designs.

## Trigger cues

- Key terms: deployment, Dockerfile, docker-compose, CI/CD, GitHub Actions, Vercel, Netlify, CDN, canary, blue-green, database migration, zero-downtime, pipeline, multi-stage build, container, edge routing.
- Writing CI pipelines, Docker config, CDN caching config, or coordinating schema migrations with code updates.

## Routing boundary

- Primary for deployment automation, containerization, release patterns, environment variables (12-factor), and edge assets optimization.
- Secondary to `developer-web-performance` for in-app bundle optimization.

## Inputs required

- Target deployment infrastructure (e.g., AWS, Railway, Vercel, Kubernetes)
- DB migration requirements and rollback targets
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing build, host, and deployment configurations (e.g., GitHub Actions, Vercel, AWS, Docker, Kubernetes, Terraform, Prisma migrations).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand continuous delivery and distributed container deployment.
4. Design pipeline operations and deployment targets matching the existing hosting tooling.
5. Establish environment configurations according to 12-factor app guidelines.
6. Implement zero-downtime deployment strategies (Blue-Green or Canary) appropriate to the infrastructure.
7. Orchestrate zero-downtime database migrations using the Expand-and-Contract (Parallel Run) pattern.

## Output format

- Primary decision/output: CI/CD configuration files, Dockerfiles, and migration scripts.
- Summary: One-paragraph overview of the release and pipeline plan.
- Actions: Verification checklist for build speed, container security, and migration safety.
