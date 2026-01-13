# Project: Seemy Luxury Eyewear (Editorial Prototype)

## Overview
A radical, high-end e-commerce experience for a designer sunglasses brand.
**Aesthetic DNA:** Celine Minimalism × Saint Laurent Edge × Gucci Editorial.
This is not a template. This is a fashion statement rendered in code.

---

## Tech Stack
- **Language:** HTML5 (Semantic), Vanilla JS (ES6+)
- **Styling:** Tailwind CSS (via CDN with extended config)
- **Fonts:** 'Playfair Display' (Display Typography), 'Lato' (Micro-Copy)
- **Icons:** Phosphor Icons (Thin stroke ONLY - weight: 1px)

---

## Key Commands
- `npm run serve` - Start local development server
- `/agent run code-reviewer` - Trigger luxury compliance audit (Sonnet-level)

---

## Design Philosophy: The 6 Pillars of Editorial Luxury

### 1. Radical Negative Space
**The Rule:** Luxury is defined by what you DON'T fill.

- **Minimum Section Padding:** `py-32` (128px vertical). `py-24` is now considered "cramped."
- **Horizontal Breathing Room:** Use `px-12 lg:px-24` (96px on desktop).
- **Element Margins:** Minimum `mb-16` between major content blocks. `mb-8` is acceptable only for tight micro-groups.
- **Grid Gaps:** Minimum `gap-16` for grids. Use `gap-20` or `gap-24` for editorial spreads.

**Rationale:** Fashion editorials use 60-70% white space. Your designs must do the same.

---

### 2. Typography as Architectural Element
**The Rule:** Headings are not labels. They are visual landmarks.

#### Size Hierarchy:
- **Hero Headlines:** `text-8xl` (96px) or `text-9xl` (128px) on desktop. Use Playfair Display at 600 weight.
- **Section Headers:** `text-6xl` (60px) minimum. Never smaller than `text-5xl` (48px).
- **Subheadings:** `text-3xl` (30px). Use sparingly.
- **Body Text:** `text-base` (16px) for Lato. Use `leading-relaxed` (1.625 line-height) for luxury readability.
- **Micro-Copy (Labels, Buttons):** `text-xs` (12px) with `tracking-[0.2em]` (letterspacing 200%).

#### Advanced Techniques:
- **Overlapping Text:** Headings may overlap images using `absolute` positioning with `z-10`. Ensure contrast with semi-transparent overlays if needed.
- **Breaking the Grid:** Allow text to span 120% of container width on purpose, creating intentional asymmetry.
- **Kerning:** Use `tracking-tighter` (-0.05em) for large Playfair headings to create density. Use `tracking-widest` (0.1em) for all-caps Lato labels.

**Example:**
```html
<h1 class="font-playfair text-9xl font-semibold tracking-tighter leading-none">
    The New<br>Minimalism
</h1>
```

---

### 3. Cinematic Micro-Interactions
**The Rule:** Speed is vulgar. Elegance takes time.

#### Transition Standards:
- **Image Hover Effects:** `duration-700 ease-out` (700ms). Use `scale-105` or `scale-110` transforms.
- **Opacity Fades:** `duration-500` minimum. Use `ease-in-out` for reversible states.
- **Text/Link Hovers:** `duration-300` for instant feedback, but apply to color changes ONLY.
- **Image Filters:** On hover, transition from `grayscale` to full color using `duration-700 ease-out grayscale hover:grayscale-0`.

#### Forbidden Shortcuts:
- ❌ NO `transition-all` (too generic).
- ❌ NO durations under `duration-200` for visual elements.
- ❌ NO "snap" effects (instant state changes).

#### Premium Hover Pattern (Image Zoom + Grayscale):
```html
<div class="overflow-hidden">
    <img
        src="..."
        class="w-full h-full object-cover grayscale transition-all duration-700 ease-out hover:grayscale-0 hover:scale-110"
    >
</div>
```

---

### 4. The Anti-Box Rule
**The Rule:** Cards are for playing poker. Products float in space.

#### Forbidden Elements:
- ❌ NO `border` on product cards.
- ❌ NO `shadow` (not even `shadow-sm`).
- ❌ NO background color on product containers (cards MUST be transparent or pure white).
- ❌ NO `rounded-lg` corners on product images (use `rounded-none` or subtle `rounded-sm`).

#### Correct Product Card Anatomy:
```html
<div class="group">
    <!-- Image floats on white, no container -->
    <div class="overflow-hidden mb-6">
        <img src="..." class="w-full aspect-square object-cover transition-transform duration-700 group-hover:scale-110">
    </div>

    <!-- Text floats below, minimal styling -->
    <p class="font-lato text-xs uppercase tracking-widest text-gray-500">Brand</p>
    <h3 class="font-playfair text-2xl text-dark mt-2">Product Name</h3>
    <p class="font-lato text-sm text-gray-600 mt-1">$450.00</p>
</div>
```

---

### 5. Fine Lines: The Editorial Divider System
**The Rule:** Separate sections like chapters in a magazine.

#### Divider Specifications:
- **Width:** `0.5px` or `border` with custom color `#E5E7EB` (gray-200).
- **Placement:** Between major sections (e.g., after Collections, before Footer).
- **Implementation:** Use `<hr>` tag with Tailwind classes:
  ```html
  <hr class="border-t border-gray-200 my-32 mx-auto max-w-7xl">
  ```
- **Never:** Use thick borders (`border-2`, `border-4`). Luxury is subtle.

#### When to Use:
- Between hero and first content section.
- Before footer.
- To separate thematic content blocks (e.g., Products → Brand Story).

---

### 6. Asymmetric Balance
**The Rule:** Symmetry is safe. Fashion is not.

#### Layout Ratios:
- **70/30 Split:** Image takes 70% width, text takes 30%. Use `grid-cols-[70%_30%]`.
- **60/40 Split:** Alternate between sections (Image Left 60%, Text Right 40%, then flip).
- **Offset Grids:** In 3-column layouts, shift the center column down by `mt-12` or `mt-16`.

#### Example: Asymmetric Brand Story:
```html
<div class="grid grid-cols-1 lg:grid-cols-[65%_35%] gap-0">
    <div class="relative h-screen">
        <img src="..." class="w-full h-full object-cover">
    </div>
    <div class="bg-light p-24 flex flex-col justify-center">
        <!-- Content -->
    </div>
</div>
```

#### Mobile Override:
Asymmetry collapses to single-column on mobile. Always stack with image first.

---

## Color System (Strict Enforcement)

### Primary Palette:
- **Brand Black:** `#1A1A1A` (text-dark) - Primary text, frames
- **Seemy Green:** `#8CB03F` (text-primary) - CTAs, hover states ONLY
- **Pure White:** `#FFFFFF` (bg-white) - Canvas
- **Off-White:** `#F9F9F9` (bg-light) - Subtle backgrounds for text containers

### Secondary Palette:
- **Gray-500:** `#6B7280` - Labels, eyebrows
- **Gray-400:** `#9CA3AF` - Secondary text
- **Gray-600:** `#4B5563` - Body text (when not using black)
- **Gray-200:** `#E5E7EB` - Divider lines

### Forbidden Colors:
- ❌ NO bright colors (red, blue, yellow) unless explicitly brand-approved.
- ❌ NO gradients.
- ❌ NO semi-transparent overlays with `bg-black/50` unless absolutely necessary for text contrast.

---

## Interaction Design Rules

### Hover States:
- **Links:** Fade to `text-primary` (green) with `duration-200`.
- **Buttons:** Invert colors (e.g., `bg-dark text-white` → `bg-primary text-dark`) with `duration-300`.
- **Images:** Apply one of:
  - **Zoom:** `scale-110` with `duration-700`
  - **Desaturate → Color:** `grayscale hover:grayscale-0` with `duration-700`
  - **Opacity Shift:** Fade overlay from `opacity-0` to `opacity-100`

### Cursor Behavior:
- Use `cursor-pointer` on all interactive elements.
- Consider custom cursors for ultra-luxury (future enhancement).

### Scroll Behavior:
- Use `scroll-smooth` on `<html>` tag.
- Implement parallax sparingly (e.g., hero background image with `bg-fixed`).

---

## Coding Standards

### Zero-Placeholder Policy:
- **NO** "Lorem Ipsum" or generic placeholder text.
- **NO** "Product Name" or "Category Title."
- **Use Real Copy:** "The Aviator 1972", "Handcrafted Italian Acetate", "Designed in Milan."

### Mobile-First Responsive Design:
- **Default:** Single column, full-width images.
- **Desktop Breakpoint:** `lg:` (1024px) for multi-column grids.
- **Typography:** Scale down hero headlines to `text-6xl` on mobile, `text-9xl` on desktop.

### Semantic HTML:
- **MUST USE:** `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<header>`.
- **Headings:** Follow hierarchy (h1 → h2 → h3). Never skip levels.
- **Alt Text:** Write descriptive alt text for all images (e.g., "Close-up of tortoiseshell acetate frame with gold hinges").

### Clean DOM:
- **Avoid:** Wrapper div hell. Use Tailwind's `@apply` or group utilities instead.
- **Max Nesting:** 3 levels deep for non-grid layouts.

---

## Absolute Prohibitions (DO NOT)

### Visual:
- ❌ **NO shadows** (`shadow-*` classes are banned).
- ❌ **NO gradients** (`bg-gradient-*` is banned).
- ❌ **NO rounded corners** on product cards (exception: buttons may use `rounded-sm`).
- ❌ **NO text over faces** in hero images (overlay text on architecture/objects only).
- ❌ **NO busy backgrounds** (patterns, textures, noise).

### Interaction:
- ❌ **NO instant transitions** (`duration-100` or less is banned for visual effects).
- ❌ **NO carousels** with auto-play (user controls only).
- ❌ **NO pop-ups** or modals unless critical (e.g., newsletter on exit intent).

### Typography:
- ❌ **NO font sizes smaller than `text-xs`** (12px minimum).
- ❌ **NO center-aligned body text** (headings may be centered, body text must be left-aligned).
- ❌ **NO mixing serif fonts** (Playfair Display ONLY for headings, Lato ONLY for body).

---

## Layout Patterns Library

### Hero Section:
```html
<section class="relative h-screen">
    <img src="..." class="absolute inset-0 w-full h-full object-cover grayscale">
    <div class="relative z-10 h-full flex items-center justify-center px-6">
        <h1 class="font-playfair text-9xl font-semibold text-white text-center tracking-tighter leading-none">
            Visionary<br>Design
        </h1>
    </div>
</section>
```

### Product Grid (4-Column):
```html
<div class="grid grid-cols-2 lg:grid-cols-4 gap-16">
    <!-- Product cards without borders -->
</div>
```

### Asymmetric Feature (70/30):
```html
<div class="grid grid-cols-1 lg:grid-cols-[70%_30%] gap-0 items-center">
    <img src="..." class="w-full h-full object-cover">
    <div class="p-24">
        <!-- Text content -->
    </div>
</div>
```

### Editorial Divider:
```html
<hr class="border-t border-gray-200 my-32 mx-auto max-w-6xl">
```

---

## Image Guidelines

### Aspect Ratios:
- **Hero:** `aspect-[16/9]` or full viewport height (`h-screen`).
- **Products:** `aspect-square` (1:1) for consistency.
- **Collections:** `aspect-[3/4]` (portrait) for editorial feel.
- **Brand Story:** `aspect-[4/3]` (landscape) or full-height (`h-[700px]`).

### Treatment:
- **Default State:** May use `grayscale` filter for ultra-editorial aesthetic.
- **Hover State:** Transition to full color (`hover:grayscale-0`).
- **Zoom:** All images should subtly scale on hover (`hover:scale-105` or `hover:scale-110`).

### Technical:
- Use `object-cover` to maintain aspect ratios.
- Use `overflow-hidden` on parent containers to contain zoom effects.
- Optimize images to 1200px width minimum for desktop, 600px for mobile.

---

## Button & CTA Design

### Primary Button (Green):
```html
<button class="bg-primary text-dark font-lato text-xs uppercase tracking-[0.2em] px-8 py-4 rounded-sm hover:bg-dark hover:text-white transition-all duration-300">
    Shop Now
</button>
```

### Text Link (Underlined):
```html
<a href="#" class="font-lato text-sm uppercase tracking-wide text-dark underline decoration-1 underline-offset-4 hover:text-primary transition-colors duration-200">
    Discover More
</a>
```

### Ghost Button (Outline):
```html
<button class="border border-dark text-dark font-lato text-xs uppercase tracking-[0.2em] px-8 py-4 hover:bg-dark hover:text-white transition-all duration-300">
    Add to Bag
</button>
```

---

## Subagent & Workflow Rules

### Code Review:
- **ALWAYS** use the `code-reviewer` agent before marking a feature complete.
- **ALWAYS** use Sonnet model for subagents unless explicitly overridden.

### Luxury Compliance Checklist (For Audits):
1. ✅ Minimum `py-32` section padding?
2. ✅ Headings are `text-6xl` or larger?
3. ✅ Transitions are `duration-500` or slower for images?
4. ✅ NO borders, shadows, or gradients on product cards?
5. ✅ Fine divider lines (`border-gray-200`) between sections?
6. ✅ Asymmetric layouts where appropriate?
7. ✅ Grayscale-to-color hover effects implemented?
8. ✅ Real copy (no placeholders)?

---

## Context Management

### Rules:
- **Warn me** when context usage exceeds 60%.
- **Include "Context: X%"** in responses when above 50%.
- **NEVER auto-compact.** I will manually trigger `/compact` when needed.

---

## File Structure

```
/seemy-luxury-proto/
├── index.html          # Main prototype (single-page)
├── CLAUDE.md           # This file (design system)
└── README.md           # Project overview (optional)
```

---

## Final Mandate

**You are not a developer. You are a Creative Director.**
Every line of code you write must pass the "Would this appear in Vogue?" test.
If it looks like a Bootstrap template, delete it and start over.

**Luxury is not a feature. It is a standard.**

---

## Quick Reference: Do's & Don'ts

| DO ✅ | DON'T ❌ |
|------|---------|
| Use `py-32` minimum for sections | Use `py-12` or `py-16` (too tight) |
| Use `text-8xl` for hero headlines | Use `text-4xl` or smaller for hero |
| Use `duration-700` for image hover | Use `duration-200` for image effects |
| Use `border-gray-200` dividers | Use thick borders (`border-2`, `border-4`) |
| Float products on white (no container) | Wrap products in shadowed cards |
| Use `grayscale` → color transitions | Use instant color changes |
| Use asymmetric grids (70/30, 60/40) | Use perfectly symmetrical layouts everywhere |
| Use real marketing copy | Use "Lorem Ipsum" or "Product Name" |

---

**Version:** 2.0 (Editorial Luxury)
**Last Updated:** 2026-01-11
**Maintained By:** Creative Direction Team
