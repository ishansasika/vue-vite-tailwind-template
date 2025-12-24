# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a modern Vue 3 + TypeScript + Tailwind CSS template built with Vite. It includes a complete, production-ready UI with four pages (Home, About, Services, Contact), responsive navigation, footer, and a blue-purple gradient design theme.

## Essential Commands

```bash
# Development
npm run dev                  # Start Vite dev server (default: http://localhost:5173)

# Type Checking
npm run type-check           # Run Vue TypeScript compiler without emitting files

# Build
npm run build                # Type check and create production build in dist/ folder
npm run preview              # Preview production build locally
```

## Architecture

### Tech Stack
- **Vue 3.5** - Progressive JavaScript framework with Composition API
- **Vite 6** - Next-generation frontend build tool with HMR
- **TypeScript 5.7** - Static type checking with strict mode
- **Tailwind CSS 3.4** - Utility-first CSS framework
- **Vue Router 4.5** - Official router for Vue.js

### Application Structure
- Entry point: `index.html` → `src/main.ts` → `src/App.vue`
- `App.vue` contains the main layout structure with Header, Footer, and router-view
- All routes defined in `src/router/index.ts` using createRouter
- All routes wrapped in persistent layout (Header + Footer remain across navigation)

### Routing Structure
Four pages are configured in `src/router/index.ts`:
- `/` - Home page with hero, features, stats, and CTAs
- `/about` - About page with mission, tech stack, values, and team
- `/services` - Services showcase with 6 service cards
- `/contact` - Contact page with form and contact information

Route definitions use declarative objects passed to createRouter:
```typescript
const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    { path: '/', name: 'home', component: Home },
    { path: '/about', name: 'about', component: About },
    { path: '/services', name: 'services', component: Services },
    { path: '/contact', name: 'contact', component: Contact },
    { path: '/:pathMatch(.*)*', redirect: '/' }  // Catch-all route
  ]
})
```

**Catch-all Route**: Any invalid/unmatched paths automatically redirect to home (src/router/index.ts:30)

### Component Organization
All components are Single File Components (.vue) using the Composition API with `<script setup>`:
- **Components**: `src/components/` (Header.vue, Footer.vue)
- **Pages**: `src/pages/` (Home.vue, About.vue, Services.vue, Contact.vue)
- Each component uses `<script setup lang="ts">` for TypeScript support
- Template, script, and styles are co-located in .vue files

**Layout Components:**
- `Header.vue`: Sticky navigation with logo, nav links, mobile menu, active route highlighting
- `Footer.vue`: Multi-column footer with brand info, quick links, resources, social icons

**Page Components:**
- `Home.vue`: Multi-section landing with hero, features, stats, CTAs
- `About.vue`: Mission statement, tech stack grid, values cards, team profiles with images
- `Services.vue`: 6 service cards with icons, features, color-coded themes
- `Contact.vue`: Two-column layout with contact info and functional form

### Design System
**Color Theme**: Blue-purple gradient (`from-blue-500/600 to-purple-600`)
- Primary gradient used in: buttons, logos, hero text, stats section
- Color-coded service cards: blue, purple, pink, green, indigo, yellow

**Dark Mode**: Tailwind dark mode classes throughout
- Uses `dark:` prefix for dark mode variants
- Applied to text, backgrounds, borders

**Responsive Design**: Mobile-first breakpoints
- Mobile menu toggle in Header for small screens
- Grid layouts adjust: `grid-cols-1 md:grid-cols-2 lg:grid-cols-3`
- Responsive spacing and typography

### TypeScript Configuration
- `tsconfig.json` - Root config with project references
- `tsconfig.app.json` - Main app config with strict mode, Vue JSX support
- `src/env.d.ts` - Vite type definitions

### Styling Architecture
- `src/style.css` - Tailwind directives (@tailwind base/components/utilities) + global styles
- `src/App.css` - Page container flexbox layout for sticky footer
- `tailwind.config.js` - Content paths for all source files
- `postcss.config.js` - Tailwind + Autoprefixer

### Adding New Routes
1. Create page component: `src/pages/[PageName].vue`
2. Import in `src/router/index.ts`: `import PageName from '../pages/PageName.vue'`
3. Add to routes array BEFORE the catch-all route:
   ```typescript
   {
     path: '/page-name',
     name: 'pageName',
     component: PageName
   }
   ```
4. Add navigation link in `Header.vue` navLinks array
5. Add footer link in `Footer.vue` if needed

### State Management
Currently uses Vue's Composition API with ref/reactive for local component state:
- Header: `isMenuOpen` ref for mobile menu toggle
- Contact: `formData` ref for form inputs
No global state management library included - add Pinia if needed

### Form Handling
Contact form (src/pages/Contact.vue):
- Uses v-model for two-way binding with reactive formData
- Form validation via HTML5 required attributes
- @submit.prevent handler prevents default, logs data, shows alert, resets form
- No backend integration - implement API call in handleSubmit as needed

### File Extensions
- `.vue` - Single File Components with template, script, and style sections
- `.ts` - TypeScript files (main.ts, router/index.ts, env.d.ts)
- `.css` - Stylesheets (style.css, App.css)
- `.js` - Config files (vite.config.ts is actually TypeScript)
- `.json` - Package configuration (package.json, tsconfig files)

## Vue 3 Composition API Patterns

### Script Setup
All components use `<script setup lang="ts">` which:
- Automatically exposes imports and top-level bindings to template
- Provides better TypeScript inference
- Reduces boilerplate compared to Options API

Example:
```vue
<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const count = ref(0)
const increment = () => count.value++
</script>

<template>
  <button @click="increment">{{ count }}</button>
</template>
```

### Reactivity
- Use `ref()` for primitive values: `const count = ref(0)`
- Use `reactive()` for objects: `const state = reactive({ name: 'John' })`
- Access ref values in script with `.value`: `count.value++`
- No need for `.value` in templates: `{{ count }}`

### Router
- Use `useRoute()` to access current route information
- Use `useRouter()` to programmatically navigate
- Use `<RouterLink>` component for navigation links
- Use `<RouterView>` for rendering matched routes
