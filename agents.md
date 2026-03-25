# Agent Notes — Regulus Vibe

## Commands
| Task | Command |
|------|---------|
| Dev server | `npm run dev` |
| Type-check | `npm run check` |
| Production build | `npm run build` |
| Preview build | `npm run preview` |
| Lint (check + dry build) | `npm run lint` |

No test framework is configured. Verify changes visually via the dev server. Always run `npm run lint` before finishing.

## Stack & Structure
- **Astro 6** static site, `type: module`, Node ≥ 22. TypeScript strict (`astro/tsconfigs/strict`). No JS framework — vanilla JS in `<script>` tags only.
- Pages: `src/pages/` · Components: `src/components/` · Layouts: `src/layouts/` · Styles: `src/styles/`
- Data files: `src/data/*.json` — add new collections here; register them in `public/admin/config.yml` for CMS editing.

## CSS Rules
- Design tokens live in `src/styles/variables.css` — **never hard-code colours, spacing, radii, or shadows**. Use `--color-*`, `--spacing-*`, etc.
- Section backgrounds alternate: white (`--color-tertiary`) ↔ off-white (`--color-surface`) ↔ navy (`--color-primary`). Never stack two navy sections without a light section between them.
- Add class `dark-section` to any navy container — global.css automatically flips `.btn-primary` to white-on-navy and `.btn-secondary` to transparent-with-white-border.
- Use `<style is:global>` for rules targeting JS-created elements; scoped `<style>` for static markup. No `!important` except overriding third-party inline styles.
- Breakpoints: mobile ≤ 768 px (only). Test at 384 px wide in Chrome DevTools Responsive Mode.

## Code Style
- **TypeScript**: type all function params, return values, and `interface Props` shapes; no `any`.
- **Imports**: Astro components first, then third-party, then local. No barrel files.
- **Naming**: PascalCase for `.astro` components, camelCase for variables/functions, UPPER_SNAKE for constants.
- **Props**: define `interface Props` inline in frontmatter; destructure with defaults: `const { x = 'default' } = Astro.props`.
- **No inline styles** except dynamic CSS custom properties (e.g. `style="--pct:42%"`).

## Layout & Mobile Gotchas
- `position: fixed` overlays must be the **last child of `<body>`** (after `<Footer />`), never inside a container with `overflow`, `transform`, `will-change`, `filter`, or `backdrop-filter`.
- Always include `viewport-fit=cover` in `<meta name="viewport">` so `env(safe-area-inset-bottom)` resolves correctly in DevTools emulation.
- Fixed bottom bars and the page content beneath them both need `padding-bottom: calc(Xpx + env(safe-area-inset-bottom))`.
- External links: always add `target="_blank" rel="noopener noreferrer"`.
