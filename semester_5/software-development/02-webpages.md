# Frontend Development Overview

## Core Concepts

* **UI Rendering**: Translating data into visual components.
* **State Management**: Handling dynamic data and UI updates.
* **Event Handling**: Capturing and responding to user interactions.
* **Routing**: Managing navigation in single-page applications.
* **Performance**: Optimizing load times, bundle sizes, and render speed.

## Core Technologies

### HTML

* Defines document structure.
* Semantic tags improve accessibility and SEO.

### CSS

* Controls layout, typography, and visual styling.
* Includes responsive design, flexbox, grid.

### JavaScript

* Adds logic, interactivity, and dynamic DOM manipulation.

## Modern Frameworks and Libraries

### React

* Component-based UI architecture.
* Virtual DOM for efficient updates.

### Vue

* Reactive data binding.
* Lightweight with a gentle learning curve.

### Angular

* Full MVC framework.
* Built-in tooling for routing, forms, and dependency injection.

## Build Tools

### Webpack

* Module bundler with loaders and plugins.

### Vite

* Fast dev server with native ES modules and optimized production builds.

### Rollup

* Tree-shaking focused bundler for libraries.

## Package Managers

* **npm**
* **Yarn**
* **pnpm**

## UI Component Libraries

* **Tailwind CSS**: Utility-first styling.
* **Material UI**: Prebuilt React components.
* **Bootstrap**: Grid, utilities, and responsive components.

## Testing Tools

* **Jest**: Unit testing.
* **React Testing Library**: Component behavior testing.
* **Cypress**: End-to-end testing.

## API Interaction

* **Fetch API**
* **Axios**

## Developer Utilities

* **ESLint**: Linting.
* **Prettier**: Formatting.
* **TypeScript**: Static typing for JavaScript.

## Deployment Targets

* Static hosting (Netlify, Vercel)
* CDNs
* Containerized environments

## Unidirectional Data Flow
Action -> Reducer/Store -> Updated Applications State -> UI Re-renders

## Rest vs GraphQL
- Rest 
	- URL based endpoints
	- Multiple requests
- GraphQL
	- Single endpoint
	- Request exact data you need