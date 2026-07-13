SPEC.md — Architectural Firm Portfolio
1. Concept & Vision
HAUS — a Zurich-based architectural studio whose digital presence embodies the same discipline as their buildings: nothing arbitrary, every element earning its place. The site feels like walking through a perfectly proportioned space — quiet confidence, material honesty, structural clarity. Not a portfolio that shouts; one that commands attention through restraint.

The experience: deliberate pacing, rigorous grid, generous nothingness between elements. Scroll like turning pages of a Swiss design annual.

2. Design Language
Aesthetic Direction
Swiss International Typographic Style × Bauhaus Objectivism — strict grid adherence, asymmetric layouts anchored to mathematical proportions, typography as structure not decoration. Inspired by Müller-Brockmann's poster work and Bauhaus workshop aesthetics.

Color Palette
Role	Name	Hex
Background	Chalk White	#F7F6F3
Surface	Stone Grey	#E8E6E1
Text Primary	Charcoal	#1C1C1C
Text Secondary	Graphite	#6B6B6B
Accent	Warm Wood	#B8976A
Accent Deep	Walnut	#7A5C3A
Divider	Ash	#D4D2CC
Inverted BG	Near Black	#141414
Typography
Primary: 'Neue Haas Grotesk Display Pro' → fallback 'Helvetica Neue', Helvetica, Arial, sans-serif
Secondary / Body: 'Inter' (variable weight, clean and precise)
Mono / Labels: 'JetBrains Mono' for project codes and technical labels
Scale: 12px base → 14 / 16 / 20 / 28 / 40 / 56 / 80 / 120px
Tracking: Display text at -0.03em to -0.05em; labels at +0.12em uppercase
Line height: Body 1.6, Display 1.05–1.1
Spatial System
Grid: 12-column, 24px gutter, max-width 1440px, 80px horizontal padding (desktop)
Vertical rhythm: 8px base unit — all spacing is multiples (8, 16, 24, 32, 48, 64, 80, 96, 128px)
Section breathing: 160px vertical padding on hero; 120px on content sections
Negative space: Sections intentionally leave >40% of viewport empty
Motion Philosophy
Entrance: Fade + slight upward translate (24px), 600ms ease-out, staggered 80ms between siblings
Scroll-triggered: IntersectionObserver at 15% threshold — elements reveal as user scrolls
Hover: Subtle scale (1.0 → 1.02) on project cards, 300ms ease; wood accent color bleeds on borders
Hero slider: Smooth horizontal scroll with momentum, snap to slide, no jarring cuts
Page load: Hero fades in with 1.2s delay after DOMContentLoaded — cinematic arrival
No bounce, no overshoot — all easing uses cubic-bezier(0.25, 0.1, 0.25, 1) or custom equivalents
Visual Assets
Icons: Custom inline SVGs — architectural line-weight (1.5px stroke), minimal geometric forms
Images/Videos: Unsplash architectural photography + Pexels interior videos (cinematic 16:9 or wider)
Decorative: Thin 1px rule lines as section dividers; grid overlay option for hero (CSS)
Favicon: Minimal geometric SVG — "H" letterform in charcoal on white
3. Layout & Structure
Page Architecture
text

Copy
[HEADER] — Fixed, minimal: Logo left + nav right, becomes translucent on scroll

[HERO] — Full viewport width, 100vh height

         Horizontal slider — 5 slides, each full-height video/image with text overlay

         Slide indicators: thin vertical progress line + dot markers

         Hero text: studio name, year established, one-line manifesto

[MANIFESTO] — Large-scale typography, asymmetric grid, one powerful statement

[SELECTED WORKS] — 2-column project grid, Swiss-aligned, hover reveals project info

[BY THE NUMBERS] — Horizontal stat strip: projects, countries, years, awards

[PHILOSOPHY] — Text-heavy editorial section, 3-column reading layout

[TEAM] — Minimal portraits with name + role, generous spacing

[CONTACT] — Split: large text left, form right; wood accent on CTA button

[FOOTER] — Minimal: copyright, social links as icon row, back-to-top
Visual Pacing
Hero (loud/expansive) → Manifesto (quiet/typographic) → Works (visual feast) → Stats (pause) → Philosophy (contemplative) → Team (human) → Contact (action)
Every section shift has 1px rule line or color inversion as breath marker
Responsive Strategy
Desktop (1200px+): Full 12-column Swiss grid, horizontal hero slider
Tablet (768–1199px): 8-column grid, hero remains horizontal but with swipe support
Mobile (<768px): Single column, hero becomes full-screen stacked slides (not horizontal)
4. Features & Interactions
Header
Logo: "HAUS" wordmark, tracked uppercase, left-aligned
Nav: WORK · STUDIO · CONTACT — right-aligned, 14px, 0.08em tracking
On scroll past 80px: background transitions from transparent to rgba(247,246,243,0.92) with backdrop-filter: blur(12px)
Active section highlighted via scroll spy
Mobile: hamburger → full-screen overlay nav
Hero Horizontal Slider
5 full-height slides, each ~100vw wide
Background: cinematic interior video (autoplay, muted, loop) or high-res architectural image
Each slide: project title (large, bottom-left), project type + location (small, bottom-right)
Slide transition: crossfade 800ms ease
Navigation: scroll-hijack — mouse wheel vertical scroll translates to horizontal slide movement
Progress indicator: thin vertical line on right edge, fills as user scrolls through slides
Auto-advance: every 6 seconds with pause on hover
Scroll Reveal
All sections use IntersectionObserver (threshold: 0.15, rootMargin: '0px 0px -50px 0px')
Elements with .reveal class: opacity 0 → 1, translateY 24px → 0, 600ms ease-out
Stagger: data-delay="0", data-delay="1" etc. on children — each increments 80ms
Images: scale from 1.05 → 1.0 simultaneously with opacity (cinematic zoom-in effect)
Project Cards
On hover: thin wood-colored border appears (border-color transition 300ms), subtle scale 1.02
Image zooms slightly (scale 1.0 → 1.06, 500ms)
Project name and category fade in over the image with dark gradient overlay
Click → smooth scroll to project detail (future expansion)
Navigation Links
Underline animation: pseudo-element line grows from left on hover (width 0 → 100%, 250ms)
Current section: underline always visible
Contact Form
Fields: Name, Email, Project Type (select), Message
Validation: real-time on blur, error state with red border + helper text
Submit: button text changes to "Sending…" with spinner, then "Message Sent ✓"
Error: shake animation on form container
Back to Top
Appears after scrolling 600px
Fixed bottom-right, 48px circular button, wood accent background
Scrolls to top with smooth behavior, 400ms
5. Component Inventory
Header
Default: transparent bg, charcoal text
Scrolled: frosted glass bg, same text
Mobile open: full-screen overlay, centered large nav links
Hero Slide
Loading: solid #E8E6E1 placeholder until video loads
Active: video playing, text visible with gradient overlay at bottom
Inactive: paused, text at reduced opacity
Project Card
Default: image fills, no overlay text visible
Hover: wood border, image scale, overlay text visible
Focus: wood border visible (keyboard nav)
Stat Item
Default: number in large display font, label in small caps
Reveal: number counts up from 0 on scroll into view (1000ms, ease-out)
Section Label
Small all-caps text with 0.12em tracking, graphite color, left or right aligned
Followed by 1px rule line extending to grid edge
CTA Button
Default: wood accent background, chalk white text, no border-radius (Bauhaus: square corners)
Hover: walnut background, slight translateY(-2px)
Active: translateY(0), darker background
Disabled: 50% opacity, no hover effect
Form Input
Default: 1px ash border-bottom only, no border-radius
Focus: border-bottom becomes charcoal, label floats up
Error: border-bottom becomes muted red, helper text appears below
Filled: label stays floated, border stays charcoal
6. Technical Approach
Stack
Single HTML file with embedded CSS and vanilla JavaScript
No framework — pure HTML/CSS/JS for maximum performance and Awwwards credibility
Google Fonts: Inter, JetBrains Mono (Neue Haas via system Helvetica as primary)
CSS Architecture
CSS custom properties for all design tokens
Mobile-first media queries, progressive enhancement
CSS Grid for layout, Flexbox for alignment
scroll-behavior: smooth on html
Custom scrollbar: 4px wide, ash track, charcoal thumb
::selection: wood accent background, white text
JavaScript
IntersectionObserver for all scroll reveal animations
Horizontal scroll conversion for hero (wheel event → horizontal translate)
Video autoplay management (play/pause based on visibility)
Scroll spy for active nav highlighting
Mobile detection → disables wheel-hijack horizontal scroll
Smooth scroll polyfill not needed (modern browsers)
Performance
Videos: preload="metadata", playsinline, muted, loop attributes
Images: loading="lazy" on below-fold images
Fonts: font-display: swap
Critical CSS inlined in <head>, non-critical deferred
Accessibility
All images have descriptive alt text
Video has aria-label describing content
Form labels properly associated
Keyboard navigation for all interactive elements
Reduced motion: @media (prefers-reduced-motion: reduce) disables animations
Color contrast: all text meets WCAG AA (4.5:1 for body, 3:1 for large text)
