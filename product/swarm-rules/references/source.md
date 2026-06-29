# THE SWARM MANIFESTO: PRINCIPLES & TACTICAL RULES

## I. CORE PRINCIPLES

1. **The Leader-Follower Axiom**
   Every swarm must have exactly one **Leader** (Orchestrator). The Leader is the only agent responsible for state management, task decomposition, and final synthesis. Followers (Teammates) execute and report; they do not redefine the mission.

2. **State-Driven Orchestration**
   Never rely on an agent's "memory" or context window for long-running workflows. Use an external **Task List** (JSON/Database) as the single source of truth for progress. If an agent dies, the state survives.

3. **Hyper-Specialization**
   A "general-purpose" agent is a jack-of-all-trades and master of hallucinations. Deploy specialized personas (e.g., Security Sentinel, Performance Oracle) for specific files or functions. Smaller models (Haiku/GPT-4o-mini) are often better and faster for narrow research tasks.

4. **Structured Communication (Inboxes)**
   Direct "chatting" between agents is noisy and prone to drift. Use **Structured Messages** (JSON) for inter-agent communication. Every message should have a type (e.g., `task_update`, `shutdown_request`, `finding_report`).

5. **Resource Stewardship (The Cleanup Rule)**
   Agents are processes. Processes consume tokens and compute. A swarm that cannot shut itself down is a "zombie swarm." Always define an exit condition and a cleanup routine.

---

## II. TACTICAL RULES OF ENGAGEMENT

### 1. Spawning & Initialization
* **Context Isolation:** Only give a teammate the specific files or context required for their task. Overloading context leads to noise.
* **Dependency Mapping:** Define `blocked_by` relationships at creation. Never let an agent "poll" for work manually if a dependency system can trigger it.
* **Background Execution:** Run execution tasks (coding, testing) in the background; run planning/research tasks in the foreground if they block the next step.

### 2. Communication Protocols
* **Prefer `write` over `broadcast`:** Only broadcast critical state changes (e.g., "Main branch updated"). For everything else, send targeted messages to specific agents to save tokens.
* **The Heartbeat Check:** If an agent hasn't updated its task status in 300 seconds, assume it has crashed or looped. The Leader must have a "reclaim" or "restart" logic.
* **Structured Findings:** Require agents to report findings in a standardized format: 
    * `Status`: (Success/Failure)
    * `Evidence`: (Logs/File Snippets)
    * `Action Taken`: (Changes made)

### 3. Task Management
* **Atomic Ownership:** Only one agent can "own" a task at a time. Use a "claim" mechanism to prevent race conditions in parallel swarms.
* **The Plan-Approval Loop:** For high-stakes edits, require a `plan_mode`. The agent must output a proposed diff/strategy and wait for a `plan_approved` message from the Leader before executing.

### 4. Shutdown & Lifecycle
* **Graceful Exit:** Use a two-phase commit for shutdown:
    1. Leader sends `requestShutdown`.
    2. Teammate completes current sub-task and sends `approveShutdown`.
    3. Leader terminates process.
* **Artifact Preservation:** Before cleanup, the Leader must move all critical findings from teammate inboxes into a permanent log or PR description.