# Prompt Engineering Guide for Software Engineers

A practical guide to writing effective prompts for AI coding assistants (Claude Code, Copilot, etc.) when working on real-world software engineering tasks.

---

## The C-R-A-F-T Framework

Structure your prompts using this framework for best results:

| Letter | Stands For | Purpose |
|--------|-----------|---------|
| **C** | Context | Stack, current state, what exists |
| **R** | Requirement | What exactly needs to be done |
| **A** | Acceptance Criteria | How to verify the output is correct |
| **F** | Files / Scope | Which files/modules to create or modify |
| **T** | Tech Constraints | Dependencies, patterns, things to avoid |

---

## 1. New Feature Prompts

### Bad Prompt

> "Add authentication to the app"

### Good Prompt

> **Context:** We have a Node.js/Express REST API with MongoDB. Currently there's no auth — all routes are open.
>
> **Requirement:** Add JWT-based authentication with signup and login endpoints.
>
> **Acceptance Criteria:**
> - POST `/api/auth/signup` — accepts `email`, `password`, hashes password with bcrypt, stores user, returns JWT
> - POST `/api/auth/login` — validates credentials, returns JWT
> - Auth middleware that protects all `/api/users/*` routes
> - JWT expires in 24h
>
> **Scope:** Create `auth.controller.ts`, `auth.middleware.ts`, update `routes/index.ts`
>
> **Constraints:** Use existing `User` model in `models/user.ts`. Don't add any new dependencies beyond `jsonwebtoken` and `bcrypt`.

### Template

```
Context: [stack, current state]
Add: [what exactly]
Acceptance: [bullet list of done-criteria]
Scope: [files/modules to create or modify]
Constraints: [libs, patterns, things to avoid]
```

---

## 2. Bug Fix Prompts

### Bad Prompt

> "Fix the payment bug"

### Good Prompt

> **Context:** Users report seeing "Payment Successful" but their order status stays `pending` in the database.
>
> **Bug:** In `services/payment.service.ts`, the `processPayment()` function calls Stripe API and returns success to the client, but the `order.update()` call after it is not awaited — so if it fails, the error is silently swallowed.
>
> **Expected:** Order status should update to `completed` before returning success to the client. If order update fails, payment should be refunded.
>
> **Repro steps:**
> 1. Create order → call `POST /api/payments`
> 2. Simulate DB timeout on order update
> 3. Client gets 200 but order stays `pending`
>
> **Fix scope:** `services/payment.service.ts` — wrap in transaction, await the update, add rollback logic.

### Template

```
Context: [where in the code]
Bug: [what's happening vs what should happen]
Repro: [steps to reproduce]
Root cause: [if you know it, or "investigate"]
Fix scope: [files to change]
```

---

## 3. Enhancement Prompts

### Bad Prompt

> "Make the search faster"

### Good Prompt

> **Context:** Our product search endpoint `GET /api/products?q=` does a full table scan on PostgreSQL (`products` table, ~2M rows). P95 latency is 3.2s.
>
> **Enhancement:** Optimize the search query in `repositories/product.repo.ts`.
>
> **Current implementation:** Uses `LIKE '%query%'` on `name` and `description` columns.
>
> **Expected outcome:** P95 under 500ms for typical queries.
>
> **Suggestions I'm considering:**
> - Add GIN index with `pg_trgm` for trigram matching
> - Or switch to `tsvector` full-text search
>
> **Constraints:** No Elasticsearch — we want to keep the stack simple. Must remain compatible with existing filters (category, price range).

### Template

```
Context: [current implementation + metrics]
Improve: [what specifically]
Target: [measurable goal]
Approach: [your ideas, or "suggest options"]
Constraints: [what not to change]
```

---

## Frontend Prompts

Detailed frontend prompt examples are organized in the [frontend/](frontend/) folder:

| File | Topic |
|------|-------|
| [new-feature.md](frontend/new-feature.md) | New Feature (dashboard page with charts) |
| [bug-fix.md](frontend/bug-fix.md) | Bug Fix (modal error handling) |
| [enhancement.md](frontend/enhancement.md) | Enhancement (multi-step form wizard) |
| [styling-ui.md](frontend/styling-ui.md) | Styling & UI (responsive grid) |
| [state-management.md](frontend/state-management.md) | State Management (Zustand cart store) |

---

## Key Principles

| Principle | Why It Matters |
|-----------|---------------|
| **State what exists** | AI can't see your whole codebase — tell it what's already there |
| **State what's wrong** | For bugs, separate symptom vs root cause |
| **State boundaries** | Which files to touch, which to leave alone |
| **State constraints** | Dependencies, perf targets, backward compatibility |
| **Give acceptance criteria** | Removes ambiguity, makes output verifiable |

---

## Pro Tips

1. **Be specific upfront** — fewer back-and-forth corrections needed
2. **Provide the right constraints** — that's your biggest leverage as a senior engineer
3. **Include file paths** — helps AI navigate your codebase accurately
4. **Mention existing patterns** — "follow the pattern used in `user.controller.ts`"
5. **State what NOT to do** — "don't refactor unrelated code" or "don't add new dependencies"
