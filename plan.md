# Freshen Interiors — Coming Soon Landing Page

## Overview

Build a "Coming Soon" landing page for Freshen Interiors using the existing Astro project. The page will be deployed live to inform visitors that the full website is under construction.

## Company Description

Freshen Interiors is an interior design company that offers design services for small scale remodels up to completely new construction build homes.

## Brand Assets

- **Logo:** `public/freshen-interiors-logo.svg`
- **Brand Colors:**
  - Primary: `#304A3D` (deep forest green)
  - Secondary: `#F6EFE4` (warm cream)
- **Brand Fonts:**
  - Headings: [Bungee](https://fonts.google.com/specimen/Bungee) (Google Fonts)
  - Body: [Jost](https://fonts.google.com/specimen/Jost) (Google Fonts)

## Page Structure

### Header
- Freshen Interiors SVG logo
- Social media links (Instagram, Facebook)

### Hero Section
- Large "Coming Soon" headline (Bungee font, primary green)
- Brief company description / tagline
- Secondary cream (`#F6EFE4`) background with subtle design accents

### About Section
- Short paragraph about Freshen Interiors and the services offered
- Design services: small scale remodels to completely new construction build homes

### Contact Section
- **Contact form** with fields:
  - Sender email (required)
  - Message text box (required)
  - Submit button
- **Bot protection:**
  - Honeypot field (hidden input that bots fill out — submissions with it filled are rejected)
  - Client-side JS timestamp check (reject instant submissions)
- **Form delivery:** Use [Formspree](https://formspree.io/) or [Web3Forms](https://web3forms.com/) to forward submissions to fresheninteriors@gmail.com (no backend needed, works with static Astro/Vercel deploy)
- Social links: Instagram, Facebook

### Footer
- Social media icons (Instagram, Facebook)
- Copyright notice

## Design Direction

Based on the inspiration images, the page should feel:
- **Clean and modern** with generous whitespace
- **Bold typography** for the "Coming Soon" heading
- **Soft, elegant color palette** aligned with the brand
- **Minimal layout** — single page, no complex navigation
- Contact info and socials easily accessible

## Tech Stack

- **Framework:** Astro (already scaffolded)
- **Styling:** Native CSS (scoped Astro styles + global stylesheet)
- **Deployment:** Vercel

## Contact & Social Info

- **Email:** fresheninteriors@gmail.com
- **Instagram:** [@freshen_interiors](https://instagram.com/freshen_interiors)
- **Facebook:** [Freshen Interiors](https://www.facebook.com/profile.php?id=61587028787237)

## Implementation Plan

### Phase 1: Project Setup & Brand Foundation

- [x] 1.1 Add SVG logo to `public/freshen-interiors-logo.svg`
- [x] 1.2 Import Google Fonts (Bungee + Jost)
  - Add `<link>` tags or `@import` for Bungee (headings) and Jost (body) in a shared layout or head
- [x] 1.3 Create global stylesheet (`src/styles/global.css`)
  - Define CSS custom properties: `--color-primary: #304A3D`, `--color-secondary: #F6EFE4`
  - Set base font-family to Jost
  - Set heading font-family to Bungee
  - Add CSS reset / normalize basics (box-sizing, margin, etc.)
- [x] 1.4 Create base layout component (`src/layouts/BaseLayout.astro`)
  - Includes `<head>` with meta charset, viewport, fonts, global styles
  - Wraps page content with consistent structure

### Phase 2: Page Sections — Build the UI

- [x] 2.1 **Header** (`src/components/Header.astro`)
  - Display SVG logo (link to `/`)
  - Social media icon links (Instagram, Facebook)
  - Responsive: hamburger or stacked on mobile if needed, or keep minimal
- [x] 2.2 **Hero Section** (`src/components/Hero.astro`)
  - Large "Coming Soon" headline in Bungee font, primary green color
  - Subheadline / tagline (e.g., "Our new website is on its way.")
  - Cream background (`#F6EFE4`) with optional subtle decorative accents
- [x] 2.3 **About Section** (`src/components/About.astro`)
  - Heading: "About Freshen Interiors"
  - Paragraph: company description — design services from small remodels to new construction
  - Body text in Jost font
- [x] 2.4 **Contact Form Section** (`src/components/ContactForm.astro`)
  - Form fields:
    - Sender email input (required, type="email")
    - Message textarea (required)
    - Submit button (styled with brand colors)
  - Honeypot field: hidden input (`<input name="_gotcha" style="display:none">`) — if filled, submission is rejected
  - Timestamp check: hidden input populated with page load timestamp via JS; reject if submitted within ~2 seconds of load
  - Form `action` points to Formspree/Web3Forms endpoint
  - Success/error feedback message after submission
- [x] 2.5 **Footer** (`src/components/Footer.astro`)
  - Social media icon links (Instagram, Facebook)
  - Copyright: "© 2025 Freshen Interiors. All rights reserved."
  - Minimal styling, primary green background or accent

### Phase 3: Assemble the Page

- [x] 3.1 Update `src/pages/index.astro`
  - Use `BaseLayout` as the wrapper
  - Import and compose: Header → Hero → About → ContactForm → Footer
  - Ensure smooth vertical flow between sections

### Phase 4: SEO & Meta

- [x] 4.1 Set page `<title>`: "Freshen Interiors — Coming Soon"
- [x] 4.2 Add `<meta name="description">` with company summary
- [x] 4.3 Add Open Graph tags (`og:title`, `og:description`, `og:image`, `og:url`)
- [x] 4.4 Update favicon — use logo SVG or derive a simplified icon version

### Phase 5: Responsive Design & Polish

- [x] 5.1 Mobile layout (< 768px)
  - Stack all sections vertically
  - Ensure form inputs and buttons are full-width / tap-friendly
  - Logo and social links stack or resize appropriately
- [x] 5.2 Tablet layout (768px – 1024px)
  - Adjust spacing and font sizes for mid-range screens
- [x] 5.3 Desktop layout (> 1024px)
  - Max-width container to keep content readable
  - Generous whitespace around sections
- [ ] 5.4 Cross-browser testing (Chrome, Firefox, Safari, Edge)
- [x] 5.5 Accessibility check
  - Alt text on logo image
  - Form labels and aria attributes
  - Sufficient color contrast (primary green on cream)
  - Keyboard navigation for form and links

### Phase 6: Form Service Setup

- [ ] 6.1 Create account on Formspree (or Web3Forms) — **owner action needed**
- [ ] 6.2 Create a form endpoint linked to fresheninteriors@gmail.com — **owner action needed**
- [ ] 6.3 Add the endpoint URL to the contact form `action` attribute (replace `FORM_ID` in `src/components/ContactForm.astro`)
- [ ] 6.4 Test form submission end-to-end (confirm email delivery)
- [ ] 6.5 Verify honeypot + timestamp bot protection works

### Phase 7: Deployment

**Pre-requisites (owner action needed):**
- [ ] 7.0a Sign up for a free Vercel account at [vercel.com](https://vercel.com) (sign up with GitHub for easiest setup)
- [ ] 7.0b Push this repo to GitHub (if not already)
- [ ] 7.0c Provide the custom domain name (managed through Namecheap)

**Technical setup:**
- [x] 7.1 Install Astro Vercel adapter (`@astrojs/vercel`)
- [x] 7.2 Update `astro.config.mjs` with Vercel adapter config
- [ ] 7.3 Connect GitHub repo to Vercel project (via Vercel dashboard) — **owner action needed**
- [ ] 7.4 Configure custom domain in Vercel dashboard — **owner action needed**
- [ ] 7.5 Update DNS records in Namecheap to point to Vercel (will provide exact A/CNAME records when ready) — **owner action needed**
- [ ] 7.6 Deploy and verify live site
- [ ] 7.7 Smoke test: check all links, form, responsiveness on live URL

## Open Items

- [ ] Formspree account + form ID — owner action needed (then replace `FORM_ID` in `ContactForm.astro`)
- [ ] Custom domain name — need from owner
- [ ] Vercel account sign-up — owner action before Phase 7
- [ ] Cross-browser testing (5.4) — manual testing after deployment
