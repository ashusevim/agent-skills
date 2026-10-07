---
name: tailwind-utilities
version: 1
source: https://tailwindcss.com/docs
description: Style with Tailwind utility classes. Use when installing Tailwind, composing utilities in markup, styling hover/focus/responsive/dark states with variants, using arbitrary values, or resolving class conflicts and duplication.
---

# Tailwind Utilities

Style in markup with single-purpose classes + variant prefixes. No class names invented, no CSS files touched for most work.

Source: Tailwind v4 docs (install, styling, states, responsive). Companion for systems work: `wshobson/agents@tailwind-design-system` (tokens/components, 67K installs).

## When to use

- Installing Tailwind (Vite plugin path) and first styled element
- Composing layout/type/color/spacing utilities in markup
- States (`hover:`), breakpoints (`sm:`), dark mode (`dark:`), stacked variants
- Arbitrary values (`bg-[#316ff6]`), conflicts (`!`), duplication calls
- Dynamic values from data (inline styles + CSS vars)

## Instructions

1. **Install the Vite way.** `npm install tailwindcss @tailwindcss/vite` → plugin in `vite.config.ts` → `@import "tailwindcss"` in CSS → `npm run dev`. Done when: a `text-3xl font-bold underline` test element renders styled.
2. **Compose, don't name.** Layout (`flex p-6 gap-x-4`), box (`max-w-sm mx-auto rounded-xl shadow-lg`), type (`text-xl font-medium`) — one concern per class, directly in markup. Done when: element styled with zero new CSS.
3. **Prefix for conditions.** `hover:bg-sky-700` (states), `sm:grid-cols-3` (≥40rem), `dark:bg-gray-800` (pair light + dark classes, never one class for both). Stack: `dark:lg:data-current:hover:…`. Done when: each condition verified in its state.
4. **Escape hatch in order: arbitrary → inline → component.** One-off value → `bg-[#316ff6]` / `grid-cols-[24rem_2.5rem_1fr]`; dynamic-from-data → inline style or CSS var + utility (`bg-(--bg-color)`); repeated pattern → loop, multi-cursor, or real component — never `@apply` soup. Done when: no magic numbers outside theme except bracketed ones.
5. **Conflicts: remove, don't pile.** Two classes, one property → stylesheet order wins (`grid flex` = grid) — delete the loser; trailing `!` only when fighting foreign CSS. Done when: no element carries two classes for the same property.

## References

- `references/patterns.md` — install recap, variant stacking, duplication playbook

## Changelog

- v1: initial build from Tailwind v4 docs (install + styling guide)
