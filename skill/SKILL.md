---
name: fpsot-style
description: Style rules for the screens of FPSOT products. Use when adding design tokens, building or changing a component's states, writing validation, loading or empty states, confirming a destructive action, or making and checking a theme (FPSOT default PatternFly, Québec or Canada).
---

# FPSOT style

Summary of the FPSOT style specification. It adds no rules of its own.
The spec text in `spec/` wins on any difference. Each line cites its requirement ID and keeps its strength: must, should or may.
Every accessibility value (contrast, focus size, motion) comes from the FPSOT accessibility specification, never from here.

## Design tokens

- Components must take every color, font, size, space, radius, shadow and duration from a token, never a raw value (STY-001).
- Token files must follow the Design Tokens Format Module 2025.10, with a `$type` on every token, and color values must name their color space. Files should end in `.tokens.json`; tools may generate CSS custom properties (STY-002).
- Two tiers must exist: base tokens hold values, semantic tokens name a purpose and alias a base token. Components must use semantic tokens only. Component tokens may exist and must alias semantic ones (STY-003).
- Base names must give scale and step (`color.blue.50`); semantic names must give role and state (`color.text.danger`) and must not name a value (STY-004).
- Token words must come from the FPSOT naming specification's vocabulary, but token paths follow the Design Tokens format, not its JSON-field rules: segments must be kebab-case, scale steps may be numeric (`spacing.300`); CSS names must be `--fpsot--segment--segment` (STY-005).
- Themes must give a value to every semantic token and must not rename, remove or add one; components must not read tokens outside the contract (STY-006).
- The contract must use semantic versioning; a token must carry `$deprecated` for at least one minor version before removal (STY-007).

## Token categories

- Color tokens must cover text, links, backgrounds, borders, focus, disabled and the four status roles; link tokens must cover default, hover and visited. Each foreground token must list its backgrounds under `$extensions."org.fpsot.style".on` (STY-010).
- Font families must end with a generic family; sizes must be `rem`, line heights unitless numbers; themes must not bundle fonts they cannot redistribute (STY-011).
- Spacing must be one fixed `rem` scale, and components must use only its steps (STY-012).
- Radius tokens must cover small, medium, large and pill; components must not set their own radius (STY-013).
- Elevation must be a short list of shadow levels tied to roles; layers above the page should also have a border or backdrop (STY-014).
- Every animation must use `duration` and `cubicBezier` tokens, and one setting must zero every duration (STY-015).
- Layout tokens must cover breakpoints and content width as `rem` dimensions, and line length as a `number` token of characters with the unit `ch` in `$extensions."org.fpsot.style".unit` (STY-016).

## Component states

- Interactive components must define default, hover, focus, pressed and disabled, plus selected and error where they apply. Two states must not look the same; on touch screens a theme may merge hover and pressed (STY-020).
- Focus must show on keyboard focus, must use only the focus tokens, and must add to the hover look (STY-021).
- Hover must not be the only way to reveal content, and must not shift layout (STY-022).
- Pressed must show during activation; selected must persist and show by more than color (STY-023).
- Products should not disable buttons to signal an incomplete form; when they disable a control, they must say why (STY-024).

## Errors, loading and empty states

- Validate on leaving a field or on submit, never while typing; the server must check again (STY-030).
- Field errors must sit next to the field with danger tokens and an icon, and name one problem and its fix. The product or engine sets above or below in the markup, never the theme; a binding government position is recorded under STY-056 (STY-031).
- When a product shows an error summary, it must sit above the form and list the errors in field order. When a summary is needed, its links and focus come from the accessibility spec (STY-032).
- Forms should work without browser scripts; HTMX or Alpine.js may enhance them (STY-033).
- No indicator should show under one second; one must show for longer waits; it should be a shaped placeholder when the shape is known, else a spinner; a progress bar must show for known steps or waits over five seconds (STY-034).
- A busy control must show its state and ignore a second activation (STY-035).
- Empty views must show an empty state with a heading that says why; no-result views must offer to clear the filter; failed loads must show an error (STY-036).

## Destructive actions

- Reversible actions should run at once with an undo instead of a confirmation (STY-040).
- Irreversible actions must confirm in a dialog that names the object and result; the button must repeat the verb and must not say "OK" or "Yes" (STY-041).
- The confirm button must use danger tokens; focus must start on the least destructive action; Escape must cancel (STY-042).
- Severe actions may require typing the object's name; the dialog must say what to type (STY-043).
- Destructive actions must use a form button, never a link (STY-044).

## Themes

- A theme must contain only color, type and layout; it may hold several color schemes; motion tokens are not themable (STY-050).
- A theme must not change behavior: it must not contain scripts or templates, nor change states, keyboard use, focus order, validation, messages, confirmation steps or content (STY-051).
- A theme must not contain official marks; the engine must give header and footer slots where the deploying body adds its own (STY-052).
- The default theme must be PatternFly 6 as published (6.7.0 in v0.1), changing no value except STY-064 overrides; public services should use their jurisdiction theme (STY-053).
- The Québec theme must follow the Système de design gouvernemental and the PIV header banner layout (STY-054).
- The Canada theme must follow the GC Design System, the Canada.ca specifications and the Canada.ca header and footer layout (STY-055).
- Government behavior rules must not go into a theme; the product must record each binding difference (STY-056).

## Checking a theme

- Every theme must pass the checks before each release and on each upstream version change; PatternFly is not assumed to pass (STY-060).
- The token check must test every listed pair in every color scheme against the accessibility spec, and confirm every token has a value (STY-061).
- The component check must render every state in every color scheme and run the accessibility spec's web tests (STY-062).
- Each theme must publish a check record with versions, date, tools and each failure (STY-063).
- Gaps must be fixed by token values, never behavior; the default theme may override a failing PatternFly value until upstream fixes it, and must report it (STY-064).
- Each jurisdiction theme must meet the FPSOT accessibility baseline, which already includes Québec's added criteria (STY-065).
