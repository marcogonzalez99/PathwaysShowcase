# Changelog

All notable changes to Pathways will be documented here.

## [Unreleased]

## [1.4.0] - 2026-03-21

### Added
- `src/components/NotFound.astro` custom 404 page component and a back-to-home button
- `src/pages/404.astro` dedicated 404 page using `NotFound` component 
- SVG sun and moon icons from Heroicons in `DarkMode.astro`, replacing emoji with proper scalable icons
- `D` keyboard shortcut to toggle dark mode
- `tags` optional field on `Card` interface in `types.ts` for per-card pill labels
- Tag pills rendered in `LinkCard.astro` using `?.map()`

### Updated
- `DarkMode.astro` emojis replaced with inline Heroicon SVGs

## [1.3.0] - 2026-03-21

### Added
- `src/data/types.ts` extracted all TypeScript interfaces (`SocialLink`, `Card`, `Section`, `PageData`) out of `links.ts` into a dedicated types file
- `theme-color` meta tag in `BaseLayout.astro` using `accent_color` per page for browser UI theming
- `<link rel="preload">` for header and profile images in `BaseLayout.astro`
- `@keyframes hero-reveal` in `global.css` for the header image scale-in animation
- View Transition duration and easing (`0.4s ease`) for page-to-page navigation in `global.css`

### Updated
- Dark mode toggle now uses `document.startViewTransition()` for an animated theme switch instead of an instant class swap
- `--color-text-secondary` in light mode corrected to `#5a5e63`
- `--color-profile-border` in dark mode updated to `#a8adb3`
- `src/data/links.ts` now imports types from `../data/types` instead of defining them inline

### Removed
- TypeScript interfaces removed from `links.ts` (moved to `types.ts`)
- `public/cursor.svg` custom cursor removed
- `public/images/cards/shineburst_card.jpg` unused card removed

## [1.2.1] - 2026-03-15

### Added
- Built by Nebulabs footer

## [1.2.0] - 2026-03-15

### Added
- `robots.txt` file to `public/` with basic crawl directives for search engines
- `sitemap.xml` auto-generated at build time using `astro-sitemap` integration, listing all pages for improved SEO
- Open Graph meta tags in `BaseLayout.astro` for better link sharing previews on social media platforms
- `aria-label` attributes to all interactive elements (cards, social buttons, section links) for improved accessibility
- lazy loading (`loading="lazy"`) on all non-critical images (cards, social icons) to optimize page load performance
- eager loading (`loading="eager"`) on critical images (header and profile images) to ensure they load as soon as possible for better user experience
- asynchronous decoding (`decoding="async"`) on all images to allow the browser to render other content while images are being decoded, improving overall page load performance
- `accent_color` field in `PageData` interface to allow for pathway-specific accent colors used in focus rings and future design elements

## [1.1.0] - 2026-03-14

### Added
- `ClientRouter` from `astro:transitions` to `BaseLayout.astro` for client-side page transitions
- `@keyframes fade-up` animation in `global.css`
- `fade-up` entrance animations on `LinkCard.astro`, `SocialButtons.astro`, and `Sections.astro`
- `transition:name` on header and profile images in `ProfileCard.astro` for element morphing between pages
- `description` field to `PageData` interface in `links.ts`

### Removed
- Unused `--color-bg-dark` CSS from `global.css`

## [1.0.0] - 2026-03-09

### Added
- Card images to `public/images/cards/` (`apple_music.jpg`, `instagram.png`, `kofi.png`, `polaris.png`, `spotify.jpg`, `youtube.jpg`)

## [0.9.0] - 2026-03-08

### Removed
- Old Linkedin Logo

### Updated
- `LinkCard.astro` - Added hover effects, changed text color to match dark/light mode
- `ProfileCard.astro` - Added `DarkMode` component. Updated Profile Image size. Added variables for styling
- `Sections.astro` - Updated component to use hover effects, scaling and variable styling from `global.css`. Added a flex grid for both mobile and desktop usage
- `SocialButtons.astro` - Updated hover effects

### Added
- `DarkMode` - Added new component to store Dark Mode UI
- New Linkedin Logo

## [0.8.0] - 2026-03-07

### Updated
- `ProfileCard.astro` - Profile image border now uses `--color-profile-border`
- `SocialButtons.astro` - Social icon `alt` and `title` attributes now use `link.label`
- `BaseLayout.astro` - Dark mode toggle now correctly shows only the relevant icon (`🌙` in light, `☀️` in dark) using `dark:hidden` / `hidden dark:inline`
- `src/data/links.ts` - Added `label` field to `SocialLink` interface; populated labels across all four page data objects
- `src/styles/global.css` - Added `--color-profile-border` CSS variable for light (`#FFFFFF`) and dark (`#2B2B2B`) modes

## [0.7.0] - 2026-03-06

### Added
- Dark Mode temporary toggle

## [0.6.0] - 2026-02-27

### Added
- `Section` interface in `src/data/links.ts` | typed interface with `text` and `link` fields
- `Sections.astro` | New component wired into `BaseLayout.astro` via `sections={page.sections}`

### Updated
- `src/data/links.ts` | replaced flat `section_label`/`section_link` strings in `PageData` with `sections: Section[]`, customized `social_links` per page to reflect each account's actual platforms; customized `sections` per page so each page links to the other three and excludes itself
- `LinkCard.astro` | Added `hover:scale-105` transition effect on card hover

## [0.5.0] - 2026-02-26

### Updated
- `README.md` - Updated Features list to accurately reflect the project's specific implementation.
- Cleaned up Final Design section; converted "Other Potential tabs" to a proper Roadmap section.
- Added banner image at top
- Merged and expanded "What is Pathways?" to cover both what and why; added Project Structure tree

## [0.4.0] - 2026-02-24

### Added
- `SocialButtons.astro` - Implemented component: renders social icon images from `/images/social/` using `.map()` over a `SocialLink[]` prop, with circular bordered styling

### Updated
- `src/data/links.ts` - Refactored `SocialLinks` interface into `SocialLink` (singular) with explicit `icon` and `link` fields; updated `social_links` type to `SocialLink[]` across all page data; updated `Card` interface to use `text` and `alt` fields; added real card data to `indexData`; reorganized image paths into subdirectories (`/images/headers/`, `/images/logos/`, `/images/cards/`, `/images/social/`)
- `LinkCard.astro` - Implemented component: replaced flex layout with responsive CSS Grid (`grid-cols-1 lg:grid-cols-3`), made full card clickable via wrapping `<a>` tag, added text label bar at bottom of each card
- `BaseLayout.astro` - Updated `LinkCard` usage to pass `cards={page.cards}`

## [0.3.0] - 2026-02-23

### Updated
- `ProfileCard.astro` - Implemented full component: header image, circular profile image overlapping header, name, and tagline
- `src/data/links.ts` - Populated `header_image` and `profile_image` paths for all four pages using correct root-relative `/images/` paths

## [0.2.0] - 2026-02-22

### Added
- `BaseLayout.astro` - Shared layout component accepting a `PageData` prop, renders profile, social buttons, cards, and section link
- `src/data/links.ts` - Typed interfaces (`PageData`, `Card`, `SocialLink`) and data stubs for all four pages (`indexData`, `shineburstData`, `polarisData`, `skyholdsData`)

## [0.1.0] - 2026-02-21

### Added
- Initial Astro project setup with Tailwind CSS
- `src/pages/` for four pages: `index`, `polaris`, `shineburst`, `skyholds`
- `ProfileCard.astro` and `LinkCard.astro` components
- README
