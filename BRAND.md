# REGULUS BRAND GUIDELINES

## Master Reference Document for AI Tools and Developers

**Last Updated:** 2025  
**Maintained By:** Regulus Astrology Team  
**Contact:** astrologia@regulus.com.br

---

## 1. COLOR SYSTEM

### Primary Brand Colors

| Color Name | Hex Code | RGB | PANTONE | CMYK | Usage |
|---|---|---|---|---|---|
| **Navy Blue (Primary)** | #011830 | R1, G24, B48 | 296 C | C95, M82, Y51, K64 | Headers, headings, buttons, primary accents |
| **Black (Secondary)** | #000000 | R0, G0, B0 | — | C0, M0, Y0, K100 | Body text, borders, secondary elements |
| **White (Tertiary)** | #FFFFFF | R255, G255, B255 | — | C0, M0, Y0, K0 | Backgrounds, text on dark backgrounds |

### Accent Color (Use Sparingly)

| Color Name | Hex Code | RGB | Usage |
|---|---|---|---|
| **Orange (Accent)** | #EA883A | R234, G136, B58 | Highlights, gradients, separators, decorative elements |

**Orange Usage Guidelines:**
- ✅ Use for visual highlights and emphasis
- ✅ Use in gradients (e.g., Navy to Orange transitions)
- ✅ Use as separator lines or decorative borders
- ✅ Use for hover states or interactive accents
- ❌ Do NOT use as primary button color
- ❌ Do NOT use for body text
- ❌ Do NOT overuse — keep it subtle and purposeful

### CSS Variable Names
```css
--color-primary: #011830;    /* Navy Blue */
--color-secondary: #000000;  /* Black */
--color-tertiary: #FFFFFF;   /* White */
--color-accent: #EA883A;     /* Orange - highlights, gradients, separators */
```

### DO NOT USE ❌
- Red, Green, Purple, or any other colors not listed above
- Random gradients (only Navy ↔ Orange approved)
- Lighter/darker shades outside the defined palette

---

## 2. TYPOGRAPHY

### Font Family: LATO
**License:** Open Font License (OFL)

### Font Weights
| Weight | Value | Usage |
|--------|-------|-------|
| Regular | 400 | Body text |
| Bold | 700 | Headings, emphasis, buttons |
| Black | 900 | Large headlines |

### Typographic Scale
| Element | Weight | Desktop | Mobile | Color |
|---------|--------|---------|--------|-------|
| H1 | 900 | 48px | 32px | #011830 |
| H2 | 700 | 32px | 24px | #011830 |
| H3 | 700 | 24px | 20px | #011830 |
| Body | 400 | 16px | 14px | #000000 |
| Small | 400 | 14px | 12px | #000000 |

---

## 3. LOGOS

### Files Location
- Horizontal: `/public/logos/horizontal/`
- Vertical: `/public/logos/vertical/`
- Symbol/Favicon: `/public/logos/symbol/`

### Logo Rules
- Colors: Navy (#011830) + Black (#000000) + White (#FFFFFF) only
- Min width: 240px desktop, 160px mobile
- Clear space: 20px all sides
- Never distort, rotate > 45°, or change colors

---

## 4. BUTTONS

### Primary Button
```css
background: #011830;
color: #FFFFFF;
font-weight: 700;
padding: 12px 24px;
border-radius: 4px;
```

### Secondary Button
```css
background: #000000;
color: #FFFFFF;
font-weight: 700;
padding: 12px 24px;
border-radius: 4px;
```

---

## 5. SPACING (8px Base)

- 8px, 16px, 24px, 32px, 48px, 64px

---

## 6. QUICK REFERENCE FOR AI TOOLS

### Approved Colors:
- Navy (Primary): #011830
- Black (Secondary): #000000
- White (Tertiary): #FFFFFF
- Orange (Accent): #EA883A — for highlights, gradients, separators only

### Font: Lato (400, 700, 900 only)

### When Creating/Modifying:
1. Use only approved colors
2. Use only Lato font weights 400, 700, 900
3. Follow 8px spacing grid
4. Maintain logo integrity
