# 💾 Data Persistence and Caching Guidelines

> "There are only two hard things in Computer Science: cache invalidation and naming things." — Phil Karlton

---

## 📜 Core Philosophy
Data is the state of the system, and caching is a temporary optimization of that state. Business applications require clear isolation of concerns between durable storage (databases) and volatile speed buffers (caches). We design persistence models with strict consistency constraints, prioritize correct database indexing over caching, and mitigate cache synchronization pitfalls using first-principles reasoning.

---

## 🏛️ Storage and Consistency Foundations

### 1. ACID vs. BASE
*   **ACID (Traditional SQL - e.g., PostgreSQL, SQLite)**: Focuses on strong consistency. Transactions must be Atomic (all-or-nothing), Consistent (valid transitions), Isolated (no concurrent interference), and Durable (survives crashes). *Use when*: Handling financial records, orders, inventories.
*   **BASE (Modern NoSQL / Distributed systems)**: Focuses on availability. Basically Available, Soft-state (values can change without user input), Eventually consistent. *Use when*: High-throughput activity logs, user chats, clickstream metrics.

### 2. Indexes and Query Tuning
*   **B-Tree Indexes**: Standard for relational databases. Fast point lookups ($O(\log N)$) and range scans.
*   **Composite Indexes**: Order of columns matters. The rule of thumb: `(equality, sorting, range)` columns. A composite index on `(status, created_at)` will optimize a query filtering by status and ordering/filtering by date, but it cannot optimize a query filtering *only* by `created_at`.
*   *Anti-pattern*: Blindly adding single-column indexes on every column. This degrades insert/update performance and inflates database storage.

---

## 🏎️ Caching Topology and Strategies

### 1. Caching Access Patterns
*   **Cache-Aside (Lazy Loading)**: Application queries the cache. If a miss occurs, it queries the database, writes the result to the cache, and returns it. *Benefit*: Cache only contains requested data. *Drawback*: Cache miss penalty.
*   **Write-Through**: Application writes to the cache, which writes to the database synchronously. *Benefit*: Cache is never stale. *Drawback*: Write latency penalty.
*   **Write-Behind (Write-Back)**: Application writes to the cache, which writes to the database asynchronously. *Benefit*: Extremely low write latency. *Drawback*: Risk of data loss if the cache crashes before flushing to the database.

### 2. Cache Invalidation and Stampede Mitigation
*   **Eviction Policies**: Always configure a Max Memory limit and eviction policy (e.g., `allkeys-lru` - Least Recently Used) to prevent Out-Of-Memory crashes.
*   **Cache Stampede (Thundering Herd)**: When a hot cache key expires, multiple application instances query the database concurrently to rebuild the cache, causing database saturation.
    *   *Mitigation*: Implement mutex locking (using Redis `SETNX`) around cache rebuilds, or use **Probabilistic Early Expiration** (rebuilding the cache asynchronously slightly before it actually expires).

---

## 📱 Mobile Persistence (iOS SwiftData / CoreData)

*   **Concurrency Rules**: Main thread contexts (e.g., `modelContext` tied to `@Query` in SwiftUI) must never be accessed from background tasks.
*   **Background Contexts**: Use `container.newBackgroundContext()` or run mutations inside `modelContainer.performBackgroundTask { context in ... }`.
*   **Batch Mutations**: For high-volume updates, bypass the live object graph and use `NSBatchInsertRequest` / `NSBatchUpdateRequest` to prevent memory blowups.
*   **Offline Sync**: When syncing local changes to a remote backend, use deterministic Conflict-Free Replicated Data Types (CRDTs) or optimistic version check headers (`If-Match` ETags) to handle merge conflicts.

---

## 🛠️ First-Principles Application Examples (Illustrative Stack: Drizzle ORM, Supabase/Neon Postgres, Zero, TanStack Query)

> [!IMPORTANT]
> **DO NOT FORCE A TECH STACK CHANGE**: You must detect the project's existing database stack (e.g., Prisma, TypeORM, Mongoose, SQLAlchemy, CoreData) and map these principles directly to those tools. Under no circumstances should you attempt to rewrite, migrate, or propose changing a codebase to Drizzle ORM, Supabase/Neon, Zero Sync Engine, or TanStack Query unless explicitly requested by the user. The stack below is purely illustrative.

### 1. Zero-Overhead Object-Relational Mapping (e.g., Drizzle ORM)
*   **Principle**: *Rely on query builders that map closely to SQL syntax to avoid opaque runtime overhead and hidden database operations.*
*   *Application*: Use Drizzle ORM schemas (`schema.ts`) to declare columns, constraints, and relationships. Leverage Drizzle's Relational Queries API for clean nesting, but fallback to raw SQL builders (`db.select()`) when precise control or index tuning is required. Review migration scripts generated via `drizzle-kit` before applying.

### 2. Serverless Connection Pooling (e.g., Neon/Supabase)
*   **Principle**: *Scale serverless workloads safely by virtualizing and caching database connection lifecycles.*
*   *Application*: In serverless SvelteKit endpoints, use connection pooling URLs (transaction mode, port 5432/pooled endpoints) to prevent exhausting active Postgres socket allocations during traffic bursts.

### 3. Local Replica Cache Sync (e.g., Zero Sync Engine)
*   **Principle**: *Pre-replicate application query subsets directly to local client memory to eliminate data-loading layouts.*
*   *Application*: Configure synchronization boundaries in Zero to stream schema records to the client, fetching directly from local cache rather than making direct remote DB queries inside component loops.

### 4. Client-State Caching and Revalidation (e.g., TanStack Query)
*   **Principle**: *Maintain a client-side cache of network requests with explicit expiration and revalidation limits.*
*   *Application*: Use TanStack Query to manage non-replicated API server states. Define strict revalidation limits (`staleTime`) to avoid double-fetching data during page transitions.
