# Project Guidelines

## Product Goal

- This project is a full rebuild of the older `isyll.github.io` portfolio and will be deployed to `isylladev.vercel.app`.
- Treat the app as a personal developer portfolio first: prioritize strong visual identity, clear project storytelling, responsive layouts, and production-ready polish.
- Avoid generic landing-page filler, placeholder copy, or interchangeable UI patterns unless explicitly requested.

## Code Style

- Use TypeScript with strict types; avoid `any` unless there is no practical alternative.
- Match the existing formatting: 2-space indentation, semicolons, single quotes, and `@/*` path aliases.
- Keep Tailwind utility classes readable and let Prettier with `prettier-plugin-tailwindcss` sort them.
- Reuse `cn()` from `lib/utils.ts` for class composition and follow existing `cva()` variant patterns for reusable UI components.

## Architecture

- This repo uses Next.js App Router. Keep route files in `app/`, reusable app sections in `components/`, shadcn primitives in `components/ui/`, utilities in `lib/`, and custom hooks in `hooks/`.
- Prefer Server Components by default in `app/`; add `'use client'` only when a component needs browser APIs, local state, effects, or event handlers.
- Keep theme handling centralized through `components/theme-provider.tsx`. Do not remove or repurpose the `d` theme-toggle hotkey unless asked.

## Styling

- The design system is built from Tailwind CSS v4, shadcn/ui, Radix, and CSS variables defined in `app/globals.css`.
- Prefer extending the existing token system in `app/globals.css` over hardcoding one-off colors, spacing scales, or radii.
- When adding shadcn components, place generated primitives in `components/ui/` and keep app-specific composition outside that folder.
- For major UI work, aim for a deliberate portfolio aesthetic rather than default template styling.

## Build And Validation

- Install dependencies with `bun install` or the package manager already in use for the task.
- Use these commands when validating changes:
  - `bun run dev`
  - `bun run lint`
  - `bun run typecheck`
  - `bun run build`
- There is currently no test suite configured. Do not invent test commands; mention the gap if verification is limited.

## Working Conventions

- Preserve the current shadcn and Radix patterns such as `asChild`, `Slot`, and `cva` variants instead of rewriting them into bespoke APIs.
- Keep changes minimal and coherent with the existing structure; if a new feature introduces a new pattern, establish it cleanly and use it consistently.
- Favor accessible, semantic markup and performance-conscious choices suitable for a public portfolio site.
