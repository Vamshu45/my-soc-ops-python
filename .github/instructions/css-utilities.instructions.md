---
description: CSS utility classes and styling practices for this Python/Jinja2 project.
---

# CSS Styling Practices

## Overview
This project uses custom CSS utility classes (similar to Tailwind) defined in `app/static/css/app.css`. These provide consistent, composable styling without external dependencies.

## Available Utilities

### Layout
```css
.flex, .flex-col, .flex-1
.grid, .grid-cols-5
.items-center, .justify-center, .justify-between
```

### Spacing
```css
.p-1 through .p-6, .px-*, .py-*
.mb-2 through .mb-8, .mx-auto
.gap-1, .space-y-2
```

### Sizing
```css
.h-full, .w-full, .min-h-full
.max-w-xs, .max-w-sm, .max-w-md
.aspect-square
```

### Colors
```css
.bg-white, .bg-gray-50, .bg-gray-100
.bg-accent (primary blue), .bg-marked (green for selected)
.text-gray-500 through .text-gray-900
.text-green-600, .text-amber-500
```

### Typography
```css
.text-xs through .text-5xl
.font-semibold, .font-bold
.text-center, .text-left
.leading-tight
```

### Borders & Shadows
```css
.border, .border-b
.rounded, .rounded-lg, .rounded-xl
.shadow-sm, .shadow-xl
```

### Positioning
```css
.fixed, .absolute, .relative
.inset-0, .z-50
```

### Animation
```css
.transition-all, .transition-colors
.duration-150
.animate-[bounce_0.5s_ease-out]
```

### Emphasis & Highlights (Playfair Display)
Uses Google Font **Playfair Display** for elegant emphasis:

```css
.font-playfair              /* Playfair Display, bold (700) */
.underline                  /* Simple underline with 2px thickness */
.underline-accent           /* Blue underline (3px) */
.highlight                  /* Playfair Display bold text, 1.125rem */
.highlight-underline        /* Playfair + blue underline (3px) */
.highlight-accent           /* Bold Playfair (900), blue, underlined */
.emphasis-title             /* Large Playfair (1.875rem) with blue underline */
```

**Usage Examples:**
```html
<!-- Simple highlight -->
<span class="highlight">Important Info</span>

<!-- Highlight with underline -->
<span class="highlight-underline">Key Point</span>

<!-- Accent emphasis -->
<span class="highlight-accent">Call to Action</span>

<!-- Large title with emphasis -->
<h2 class="emphasis-title">Section Title</h2>
```

## Best Practices

1. **Compose utilities**: Combine classes for complex layouts
2. **Add new utilities to app.css**: When needed, follow existing patterns
3. **Use CSS variables**: For theming, define in `:root`
4. **Keep specificity low**: Utility classes should be single-purpose
5. **Playfair usage**: Reserve highlight classes for truly important information to maintain visual hierarchy

## Example Component Styling
```html
<div class="flex flex-col items-center justify-center min-h-full bg-gray-50">
    <h1 class="emphasis-title mb-4">Welcome</h1>
    <button class="px-6 py-3 bg-accent text-white rounded-lg font-semibold">
        <span class="highlight-underline">Start Game</span>
    </button>
</div>
```
