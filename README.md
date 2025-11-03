DOCUMENTATION


# Smart Scheduler

Smart Scheduler is an intelligent classroom and timetable management platform that helps institutions automate classroom allocation, generate optimized timetables, and manage faculty schedules.

## Features
- Smart timetable generation (frontend UI + integration points)
- Classroom allocation based on capacity and equipment
- Faculty management and workload balancing
- Real-time updates and conflict resolution
- Export schedules and download reports

## Quick start (development)
1. Clone the repository:
   ```bash
   git clone https://github.com/satvik66385/repo2.git
   cd repo2
   ```

2. Install dependencies (example uses npm):
   ```bash
   npm install
   # or
   pnpm install
   ```

3. Start the development server (example with Vite):
   ```bash
   npm run dev
   ```

4. Build for production:
   ```bash
   npm run build
   ```

## Project layout (recommended)
- public/ — static assets and index.html  
- src/ — React + TypeScript source
  - src/pages/ — route pages (Landing, Dashboard, Timetable, Classrooms, Faculty)
  - src/components/ — shared UI components (Navbar, Card, Button, etc.)
  - src/styles/ — Tailwind CSS and global styles
- docs/ — project documentation and architecture notes
- package.json — npm scripts and dependencies

## Documentation
See `docs/PROJECT.md` for project architecture, coding conventions, environment variables, and deployment notes.

## Contributing
Contributions are welcome. Please:
1. Fork the repository (or create a branch).
2. Implement your change with tests where appropriate.
3. Open a pull request describing the change.

Follow the coding conventions in `docs/PROJECT.md`.

## License
This project is licensed under the MIT License — see `LICENSE` for details.





# Project Documentation — Smart Scheduler

This document provides architecture notes, development conventions, environment variables, and deployment guidance.

## Overview
Smart Scheduler is a frontend-first application (React + TypeScript) providing UI for timetable generation, classroom allocation, and faculty management. The architecture is modular with pages, shared UI components, and a thin data-layer that can be connected to a backend API.

## Architecture
- UI: React + TypeScript, component-driven (e.g., Navbar, Card, Button, Avatar).
- Styling: Tailwind CSS (custom design tokens in CSS variables).
- State & Data: plan to use React Query (@tanstack/react-query) for server state.
- Routing: react-router-dom for client-side routes.

## Folder structure (recommended)
```
/public
/src
  /components
    /ui          # design system primitives (Button, Card, Avatar, Badge, etc.)
    Navbar.tsx
  /pages         # route pages (Landing, Dashboard, Timetable, Classrooms, Faculty)
  /utils         # helpers, formatters, API wrappers
  main.tsx
/docs
  PROJECT.md
tailwind.config.js
package.json
```

## Environment variables
- VITE_API_URL — backend API base URL
- VITE_APP_ENV — development | staging | production

Store these in `.env` or `.env.local` (never check secrets into source control).

## Coding conventions
- TypeScript strict mode enabled (recommended).
- Use React.FC only where appropriate; prefer named function components.
- Prefer composable UI primitives. Use `asChild` pattern or `NavLink` for accessible links.
- Use semantic HTML and ARIA where needed for accessibility.
- Use stable keys for lists; avoid index keys unless items are static.

## Styling & Design tokens
Design variables are defined as CSS custom properties (HSL triplets). Use utility classes and prefer using design tokens for colors and spacing.

Example:
```css
/* Use like: color: hsl(var(--primary)); */
```

## Data fetching
Use React Query for caching and background updates. Structure API calls in `/src/api` and expose typed hooks like `useClassrooms`, `useTimetable`, `useFaculty`.

## Testing
- Unit tests: Vitest or Jest + Testing Library
- E2E: Playwright or Cypress

## CI / CD
- Use GitHub Actions for CI:
  - Install deps, run lint/type-check/tests on PRs.
  - Build on merges to `main`.
- Deploy: Vercel / Netlify for frontend; configure environment variables in the hosting provider.

## Deployment notes
- Ensure `VITE_API_URL` is set in hosting environment.
- Build command: `npm run build`; output served from `dist/` (Vite) or equivalent.

## Next steps (recommended)
- Add initial React + Vite starter with Tailwind config and example pages.
- Add unit test scaffolding and basic linting (ESLint + Prettier).
- Add GitHub Actions workflow for CI.
