---
name: 'Frontend Standards'
description: 'SvelteKit + TypeScript conventions and patterns'
applyTo: '**/*.svelte,**/*.ts,**/*.css'
---

# Frontend Coding Standards

Reference: `docs/DESIGN_SYSTEM.md` for visual patterns, `docs/STANDARDS.md` for general principles.

## SvelteKit Conventions

- One component per file. Name files in PascalCase (`UserCard.svelte`).
- Prefer `$state` and `$derived` runes over legacy reactive declarations.
- Use TypeScript strict mode. Avoid `any` — use `unknown` and narrow types.
- Keep components small and composable. Extract logic into `.ts` utility files when it's reusable.

## State Management

- Use Svelte stores (`writable`, `readable`, `derived`) for shared state.
- Avoid prop drilling beyond 2 levels — use context or stores instead.
- Server-side data loading goes in `+page.server.ts` / `+layout.server.ts`.

## Styling

- Use CSS variables defined in `docs/DESIGN_SYSTEM.md` for colors, spacing, typography.
- Scoped styles in `<style>` blocks by default. Global styles go in `app.css`.
- Mobile-first responsive design. Use `min-width` media queries.

## Accessibility

- All interactive elements must be keyboard accessible.
- All images need `alt` text. Decorative images use `alt=""`.
- Use semantic HTML elements (`<nav>`, `<main>`, `<section>`, `<button>`).

## Error Handling

- Use SvelteKit error pages (`+error.svelte`) for route-level errors.
- Display user-friendly error messages. Log technical details to console.
- Handle loading states explicitly — no blank screens during data fetches.
