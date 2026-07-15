# 🤝 Contributing to ModularWork

<div align="center">

![ModularWork](https://img.shields.io/badge/ModularWork-Contribution%20Guide-5865F2?style=for-the-badge)
![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge)
![Standard](https://img.shields.io/badge/standard-ENFORCED-critical?style=for-the-badge)

### The official engineering standard for contributing to the ModularWork ecosystem.

</div>

---

# 📜 Status

| Property   | Value                 |
| ---------- | --------------------- |
| Document   | Contribution Standard |
| Version    | `1.0.0`               |
| Status     | Active                |
| Applies To | All contributors      |
| Language   | English               |

---

# 1. Introduction

ModularWork is designed as a long-term framework ecosystem.

Contributions are not only code changes.

Every contribution affects:

* architecture;
* maintainability;
* compatibility;
* ecosystem stability.

Therefore, all contributions MUST follow this document.

> A contribution that works but violates ModularWork standards is considered invalid.

---

# 2. Contribution Philosophy

ModularWork follows these priorities:

```
Correctness
      >
Consistency
      >
Maintainability
      >
Performance
      >
Convenience
```

A smaller, predictable solution is preferred over a complex solution that introduces unnecessary behavior.

---

# 3. Contribution Workflow

## 3.1 Before Development

Before creating changes:

Contributors SHOULD:

* read the project architecture;
* understand affected modules;
* check existing issues;
* avoid duplicate implementations.

Large changes SHOULD be discussed before implementation.

---

## 3.2 Branch Naming

Branches MUST follow:

```
type/name
```

Examples:

```
feature/inventory-system
fix/database-timeout
refactor/network-layer
docs/api-reference
```

Allowed types:

| Type       | Purpose               |
| ---------- | --------------------- |
| `feature`  | New functionality     |
| `fix`      | Bug fixes             |
| `refactor` | Internal improvements |
| `docs`     | Documentation         |
| `test`     | Testing               |
| `chore`    | Maintenance           |

---

# 4. Pull Requests

## 4.1 Requirements

A Pull Request MUST:

* have a clear description;
* explain the reason for changes;
* contain only related changes;
* pass required checks;
* follow project standards.

---

## 4.2 Pull Request Structure

Recommended format:

```md
## Summary

What changed?

## Reason

Why was this needed?

## Technical Details

How does it work?

## Testing

How was it verified?
```

---

## 4.3 Pull Request Review

Review focuses on:

```
Architecture
      |
      v
Correctness
      |
      v
Maintainability
      |
      v
Style
```

Reviews are about the implementation.

Not the author.

---

# 5. Commit Standards

Commits SHOULD be:

* small;
* focused;
* understandable.

Bad:

```
fixed stuff
```

Good:

```
fix(database): handle connection timeout
```

---

## Commit Format

ModularWork follows:

```
type(scope): description
```

Examples:

```
feat(inventory): add container support
fix(net): prevent invalid packet state
refactor(core): simplify module loader
docs(api): update networking documentation
```

---

# 6. Code Requirements

All code MUST:

* follow project architecture;
* avoid hidden side effects;
* be documented where necessary;
* preserve compatibility.

Code SHOULD:

* be simple;
* avoid unnecessary abstraction;
* prefer existing utilities.

---

# 7. Lua Development Standard

ModularWork uses a strict Lua style.

The following rules are mandatory.

---

# 7.1 Formatting

## Indentation

Tabs MUST be used.

Required `.editorconfig`:

```ini
root = true

[*]
indent_style = tab
indent_size = 4
charset = utf-8
trim_trailing_whitespace = true
insert_final_line = true
```

---

# 7.2 Lua Syntax

Use standard Lua syntax.

Required:

```lua
if value then
	print('Hello')
end
```

Forbidden:

```lua
if (value) then
	print('Hello')
end
```

---

Forbidden:

```lua
&&
||
!
!=
```

Required:

```lua
and
or
not
~=
```

Exception:

`continue` MAY be used.

---

# 7.3 Strings

Single quotes are preferred.

Required:

```lua
local text = 'Hello world'
```

If a single quote is required:

```lua
local text = 'Don\'t do this'
```

---

# 7.4 Line Length

Lines SHOULD NOT exceed:

```
120 characters
```

Long expressions MUST be formatted:

```lua
local allowed =
	IsValid(player) and
	player:IsAdmin() and
	not player:IsFrozen()
```

---

# 7.5 Tables

Multi-line tables MUST use trailing commas.

Required:

```lua
local data = {
	name = 'Player',
	level = 10,
}
```

---

# 8. Naming Convention

## Variables and Functions

MUST use:

```
camelCase
```

Example:

```lua
local playerData = {}

local function savePlayer()
end
```

---

## Classes and Metatables

MUST use:

```
PascalCase
```

Example:

```lua
local Character = {}

Character.__index = Character
```

---

## Enumerations

MUST use:

```
ALL_CAPS
```

Example:

```lua
MODULARWORK_VERSION = '1.0'
```

---

## Unused Variables

Unused variables MUST be named:

```lua
_
```

Example:

```lua
for _, value in next, data do
end
```

---

# 9. Architecture Rules

## 9.1 Module Isolation

Modules MUST:

* own their internal state;
* avoid unnecessary globals;
* expose explicit APIs.

Forbidden:

```lua
globalVariable = {}
```

Preferred:

```lua
myModule = myModule or {}
```

---

# 9.2 Hooks and Network Messages

Identifiers MUST follow:

```
module.submodule.action
```

Examples:

```lua
hook.Run('inventory.itemAdded')

netstream.Start(
	'orgs.users.setRank'
)
```

---

# 9.3 Libraries

Libraries SHOULD use:

```lua
module.function()
```

instead of unnecessary objects.

Example:

```lua
inventory.addItem(item)
```

---

Metatables SHOULD only be used when:

* creating many similar objects;
* requiring shared behavior;
* implementing special structures.

---

# 10. Performance Requirements

Performance-sensitive code MUST avoid unnecessary allocations.

---

## Static Data

Cache static values outside functions.

Bad:

```lua
local function test()
	local messages = {}
end
```

Good:

```lua
local messages = {}

local function test()
end
```

---

## Table Iteration

Preferred:

```lua
for _, value in next, data do
end
```

For indexed tables:

```lua
for i = 1, #data do
	local value = data[i]
end
```

`ipairs` SHOULD NOT be used.

Exceptions:

* custom iterators;
* explicit API requirements.

---

## Table Insertions

For sequential append:

Preferred:

```lua
data[#data + 1] = value
```

instead of:

```lua
table.insert(data, value)
```

---

# 11. ModularWork Utilities

Heavy operations SHOULD use framework utilities.

Examples:

```lua
mw.func.debounce()

mw.func.throttle()

mw.func.performance()
```

Do not duplicate existing framework functionality.

---

# 12. Documentation Requirements

Complex systems MUST be documented.

Documentation SHOULD explain:

* purpose;
* architecture;
* limitations;
* usage examples.

Documentation SHOULD NOT explain obvious code.

Bad:

```lua
-- Set player name
playerName = name
```

Good:

```lua
-- Cached value is synchronized after coordinator confirmation.
```

---

# 13. Comments

Comments are allowed and encouraged.

However:

Comments MUST explain:

* why something exists;
* unusual behavior;
* architectural decisions.

Comments MUST NOT describe obvious operations.

---

# 14. Forbidden Practices

The following are prohibited:

* ❌ modifying core modules without approval
* ❌ bypassing Game Coordinator authority
* ❌ adding undocumented APIs
* ❌ introducing global state without reason
* ❌ ignoring existing framework utilities
* ❌ submitting intentionally incomplete work

---

# 15. Final Checklist

Before submitting:

* [ ] Code follows style rules
* [ ] Architecture is respected
* [ ] No unnecessary globals
* [ ] Documentation updated
* [ ] Tests pass
* [ ] Changes are focused
* [ ] No breaking changes without migration

---

# ⚖️ Final Rule

<div align="center">

## Write code that another developer can understand years later.

</div>

---

<div align="center">

**ModularWork Contribution Standard v1.0.0**

🧩

</div>