# My Landing Page Project

## Tech Stack
- Astro 5.x (Static Site Generator)
- Tailwind CSS v4 (Utility-first CSS)
- TypeScript (Type safety)
- React (Only for interactive islands)
- Vite 6.x (Build tool, included with Astro)

## Commands
```bash
pnpm dev          # Start dev server (http://localhost:4321)
pnpm build        # Build for production
pnpm preview      # Preview production build
pnpm astro check  # Check TypeScript errors
```

## Project Structure
- `/src/components` - Reusable Astro and React components
- `/src/layouts` - Page layouts
- `/src/pages` - File-based routing (index.astro = homepage)
- `/public` - Static assets (images, fonts)

## Design System
- Primary Color: #3B82F6 (blue-500)
- Secondary Color: #8B5CF6 (violet-500)
- Font: Inter (Google Fonts)
- Spacing: 4, 8, 16, 24, 32, 48, 64px (Tailwind defaults)
- Max Width: 1280px (container)
- Breakpoints: sm:640px, md:768px, lg:1024px, xl:1280px

## Coding Conventions
- Use semantic HTML5 elements
- Mobile-first responsive design
- Astro components for static content
- React components ONLY for interactive elements (forms, modals)
- Tailwind utility classes (avoid custom CSS)
- Add client:load directive for React hydration
- Keep components under 200 lines
- TypeScript strict mode enabled

## Component Patterns
```astro
---
// Astro component example
interface Props {
  title: string;
  description?: string;
}
const { title, description } = Astro.props;
---
<section class="py-16 px-4">
  <h2 class="text-3xl font-bold">{title}</h2>
  {description && <p class="text-gray-600">{description}</p>}
</section>
```

## Interactive Components
Use React for forms, animations, state management:
```tsx
// ContactForm.tsx

```

## Testing Requirements
- Visual check on mobile (375px), tablet (768px), desktop (1280px)
- All images optimized and under 200KB
- Lighthouse score must be 90+ (mobile and desktop)
- No console errors

## Deployment
- Host: Vercel
- Branch strategy: main = production, dev = preview
- Auto-deploy on push to main