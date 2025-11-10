# Design References for WebSummit 2025 Landing Page

## ✅ Design Files Added

This folder contains the design references for the WebSummit 2025 landing page implementation.

### 📁 Current Files:

1. **Desktop.png** - Full desktop mockup (3.2 MB)
   - Shows complete page layout with all sections
   - Color blocks: Blue (#0047FF), Yellow (#FFD600)
   - Hero section with "SAFETY FOR UKRAINIANS"
   - All 8 content sections

2. **Mobile.png** - Mobile responsive layout (866 KB)
   - Mobile-optimized vertical stacking
   - Same color scheme as desktop
   - Shows how sections adapt to mobile

### 🎨 Design Analysis Summary:

**Key Features:**
- ⚡ **Minimalist design** - No icons, no cards, clean typography
- 🎨 **Color blocks** - Full-width sections alternating between blue, yellow, white, gray
- 📐 **Grid layout** - Two columns on desktop (title left, content right)
- 🔤 **Bold typography** - 80px hero title, 40px section titles
- 📱 **Responsive** - Stacks vertically on mobile

---

### Step 2: Reference During Development

When implementing the components (see `/docs/DEVELOPMENT_PLAN.md`), open your design PNG in a separate window to:
- ✅ Match colors exactly
- ✅ Measure spacing between elements
- ✅ Identify fonts and sizes
- ✅ Replicate button styles
- ✅ Copy card layouts

---

## Recommended File Structure (Optional)

If you have multiple design files, organize them like this:

```
design-refs/
├── README.md (this file)
├── full-page-design.png        # Complete page mockup
├── colors-palette.png           # Color swatches
├── typography-guide.png         # Font specifications
└── sections/                    # Individual section mockups
    ├── hero-section.png
    ├── about-block.png
    ├── fundraiser-block.png
    └── ...
```

---

## Design Extraction Checklist

When reviewing your design PNG, extract:

### Colors
- [ ] Primary brand color (currently: #1a4d8c blue)
- [ ] Accent/CTA color (currently: #ffc439 yellow)
- [ ] Background colors
- [ ] Text colors (headings, body, links)
- [ ] Border colors

### Typography
- [ ] Font family (currently: Inter)
- [ ] Heading sizes (H1, H2, H3)
- [ ] Body text size
- [ ] Font weights (normal, semibold, bold)
- [ ] Line heights

### Spacing
- [ ] Section padding (top/bottom)
- [ ] Card padding (internal)
- [ ] Grid gaps
- [ ] Container max-width

### Components
- [ ] Button styles (padding, border-radius, hover effects)
- [ ] Card styles (borders, shadows, hover effects)
- [ ] Icon sizes and placement
- [ ] Image/video placeholder dimensions

### Layout
- [ ] Desktop grid columns (2, 3, 4?)
- [ ] Mobile stacking order
- [ ] Breakpoints (when layout changes)
- [ ] Container alignment

---

## Using Design Reference with Claude Code

When giving the design PNG to Claude Code for implementation:

1. **Place the PNG in this folder** (`design-refs/`)
2. **Reference it in your prompt:**
   ```
   "Please implement the landing page according to the design in
   design-refs/websummit-page-design.png and the specifications
   in docs/DEVELOPMENT_PLAN.md"
   ```
3. **Claude Code can view images** and extract design details automatically

---

## Current Design System (Default)

If no custom design PNG is provided, the following defaults from `DEVELOPMENT_PLAN.md` will be used:

**Colors:**
- Primary: #1a4d8c (Deep Blue)
- Accent: #ffc439 (Yellow)
- Background: #ffffff / #f7f9fa

**Typography:**
- Font: Inter (Google Fonts)
- Sizes: 16px base, 24-48px headings

**Spacing:**
- Section padding: 80px (desktop), 48px (mobile)
- Cards: 24-32px padding
- Grid gap: 24px

**Components:**
- Cards: Rounded corners (12px), subtle shadows
- Buttons: Yellow (#ffc439), bold text, hover lift effect
- Icons: 48-64px, emoji or SVG

---

## Tips for Best Results

### For High-Fidelity Implementation
- Provide design PNG at actual size (1920px+ width recommended)
- Include annotations for spacing/sizing if possible
- Mark interactive elements (buttons, links, hover states)
- Specify fonts if not using Inter

### For Quick Implementation
- Even a rough sketch or screenshot works
- Claude Code can interpret basic layouts
- Combine PNG with written descriptions for clarity

---

## Questions?

If you need help extracting design details or have questions about implementation, refer to:
- `/docs/DEVELOPMENT_PLAN.md` - Complete development guide
- Existing components in `/src/components/` - Reference implementations
- Astro docs: https://docs.astro.build

---

**Last Updated:** 2025-01-10
**Project:** WebSummit 2025 Landing Page
**Framework:** Astro 5.x
