# Frontend — New Feature Prompts

## Bad Prompt

> "Add a dashboard page"

## Good Prompt

> **Context:** React 18 app with TypeScript, Tailwind CSS, React Router v6, and Zustand for state management. We use `shadcn/ui` for components. The app already has a `Layout` component with sidebar navigation in `components/Layout.tsx`.
>
> **Requirement:** Add a dashboard page that displays user analytics — total users, active sessions, and a line chart for signups over the last 30 days.
>
> **Acceptance Criteria:**
> - Route: `/dashboard` — add to existing router in `App.tsx`
> - Stat cards for "Total Users", "Active Sessions", "New Signups" using `shadcn/ui Card`
> - Line chart using `recharts` for 30-day signup trend
> - Data fetched from `GET /api/analytics/overview` via existing `useApi` hook in `hooks/useApi.ts`
> - Loading skeleton while data is fetching
> - Responsive — cards stack on mobile, grid on desktop
>
> **Scope:** Create `pages/Dashboard.tsx`, `components/dashboard/StatCard.tsx`, `components/dashboard/SignupChart.tsx`. Update `App.tsx` routes.
>
> **Constraints:** Follow existing component patterns in `pages/Settings.tsx`. Use Tailwind only — no inline styles. Don't install new UI libraries beyond `recharts`.

## Template

```
Context: [framework, UI library, state management, existing components]
Add: [page/component, what it displays]
Acceptance: [routes, components, data source, responsive behavior]
Scope: [files to create/modify]
Constraints: [follow existing patterns, allowed libraries]
```
