# Frontend — Styling & UI Prompts

## Bad Prompt

> "Make it look better on mobile"

## Good Prompt

> **Context:** Next.js app with Tailwind CSS. The product listing page at `app/products/page.tsx` uses a 4-column CSS grid. On mobile (< 640px), the cards overflow horizontally and text gets cut off.
>
> **Requirement:** Make the product grid fully responsive.
>
> **Expected outcome:**
> - Mobile (< 640px): single column, full-width cards
> - Tablet (640px–1024px): 2 columns
> - Desktop (> 1024px): 4 columns (current layout)
> - Product images should maintain aspect ratio, not stretch
> - Price and "Add to Cart" button should always be visible without scrolling within a card
>
> **Scope:** `app/products/page.tsx` and `components/ProductCard.tsx`
>
> **Constraints:** Tailwind only — no media query CSS files. Don't change the card content or data fetching logic.

## Template

```
Context: [framework, CSS approach, current layout]
Requirement: [what needs to be responsive/styled]
Expected: [breakpoint-by-breakpoint behavior]
Scope: [files to modify]
Constraints: [CSS approach, what not to change]
```
