---
name: direct-data-flow
description: Choose direct data and call paths when implementing, refactoring, or reviewing code, including serialization, representation conversions, intermediate values, forwarding wrappers, and adapters.
---

# Direct Data Flow

Use this skill when implementing, refactoring, or reviewing code that passes or transforms data between producers and consumers.

## Core rule

Trace the complete data path from producer to consumer and prefer the most direct path that preserves required meaning, contracts, and behavior.

## Evaluate the path

1. Identify the source data, the destination's required representation, and the contracts of genuine boundaries.
2. Trace the affected calls and representations, including conversions, encode/decode stages, temporary values, allocations, copies, forwarding wrappers, and adapters.
3. Compare the whole path with the most direct alternative supported by the existing types, interfaces, and library APIs.
4. Keep stages that perform independently required work, such as validation, normalization, semantic transformation, format compatibility, ownership or lifetime handling, or adapting a real boundary.
5. Prefer direct serialization, conversion, and calls to the responsible implementation when intermediate steps only forward or re-express the same information.
6. Verify the selected path against actual uses, required formats, failure behavior, and observable contracts. Consider recurring cost where the path is performance-sensitive.

For example, when the destination requires JSON bytes, compare `serde_json::to_string(&value)?.into_bytes()` with `serde_json::to_vec(&value)?`. Use the direct byte serialization when the string has no independent use.

## Responsibility boundaries

This skill owns the directness of data and call paths, including paths built entirely from existing types and APIs.

[`concept-introduction-threshold`](https://github.com/supersovaa/concept-introduction-threshold/blob/main/SKILL.md) owns whether named implementation concepts and abstractions are justified.

[`responsibility-aligned-refactoring`](https://github.com/supersovaa/responsibility-aligned-refactoring/blob/main/SKILL.md) owns coherent operation and state ownership when responsibilities move across implementation boundaries.

Requirements and existing interface contracts determine which representations and conversions are necessary. The surrounding implementation and review workflows own changes, tests, and acceptance.
