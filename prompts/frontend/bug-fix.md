# Frontend — Bug Fix Prompts

## Bad Prompt

> "The modal is broken"

## Good Prompt

> **Context:** React app using `shadcn/ui Dialog` component. We have a "Delete User" confirmation modal in `components/UserActions.tsx`.
>
> **Bug:** When the user clicks "Delete" and the API call fails, the modal closes anyway and shows no error. The user thinks the deletion happened but it didn't.
>
> **Expected:** On API error, the modal should stay open, show an inline error message ("Failed to delete user. Please try again."), and the "Delete" button should re-enable.
>
> **Repro steps:**
> 1. Open user list → click delete on any user
> 2. Simulate API failure (disconnect network or return 500)
> 3. Modal closes, no error shown, user still exists
>
> **Root cause:** In `UserActions.tsx:45`, the `finally` block calls `setOpen(false)` unconditionally — it should only close on success.
>
> **Fix scope:** `components/UserActions.tsx` — move `setOpen(false)` to the `.then()` block, add error state and display it inside the Dialog.

## Template

```
Context: [component, library used]
Bug: [what happens vs what should happen]
Repro: [exact steps to reproduce]
Root cause: [file:line, what's wrong, or "investigate"]
Fix scope: [files to change, what to fix]
```
