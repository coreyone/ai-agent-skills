---
name: data-persistence-caching
description: Use when designing database schemas, query optimization, caching layers (Redis, local cache), transaction boundaries, and mobile offline storage sync.
---

# 💾 Core Philosophy: Data is the most valuable asset; protect its integrity and optimize its retrieval.

## When to use

Use this skill when defining SQLite/PostgreSQL schemas, ORM models, Redis key schemas, local app storage (SwiftData, CoreData, IndexedDB), sync models, cache-aside strategies, and transaction logic.

## When not to use

Do not use this skill for layout styling, UI interactions, API transport conventions (HTTP details), or provisioning.

## Trigger cues

- Key terms: database, cache, transactional, ACID, BASE, PostgreSQL, SQLite, SwiftData, CoreData, Redis, IndexedDB, transaction, migration, query, indexing, TTL, invalidation.
- Designing schema models, implementing cache layers, writing complex queries, or offline sync logic.

## Routing boundary

- Primary for database layout, storage performance, cache eviction, transactions, and data structures.
- Secondary to `system-architecture-rules` for domain boundaries.

## Inputs required

- Target storage engines (PostgreSQL, SwiftData, Redis, etc.)
- Strict read/write ratios and low latency limits
- Source of truth: `references/source.md`

## Instructions

1. **Detect Stack**: Inspect the workspace files to identify the project's existing technology stack (e.g., Prisma, TypeORM, SQLAlchemy, CoreData, PostgreSQL, SQLite).
2. **Do Not Migrate**: Never propose or force a technology stack change. Apply the principles in this skill using the project's current tooling.
3. Read [references/source.md](references/source.md) to understand storage systems and cache invalidation.
4. Outline database schemas and queries using the project's existing database tools and libraries.
5. Design caching strategies including cache eviction policies (LRU) and stampede mitigation.
6. Establish transaction boundaries to guarantee ACID behavior where required.
7. In mobile apps (iOS), enforce separate background concurrency context rules for CoreData/SwiftData.

## Output format

- Primary decision/output: Database schema/migrations, indexing strategy, and caching topology.
- Summary: One-paragraph overview of persistence and cache strategy.
- Actions: Validation checklist for performance, concurrency safety, and cache consistency.
