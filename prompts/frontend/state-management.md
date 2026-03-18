# Frontend — State Management Prompts

## Bad Prompt

> "Add global state for the cart"

## Good Prompt

> **Context:** React app with Zustand. Currently, cart state lives in `useState` inside `components/ProductPage.tsx` and is lost on navigation. Existing Zustand stores follow the pattern in `stores/authStore.ts`.
>
> **Requirement:** Move cart state to a Zustand store with persistence.
>
> **Acceptance Criteria:**
> - Create `stores/cartStore.ts` following the pattern in `authStore.ts`
> - Actions: `addItem`, `removeItem`, `updateQuantity`, `clearCart`
> - Persist to `localStorage` using Zustand's `persist` middleware
> - Cart item shape: `{ productId, name, price, quantity }`
> - Cart badge in `components/Navbar.tsx` shows total item count
> - Cart survives page refresh
>
> **Scope:** Create `stores/cartStore.ts`. Update `ProductPage.tsx`, `CartPage.tsx`, `Navbar.tsx`.
>
> **Constraints:** Don't use Redux or Context API. Follow existing Zustand patterns. No changes to API calls — cart is client-side only for now.

## Template

```
Context: [current state approach, existing patterns]
Requirement: [what state to manage, where]
Acceptance: [store shape, actions, persistence, UI updates]
Scope: [files to create/modify]
Constraints: [library choice, patterns to follow]
```
