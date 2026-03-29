# Agent Notes — Regulus Vibe

## Commands
| Task | Command |
|------|---------|
| Dev server | `npm run dev` |
| Type-check | `npm run check` |
| Production build | `npm run build` |
| Lint (check + dry build) | `npm run lint` |

No test framework is configured. Verify changes visually via the dev server.

### When npm commands fail (dyld / Node environment error)
If any npm command exits with `dyld: Symbol not found` or `Abort trap: 6`, the Node
installation is broken and CLI tools are unavailable. **Do not skip validation — use the fallback:**
- Run `eca__editor_diagnostics` on every modified `.astro` / `.ts` file — this uses the
  LSP and catches type errors, missing imports, and syntax issues without Node
- Treat any diagnostic as a blocking error exactly as you would a failed `npm run check`

### Git staging discipline
**Never use `git add -A` or `git add .`** — always stage only the files that belong to the
current change. Untracked files that existed before your work must not enter the commit.
Use `git add <explicit-paths>` and verify with `git status` before committing.

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
- Breakpoints: mobile ≤ 768 px · desktop > 768 px (canonical breakpoint; all CSS media queries use this value)
- `position: fixed` overlays (action bars, modals) **must be the last child of `<body>`**, i.e. placed after `<Footer />` in the page template — never nested inside `<main>` or any container with `overflow`, `transform`, `will-change`, `filter`, or `backdrop-filter`
- Avoid `backdrop-filter` on fixed overlays — it creates a stacking context that breaks child positioning in Chrome

### Safe-area & DevTools emulation (learned from /mapa action bar bug)
- **Always include `viewport-fit=cover`** in `<meta name="viewport">` — without it `env(safe-area-inset-bottom)` always resolves to `0`, so fixed bottom bars appear behind the simulated home-indicator/device bezel in DevTools emulation even though they look fine on a plain browser resize
- **Any fixed bottom overlay must clear `env(safe-area-inset-bottom)`** in its own padding: `padding-bottom: calc(Xpx + env(safe-area-inset-bottom))`
- **Page content below a fixed bottom bar** must also add the same clearance so content isn't hidden under it: `padding-bottom: calc(<bar-height> + env(safe-area-inset-bottom))` — apply this to both the default and the `@media (max-width: 768px)` overrides
- **DevTools emulation ≠ plain browser resize**: emulation also changes `pointer: coarse` / `hover: none` media features and simulates a real device viewport (dynamic viewport height, safe-area insets). A plain resize does none of this — so an element that appears fine on resize may still be broken under emulation

## Astro-Specific Rules
- Props interfaces are defined inline with `interface Props` in the component frontmatter
- `Astro.props` destructuring uses default values inline: `const { x = 'default' } = Astro.props`
- Prefer `<style is:global>` over global CSS files for page-specific rules targeting dynamic elements
