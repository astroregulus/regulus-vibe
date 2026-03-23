# Agent Notes — Regulus Vibe

## Commands
| Task | Command |
|------|---------|
| Dev server | `npm run dev` |
| Type-check | `npm run check` |
| Production build | `npm run build` |
| Lint (check + dry build) | `npm run lint` |

No test framework is configured. Verify changes visually via the dev server.

## Stack & Structure
- **Astro 6** (static site, `type: module`), **TypeScript strict**, no framework (vanilla JS in `<script>` tags)
- Pages: `src/pages/` · Components: `src/components/` · Layouts: `src/layouts/` · Styles: `src/styles/`
- CSS design tokens live in `src/styles/variables.css` — always use them, never hard-code colours or spacing

## Code Style
- **TypeScript strict** — always type function params, return values, and `interface` shapes; no `any`
- **Imports** — Astro components first, then third-party, then local; no barrel files
- **Naming** — PascalCase for `.astro` components, camelCase for variables/functions, UPPER_SNAKE for constants
- **CSS** — use `<style is:global>` for any rule targeting JS-created elements; scoped `<style>` for static markup
- **No inline styles** except for dynamic CSS custom properties (e.g. `style="--pct:42%"`)
- **No `!important`** except overriding third-party library inline styles (e.g. astrochart SVG dimensions)

## Mobile / Responsive
- **"Mobile" = Chrome DevTools Responsive Mode at 384 px width** — this is the only mobile environment tested
- Breakpoints: mobile ≤ 900 px · desktop > 900 px
- `position: fixed` overlays (action bars, modals) **must be the last child of `<body>`**, i.e. placed after `<Footer />` in the page template — never nested inside `<main>` or any container with `overflow`, `transform`, `will-change`, `filter`, or `backdrop-filter`
- Avoid `backdrop-filter` on fixed overlays — it creates a stacking context that breaks child positioning in Chrome

## Astro-Specific Rules
- Props interfaces are defined inline with `interface Props` in the component frontmatter
- `Astro.props` destructuring uses default values inline: `const { x = 'default' } = Astro.props`
- Prefer `<style is:global>` over global CSS files for page-specific rules targeting dynamic elements
