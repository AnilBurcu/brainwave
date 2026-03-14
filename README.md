# Brainwave

A modern AI SaaS landing page built with React, featuring scroll-driven parallax animations, a custom SVG design system, and a fully responsive component architecture.

`React + Vite` | `Component-Driven Architecture` | `Custom SVG System` | `Responsive Design`

<!-- Live Demo: Add deployment URL here -->

<!-- Screenshots: Add 2-3 screenshots here -->

---

## Features

- Scroll and mouse-driven parallax animations using react-just-parallax
- Custom SVG gradient system with globally defined, reusable gradient references
- Fully responsive layout with mobile-first breakpoints and adaptive aspect ratios
- Data-driven section rendering with centralized content constants
- Polymorphic button component with SVG-based gradient borders
- Smooth scroll navigation with scroll-lock for mobile menu overlay
- CSS-only entrance animations triggered by React mount state
- Conic gradient borders and radial gradient overlays for visual depth

## Tech Stack & Architecture

**Core**: React 18, Vite 5, Tailwind CSS 3, React Router 6

**Animation**: react-just-parallax (scroll + mouse tracking), CSS transforms, mount-based transitions

**Design System**: Custom Tailwind configuration with a 6-color brand palette, 13-step neutral scale, three font families (Sora, Source Code Pro, Space Grotesk), and extended spacing/opacity utilities

**Architecture**: The project follows a component composition pattern with clear separation between layout components, section components, and design (decorative) components. All sections share a unified `Section` wrapper and `Heading` component, while visual elements like gradients, curves, and decorative lines live in a dedicated `design/` layer. Content data is fully externalized into a constants module, keeping components focused on structure and interaction.

## Technical Highlights

**Custom SVG Gradient System**
A global `ButtonGradient` component defines reusable SVG `<linearGradient>` elements that are referenced across the application via `url(#gradient-id)`. This avoids gradient duplication, keeps bundle size minimal, and enables consistent gradient styling on buttons, taglines, and decorative borders from a single source of truth.

**Parallax & Animation Strategy**
Animations rely on CSS transforms and react-just-parallax rather than heavier libraries like Framer Motion. Mouse-tracking parallax uses low-strength values and absolutely positioned elements to avoid layout recalculations. Entrance animations are handled through React state changes on mount, applying CSS transitions without JavaScript animation loops.

**Responsive Image & Layout System**
Images use explicit `width`/`height` attributes as intrinsic size hints to prevent cumulative layout shift. Responsive aspect ratios change across breakpoints (`aspect-[33/40]` on mobile to `aspect-[1024/490]` on desktop), and the layout switches between stacked and grid compositions using Tailwind's responsive prefixes.

**Component Composition Pattern**
Each page section follows a consistent pattern: a `Section` wrapper handles spacing, cross decorations, and IDs, while a `Heading` component standardizes titles and taglines. Design-specific visuals (background circles, gradient overlays, decorative curves) are isolated in `components/design/`, keeping section logic clean and each layer independently maintainable.

## Project Structure

```
brainwave/
├── src/
│   ├── assets/
│   │   ├── svg/                # Reusable SVG components (gradients, icons, clip paths)
│   │   ├── benefits/           # Benefit card backgrounds and icons
│   │   ├── collaboration/      # App icons and curve graphics
│   │   ├── hero/               # Hero section images and backgrounds
│   │   ├── services/           # Service showcase images
│   │   ├── roadmap/            # Roadmap section assets
│   │   ├── pricing/            # Pricing decoration assets
│   │   └── index.js            # Centralized asset exports
│   ├── components/
│   │   ├── design/             # Decorative/visual components per section
│   │   ├── Section.jsx         # Reusable section wrapper
│   │   ├── Heading.jsx         # Standardized section heading
│   │   ├── Button.jsx          # Polymorphic button with SVG borders
│   │   ├── Header.jsx          # Fixed navigation with mobile menu
│   │   ├── Hero.jsx            # Hero with parallax animations
│   │   ├── Benefits.jsx        # Feature cards with clip-path overlays
│   │   ├── Collaboration.jsx   # Circular icon layout
│   │   ├── Services.jsx        # AI capabilities showcase
│   │   ├── Pricing.jsx         # Three-tier pricing grid
│   │   ├── Roadmap.jsx         # Development roadmap grid
│   │   └── Footer.jsx          # Footer with social links
│   ├── constants/
│   │   └── index.js            # All section content and navigation data
│   ├── App.jsx                 # Root layout composing all sections
│   ├── main.jsx                # Entry point with router setup
│   └── index.css               # Global styles and Tailwind layers
├── tailwind.config.js          # Extended design system configuration
├── vite.config.js              # Vite build configuration
└── package.json
```

## Getting Started

**Prerequisites**: Node.js 18+

```bash
# Clone the repository
git clone https://github.com/<your-username>/brainwave.git
cd brainwave

# Install dependencies
npm install

# Start the development server
npm run dev
```

The app runs at `http://localhost:5173` by default.

```bash
# Build for production
npm run build

# Preview the production build
npm run preview
```
