# Patterns

## Install recap (Vite)

```bash
npm create vite@latest my-project && cd my-project
npm install tailwindcss @tailwindcss/vite
# vite.config.ts: import tailwindcss from '@tailwindcss/vite' → plugins: [tailwindcss()]
# style.css: @import "tailwindcss";
npm run dev
```

## Variant stacking

`hover:bg-sky-700` → CSS only acts on `:hover`. `disabled:hover:bg-sky-500` for multi-condition.
`sm:grid-cols-3` → `@media (width >= 40rem)`. `dark:bg-gray-800` → `@media (prefers-color-scheme: dark)`.
Parent-aware: `group-hover:underline`. Fully arbitrary: `[&>[data-active]+span]:text-blue-600`.

## Duplication playbook (in order)

1. Loop — markup authored once, rendered N times. No problem exists.
2. Multi-cursor — localized repeats edited simultaneously.
3. Component/partial — cross-file reuse, single source of truth.
4. Custom CSS (`@layer components` with theme vars) — only when a partial is heavier than the style.

## Dynamic values

```jsx
// value from DB/API → inline style var, utility reads it
<div style={{ "--bg-color": c }} className="bg-(--bg-color) hover:bg-(--bg-color-hover)">
```
