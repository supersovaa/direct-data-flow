# Direct Data Flow

A lightweight skill for selecting direct data and call paths during code implementation, refactoring, and review.

This skill targets development by a single user working with an AI agent.

## When to use

Use [`direct-data-flow`](SKILL.md) when implementing, refactoring, or reviewing code that passes or transforms data across conversions, intermediate representations, serialization stages, forwarding wrappers, or adapters.

## Core idea and responsibility

Trace data from its producer to its consumer and choose the most direct path that preserves required meaning and contracts. Evaluate intermediate stages by the independent work they perform rather than by local appearance.

This skill owns the directness of data movement and call paths, including chains that introduce no new named concepts. Executable rules are in [`SKILL.md`](SKILL.md).

## Adjacent responsibilities

- [`concept-introduction-threshold`](https://github.com/supersovaa/concept-introduction-threshold/blob/main/SKILL.md) evaluates the justification for named abstractions.
- [`responsibility-aligned-refactoring`](https://github.com/supersovaa/responsibility-aligned-refactoring/blob/main/SKILL.md) governs ownership and authoritative paths after responsibility moves.
- Repository requirements and interface contracts define the representations and behavior that must be preserved.

## Installation

Place this repository's `SKILL.md` at `<skills-root>/direct-data-flow/SKILL.md` in the target agent's skill directory, or install this repository using the agent's skill installation mechanism.

For repository-based routing, link the [public skill definition](https://github.com/supersovaa/direct-data-flow/blob/main/SKILL.md) directly from each applicable implementation, refactoring, test-implementation, and code-review task entry. Apply it when that work type begins.
