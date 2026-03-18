# Frontend — Enhancement Prompts

## Bad Prompt

> "Improve the form"

## Good Prompt

> **Context:** We have a multi-step registration form in `pages/Register.tsx` built with `react-hook-form` and `zod` validation. Currently all 3 steps (Personal Info, Address, Payment) are rendered as one long scrollable form.
>
> **Enhancement:** Convert it into a stepper/wizard UI with step-by-step navigation.
>
> **Current implementation:** Single `<form>` with all fields, one submit button at the bottom. Validation runs on submit for all fields at once.
>
> **Expected outcome:**
> - Step indicator at the top showing progress (Step 1 of 3)
> - "Next" / "Back" buttons for navigation between steps
> - Per-step validation — validate only current step's fields before allowing "Next"
> - Final "Submit" on the last step triggers the API call
> - Preserve form data when navigating back
>
> **Constraints:** Keep using `react-hook-form` and `zod` — don't switch libraries. Follow the existing form patterns. Use Tailwind for the stepper UI, no new component library.

## Template

```
Context: [current implementation, libraries in use]
Improve: [what specifically to enhance]
Current: [how it works now]
Expected: [bullet list of improved behavior]
Constraints: [libraries to keep, patterns to follow]
```
