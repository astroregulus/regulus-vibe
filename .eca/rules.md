# ECA Rules for Regulus Project

## 🔴 MANDATORY: Post-Change Validation

**After making ANY changes to `.astro`, `.css`, `.ts`, or `.js` files, ALWAYS run:**

```bash
npm run check
```

This validates:
- ✅ TypeScript/JavaScript syntax
- ✅ Astro component structure  
- ✅ CSS syntax within style blocks
- ✅ Import/export correctness

## 🔴 MANDATORY: Before Task Completion

**Before marking any task as complete, run:**

```bash
npm run build
```

This ensures the static site builds successfully without errors.

---

## If Check Fails

1. **Read the error carefully** - Note the file path and line number
2. **Open the file** - Use `eca__read_file` to inspect the problem area
3. **Fix the issue** - Usually syntax errors (missing brackets, duplicate code)
4. **Run check again** - Verify the fix with `npm run check`
5. **Only then continue** - Don't proceed until all checks pass

---

## Common Issues to Watch For

### CSS Errors
- **Duplicate content** - When editing `<style>` blocks, ensure no duplicate CSS rules
- **Unclosed brackets** - CSS blocks must have matching `{` and `}`
- **Invalid properties** - Check CSS property names are valid

### Astro Errors  
- **Missing imports** - Components must import dependencies in frontmatter (`---` block)
- **Invalid JSX** - Use `{expression}` syntax for JavaScript in templates
- **Unclosed tags** - All HTML/JSX tags must be properly closed

### JavaScript Errors
- **Missing semicolons** - While optional, be consistent
- **Undefined variables** - Ensure all variables are declared
- **Type mismatches** - Check props match their interfaces

---

## Brand Compliance

**Always refer to `BRAND.md` before making visual changes:**

### Approved Colors ONLY:
| Color | Hex | Usage |
|-------|-----|-------|
| Navy | #011830 | Primary - headers, buttons |
| Black | #000000 | Secondary - text, borders |
| White | #FFFFFF | Tertiary - backgrounds |
| Orange | #EA883A | Accent - highlights, gradients, separators |

### Approved Fonts ONLY:
- **Lato Regular** (400) - Body text
- **Lato Bold** (700) - Headings, buttons
- **Lato Black** (900) - Large headlines

### Spacing Grid:
- Use multiples of 8px: `8px, 16px, 24px, 32px, 48px, 64px`

---

## NPM Scripts Available

| Command | Purpose |
|---------|---------|
| `npm run dev` | Start development server |
| `npm run check` | Run Astro syntax validation |
| `npm run build` | Build static site |
| `npm run preview` | Preview built site |

---

## File Structure

```
src/
├── components/    # Reusable Astro components
├── layouts/       # Page layouts (BaseLayout.astro)
├── pages/         # Route pages (index.astro, etc.)
└── styles/        # CSS files (variables, global, typography)

public/
├── fonts/         # Lato font files
├── logos/         # Brand logo files
└── images/        # Static images
```
