# Handoff: R&D + Ops Offsite Site

## Overview
A single-page marketing/utility site for TaxDome's R&D + Ops offsite (Cancún, Sep 20–26, 2026). Covers home (countdown/narrative removed per latest edits — see below), agenda, logistics, before-arrival prep, and a post-event photo recap. Built on the TaxDome ("Revenue 2025" / DesignSystem_0f8837) design system, with an original "dev / product / ops → merge" line-diagram motif tying the "one team, one model" narrative to a git-branch metaphor — chosen deliberately for a developer/designer audience.

## About the design files
The files in `reference/` are **design references** built as an HTML prototype in this product's own "Design Component" runtime (`support.js`, `image-slot.js`). They are **not production code to copy as-is** — `support.js` depends on this platform's internal runtime and will not work standalone in a plain static site or Next.js app. Treat `reference/RD Ops Offsite.dc.html` purely as the source of truth for markup structure, copy, layout, and inline styles, and **recreate the design in a real framework** — Next.js (App Router) deployed on Vercel is the natural fit given the stated GitHub/Vercel workflow. Use static export or plain React state for the tab navigation (no server logic needed).

## Fidelity
**High-fidelity.** All copy, layout, spacing, and colors below are final. Two things are intentionally NOT final:
- Two photos are placeholders (`<image-slot>` elements) — see **Assets**.
- The "Location" section on Home uses Sep 20–26, 2026 / Cancún / AVA Resort Cancun, which does not match the Agenda page's Nov 15–20 dates — this inconsistency exists in the current design and should be resolved with the client before/during build (probably the agenda dates are stale and should move to Sep 20–26).

## Global layout
- Sticky top nav, white bg, `1px solid #DCE2F9` bottom border, `16px` vertical / `clamp(20px,5vw,64px)` horizontal padding.
- Nav left: small inline SVG mark — three curved lines (dev/product/ops) converging into one point with a yellow dot — plus wordmark "One team, one model" (sentence case), 18px/600.
- Nav center: pill tab group, `#F5F8FF` track, `12px` radius, `4px` padding; active tab = white bg + `0 1px 3px rgba(70,70,83,0.15)` shadow; tabs: Home, Agenda, Logistics, Before arrival, Recap.
- Footer: `1px solid #DCE2F9` top border, `32px` padding, `13px` `#767689` text, flex space-between: "R&D + Ops Offsite · November 15–20" / "One team, one model."
- Body font: `'Suisse Intl', sans-serif`. A `.mono` utility (`ui-monospace, SFMono-Regular, Menlo, monospace`) is used throughout for eyebrows, indices, and data-like labels (dev/product/ops branch labels, countdown units, numbered pillars/facts) — a deliberate technical accent for the dev/design audience.

## Screens

### 1. Home
- **Hero** — navy (`#000724`) full-bleed section, white text, `clamp(56px,10vw,140px)` top padding / `clamp(96px,14vw,180px)` bottom (extra bottom space for the overlap below). Two-column grid: text column (max 640px) + a static inline SVG diagram column (max 380px).
  - Eyebrow (`#FFCB0D`, 13px/600, uppercase, 1.4px tracking): "R&D + Ops Offsite · November 15–20"
  - H1 (clamp 40–72px/600, -0.02em): "One team.<br/>One model."
  - Sub (clamp 17–20px, `#C7CEEF`, max 560px): "A week for R&D and Ops to build around a single operating model — how we plan, ship, and support the business together."
  - Two buttons (DS `Button`): "View agenda" (primary) → Agenda tab; "Logistics" (secondary) → Logistics tab.
  - Countdown row: monospace, bordered pill group (`1px solid rgba(255,255,255,0.16)`, `10px` radius), 4 cells (Days/Hours/Min/Sec) divided by `1px` internal borders, live-updating every second from a `2026-11-15T09:00:00` target (see note above on date mismatch).
  - Decorative SVG (380×260 viewBox): three curved paths (dev top, product middle straight, ops bottom) in brand blue (`#3D63F7`, full/70%/50% opacity) converging at (260,130), continuing as a single yellow (`#FFCB0D`) line to the right edge — labeled `dev/`, `product/`, `ops/` and `merge` in 11px monospace. Small circles mark each branch start (navy fill, `#8EB8FF` stroke) and the merge point (solid yellow).
  - A soft radial brand-blue glow (`280px` circle, 35% opacity) sits top-right of the hero.
- **Operating model section** — white, rendered as a rounded "sheet" that overlaps the hero: `border-radius: 32px 32px 0 0`, `margin-top: -40px`, `box-shadow: 0 -16px 40px rgba(0,7,36,0.10)`, `z-index: 2`. Two-column grid (text + a 2×2 divided card grid).
  - Eyebrow "Why we're here" (`#2851F5`), H2 "Dev and Product, finally in step.", two body paragraphs (`#50505E`, 17px/1.6).
  - Pillars grid: 4 cards in a single bordered grid with `1px` `#DCE2F9` hairlines between cells (no individual card borders/shadows) — each cell: monospace 2-digit index (`01`–`04`, `#8EB8FF`), title (16px/600), body (14px/`#767689`). Content: "Shared roadmap", "Shared metrics", "Shared rituals", "Shared ownership" (see file for full body copy).
- **Location section** — white, max-width 1280px, two-column grid (text + `<image-slot>` photo, 4:3, 20px radius).
  - Eyebrow "Logistics", H2 "Cancún, Mexico", body copy, a 2×2 fact grid (monospace 2-digit index + label: dates / hotel name / "Group flights & transfers" / "28°C avg · pack light"), and two buttons ("Travel info" → Logistics, "Before arrival" → Before arrival tab).
- **Pre-work section** — `#F5F8FF` bg, H2 "Pre-work", 3-card auto-fit grid (white cards, `#DCE2F9` border, 16px radius): DS `Badge` (tone "accent") + title + body + a text link. Items: "Operating model survey", "Current-state one-pager", "Pick your breakout track".

### 2. Agenda
Max-width 1000px. Eyebrow "Nov 15–20", H1 "Agenda", intro paragraph. Six day groups (Sat Nov 15 → Thu Nov 20), each with a label/date header (bottom-bordered) and a vertical list of session rows: `96px` time column (monospace-style tabular figures) / title+detail / DS `Badge` (tone "accent" for joint "R&D + Ops" sessions, "neutral" for open sessions). Full session list is in the file.

### 3. Logistics
Max-width 760px, single-column article layout (not cards). Sections in order, each with a `17px/600` H3:
1. **Flights & airport transfers** — 2 paragraphs, a monospace arrival/departure date line (`#2851F5`), 1 paragraph.
2. **Hotel & check-in** — `<image-slot>` (16:9, 16px radius) captioned "AVA Resort Cancun — tower and main pool", hotel name (16px/600), intro paragraph, then a dash-bulleted list (6 items: check-in time, pre-check-in app, meal coverage, snack bar/café, towels, check-out time), closing note on rooming assignments.
3. **Travel insurance** — 2 paragraphs.
4. **Meals & dietary preferences** — 2 paragraphs.
5. **Dress code** — 2×2 label/value grid (monospace uppercase labels: Daytime/Activities/Evenings/Nights) + a closing note about the Welcome Dinner.
6. **What to pack** — two labeled groups ("Essentials", "Optional but recommended"), each a dash-bulleted list.
7. A `#F5F8FF` callout card: "Please do not bring" + inline list.
8. **Contacts** — top-bordered, 2-column: "Travel coordinators" / "Offsite coordinators", each with a sub-label and a list of names ("— Slack").

Dash bullets throughout use a monospace em-dash (`—`) in `#8EB8FF` in a `20px` fixed column, not list markup — replicate as a two-column grid per row, not `<ul>`, to match spacing exactly.

### 4. Before arrival
Max-width 760px, single column. Eyebrow "Before arrival", H1 "Get ready with this checklist", intro paragraph. One bordered action card (16px radius): monospace uppercase label "One quick action item", title "Join the group chat", subtext, DS `Badge` (tone "warning") reading "Soon" pinned right. Then eyebrow "Preparation guide", H2 "How to prepare yourself for offsites", and four H3 subsections — "Why we host offsites" (paragraph), "How to get the most out of it" (5 dash-bulleted tips), "A quick note on conduct" (intro paragraph + 5 dash-bulleted rules), "Travel & expenses — the practical stuff" (paragraph + a "Travel & expense policy →" link) — the last one top-bordered. Full copy is in the file.

### 5. Recap
Max-width 900px, centered, placeholder state: eyebrow "Coming November 20", H1 "Photo recap", body copy, and a dashed-border (`#DCE2F9`) empty-state box reading "Photos will appear here". Intentionally empty until after the event.

## Interactions & behavior
- Tab navigation is pure client state (`page` string) — no routing needed, but recreate as real routes/pages in Next.js (`/`, `/agenda`, `/logistics`, `/before-arrival`, `/recap`) for shareable URLs.
- Countdown re-renders every 1000ms from a fixed target date.
- No other animation — motion was deliberately removed from an earlier draft (hexagons/spinning marks) per design feedback; keep the current design fully static aside from the countdown ticking and standard button/link hover states (DS `Button` handles its own hover; links underline on hover, `#2851F5` → `#1433E1`).

## Design tokens
Pull full tokens from `reference/design-system/colors_and_type.css`; the ones actually used in this design:
- **Colors**: navy `#000724` (primary text/hero bg), blue `#2851F5` (brand/links/CTA), blue-light `#3D63F7` (diagram lines), yellow `#FFCB0D` (single accent — eyebrow on navy, merge point/line), secondary text `#50505E`, tertiary text `#767689`, placeholder-ish `#9AA6D9`/`#C7CEEF` (on-navy secondary text), borders `#DCE2F9` (default) / `#8EB8FF` (accent/mono labels), surface tints `#F5F8FF` / `#EEF1FC`.
- **Type**: Suisse Intl (body/headings, weight 600 for headings), system monospace stack for the `.mono` accent class. Headline sizes use `clamp()` for responsive scaling; letter-spacing -0.02em to -0.015em on headings, 1.4px uppercase tracking on eyebrows.
- **Radius**: 8px (small icon/index boxes), 12px (nav pill track), 16px (cards), 20px (photo slots, callouts), 32px (hero/section overlap sheet).
- **Components**: DS `Button` (variants `primary`/`secondary`), DS `Badge` (tones `accent`, `warning`).

## Assets
Two `<image-slot>` placeholders need real photos dropped in before launch:
- `location-photo` (Home → Location section, 4:3) — resort/venue establishing shot.
- `hotel-photo` (Logistics → Hotel & check-in, 16:9) — captioned "AVA Resort Cancun — tower and main pool".

No other imagery; all icons/marks are inline SVG (see hero and nav diagrams above).

## Files
- `reference/RD Ops Offsite.dc.html` — full source (markup + logic + all copy/data arrays). This is the canonical reference for exact text and structure.
- `reference/support.js`, `reference/image-slot.js` — this platform's runtime; not portable, included only so the reference file can be opened for visual inspection if needed.
- `reference/design-system/` — the TaxDome design tokens (`colors_and_type.css`, `styles.css`) and component bundle (`_ds_bundle.js`) this design was built against, plus font files. Use the CSS files directly for token values; the JS bundle's components (`Button`, `Badge`) should be reimplemented (or swapped for the codebase's existing equivalents) rather than imported as-is.
