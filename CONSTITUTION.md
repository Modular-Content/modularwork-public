# 🧩 ModularWork Constitution

<div align="center">

![ModularWork](https://img.shields.io/badge/ModularWork-Constitution-5865F2?style=for-the-badge)
![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/status-RATIFIED-success?style=for-the-badge)
![Architecture](https://img.shields.io/badge/architecture-Framework-orange?style=for-the-badge)

### The foundational law of the ModularWork ecosystem.

**A runtime framework.  
A distributed architecture.  
A foundation for independent worlds.**

</div>

---

# 📜 Status

| Property | Value |
|---|---|
| Document | ModularWork Constitution |
| Version | `1.0.0` |
| Status | ✅ Ratified |
| Type | Foundational Architecture Document |
| Scope | Entire ModularWork ecosystem |

> This document defines the non-negotiable architectural principles of ModularWork.

---

# 🧭 Table of Contents

- [1. Purpose](#1-purpose)
- [2. Core Principles](#2-core-principles)
- [3. Core Modules](#3-core-modules)
- [4. Schemas](#4-schemas)
- [5. Data Model](#5-data-model)
- [6. Game Coordinator](#6-game-coordinator)
- [7. External Services](#7-external-services)
- [8. Observability](#8-observability)
- [9. Debugging](#9-debugging)
- [10. Evolution](#10-evolution)
- [11. Non-Goals](#11-non-goals)
- [12. Final Law](#12-final-law)

---

# 1. Purpose

## What is ModularWork?

**ModularWork is not a gamemode.**

**ModularWork is not an addon.**

**ModularWork is not a content package.**

---

ModularWork is a **runtime framework and ecosystem** designed to provide a stable foundation for creating independent game schemas, services and experiences on top of Garry's Mod.

Its purpose is to provide:

- deterministic behavior
- scalable architecture
- authoritative data management
- modular extensibility
- long-term ecosystem stability

Any implementation contradicting this definition is considered **non-compliant**.

---

# 2. Core Principles

## 2.1 Source of Truth

> **There MUST be exactly one authority over persistent state.**

The authoritative source of truth in ModularWork is the:

# 🎮 Game Coordinator

Game servers do not own persistent reality.

They maintain:

```
Game Server State
        |
        v
   Local Cache
        |
        v
 Game Coordinator
        |
        v
 Persistent Reality
```

Local state is temporary.

Cache is replaceable.

The Coordinator is truth.

---

## 2.2 Determinism Over Convenience

ModularWork prioritizes predictable systems over shortcuts.

The following principles apply:

✅ Explicit state changes  
✅ Traceable mutations  
✅ Predictable execution  
✅ Reproducible results  

Forbidden:

❌ Hidden side effects  
❌ Unknown state mutations  
❌ Untraceable behavior  

> If the system cannot explain why something happened, the system is considered broken.

---

## 2.3 Runtime Independence

External dependencies must never become single points of failure.

A service outage MUST:

- degrade functionality
- preserve gameplay
- queue operations
- recover safely

A service outage MUST NOT:

- crash servers
- corrupt data
- destroy player state

```
Service unavailable
        |
        v
   Degraded Mode
        |
        v
 Recovery
        |
        v
 Deterministic Sync
```

---

# 3. Core Modules

## 3.1 Mandatory Core

The ModularWork foundation consists of:

| Module | Purpose |
|-|-|
| `mwlib` | Core framework library |
| Administration System | Permission and management layer |
| Configuration System | Runtime configuration |
| Core Spawn Menu | Framework interface |
| Core Toolgun | Framework interaction layer |

---

These modules are:

# 🔒 Immutable Core Components

They:

- MUST NOT be disabled
- MUST NOT be removed
- MUST NOT be replaced locally

Core changes may only happen through official upstream revisions.

Local modifications are considered:

```
Unsupported
Outside Specification
Non-Compliant
```

---

# 3.2 Core Architecture Rule

```
        Schemas
           |
           v
     Core Modules
           |
           v
      Garry's Mod
```

The dependency direction is absolute.

Core modules:

✅ may exist without schemas  
❌ may not depend on schemas  

Schemas:

✅ depend on core  
❌ modify core behavior globally  

---

# 4. Schemas

## 4.1 Definition

A schema is a composition of modules defining a complete experience.

A schema may define:

- gameplay rules
- progression
- entities
- interactions
- simulation logic
- player systems

Examples:

- Roleplay
- Simulation
- Scenario environments

---

## 4.2 Schema Isolation

Schemas are isolated environments.

A schema:

MUST NOT:

- mutate global core state
- depend on another schema
- create hidden cross-schema coupling

Communication MUST happen through:

```
Explicit Interfaces
        |
        v
    Defined Contracts
```

---

# 5. Data Model

## 5.1 Data Types

Every persistent object MUST exist as a registered data type.

A data type defines:

| Requirement | Description |
|-|-|
| Structure | Internal representation |
| Ownership | Responsible authority |
| Lifecycle | Creation and removal rules |
| Mutation Rules | Allowed changes |
| Version | Compatibility identifier |

---

> Unregistered data does not exist.

---

# 5.2 Data Mutation

Persistent mutations MUST follow:

```
Request
   |
   v
Validation
   |
   v
Game Coordinator
   |
   v
Persistent State
```

Forbidden:

- direct database writes
- bypassing authority
- uncontrolled synchronization

Emergency writes MUST either:

- reconcile
- or be discarded

---

# 6. Game Coordinator

## 6.1 Authority

The Game Coordinator is the sole authority for:

| Domain | Authority |
|-|-|
| Player Data | ✅ |
| Permissions | ✅ |
| Cross-server State | ✅ |
| Persistent World Data | ✅ |

Game servers may:

- read cached data
- request mutations
- process gameplay

They may not claim ownership.

---

# 6.2 Failure Handling

Coordinator failure enters:

# 🟡 Degraded Mode

Servers MUST:

- continue gameplay
- cache changes
- queue operations
- synchronize later

Recovery MUST be deterministic.

---

# 7. External Services

External services are consumers, not authorities.

Services:

✅ may read Coordinator data  
✅ may request mutations  
✅ must respect validation  

Services:

❌ cannot become sources of truth

---

# 8. Observability & Explainability

A ModularWork system MUST answer:

| Question | Requirement |
|-|-|
| What exists? | Discoverable |
| Why exists? | Explainable |
| Who controls it? | Traceable |
| What depends on it? | Visible |

Unknown systems are invalid systems.

---

# 9. Debugging & Validation

ModularWork MUST provide:

- diagnostics
- environment validation
- consistency checks
- debugging information

Silent corruption is:

# ❌ Forbidden

---

# 10. Evolution

Architecture changes slower than implementation.

Rules:

- compatibility is preferred
- migrations are documented
- breaking changes require approval

A rewrite is not an excuse to ignore history.

---

# 11. Non-Goals

ModularWork does not attempt to:

| Goal | Status |
|-|-|
| Replace Garry's Mod | ❌ |
| Become beginner-focused | ❌ |
| Maximize popularity | ❌ |

Priority order:

```
Correctness
      >
Scalability
      >
Control
      >
Convenience
```

---

# 12. Final Law

<div align="center">

## ⚖️ The Prime Directive

</div>

> **If a system violates this constitution but appears to work, it is still broken.**

---

<div align="center">

**ModularWork Constitution v1.0.0**

**Ratified. Permanent. Foundational.**

🧩

</div>