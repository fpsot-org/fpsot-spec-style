# Changelog

All notable changes to this specification are listed here.
The format follows [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/),
and versions follow [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-11-05

### Added

- Design tokens: tokens for every visual value, the Design Tokens Format Module 2025.10, base and semantic tiers, token names and the token contract (STY-001 to STY-007).
- Token categories: color, type, spacing, radius, elevation, motion and layout (STY-010 to STY-016).
- Component states: the set of states, focus, hover, pressed, selected and disabled (STY-020 to STY-024).
- Errors, loading and empty states: validation timing, field messages, the error summary, forms without scripts, loading indicators, busy controls and empty states (STY-030 to STY-036).
- Destructive actions: undo, confirmation dialogs, danger buttons, typed confirmation and form buttons (STY-040 to STY-044).
- Themes: what a theme contains, no behavior, no official marks, the PatternFly default theme, the Québec theme, the Canada theme and government behavior rules (STY-050 to STY-056).
- Checking a theme: token and component checks against the FPSOT accessibility specification, the check record, fixing gaps and jurisdiction checks (STY-060 to STY-065).
- Comparison data with an international baseline, Canada and Québec rows.
- A how-to guide, the agent skill, `llms.txt` and a book per language.

### Known gaps

- The FPSOT semantic token set itself (the list of token names) is not yet published. Version 0.1 sets its categories and rules only.
- The naming specification has no row for design tokens yet. STY-005 sets their form from the Design Tokens format until it does.
