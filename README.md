# Handoff: Miku landing page

## Overview
A single-page marketing / research site for **Miku**, an experimental learning environment where a child teaches a "faithfully ignorant" AI pupil and then predicts how well it will perform on a quiz. The page introduces the product, plays a demo video, and lays out the theoretical framework, hypotheses, method and open questions. It doubles as a learning-portfolio piece, so the research voice matters as much as the visual design.

Goal of this handoff: build it as a real, deployed website on a custom domain.

## About the design files
`design/Miku Landing.dc.html` is a **design reference created in HTML**, not production code. It renders through a proprietary component runtime (`<x-dc>`, `<helmet>`, `{{ }}` holes, `support.js`) and will not run standalone. Treat it as a spec: open it to read exact copy, inline styles, and section order, then **rebuild the page in a real framework**.

Recommended target (matches the app it advertises): **Next.js (App Router) + React**, static export or Vercel deploy, plain CSS or CSS modules. No CMS needed — content is static.

`design/styles.css` is the "Modernist" design-system stylesheet the page was built against (tokens live in `:root`). The landing page **overrides the light Modernist ground with a dark walnut ground** — see Design tokens below for what is actually used.

## Fidelity
**High fidelity.** Colors, type sizes, spacing and section order are final. Reproduce them exactly. Two known gaps that need real work, not copying:

1. **Responsive**: the reference is desktop-only (`min-width: 1000px`, fixed 768×624 video frame, absolutely-positioned step list next to the video). The real site needs mobile and tablet layouts.
2. **The demo-step list** (01 Teach / 02 Build / 03 Predict / 04 Reflect & Re-teach) is currently an absolutely-positioned block at `left: 877px; top: 244px`. Rebuild it as a proper grid column beside the video frame.

## Page structure (top to bottom)

Full-width sections, each separated by a **2px rule** in `rgba(242,234,224,.22)`. Section padding is `80px 64px` unless noted. Content is flush left; nothing is centered; **no rounded corners anywhere**.

| # | Section | Layout | Ground |
| --- | --- | --- | --- |
| 1 | Header | flex, space-between; wordmark "Miku" 20px/800 + uppercase 11px label "Learning by teaching" with a 2px left rule; right: solid accent button "Get in touch" | dark |
| 2 | Hero | grid `1.35fr 1fr`, padding `88px 64px 72px`; left: H1 "Miku." 76px, 28px/800 tagline, two 17px paragraphs; right: `miku-happy.png` max 360px with a slow bob animation | **light** (`--color-accent-2-100`), dark text |
| 3 | Demo | H2 label "The demo" 13px uppercase; browser frame 768×624 (2px border, `#1A140F`): chrome bar with three 11px squares (accent, 35% ink, 20% ink) + a URL field reading `miku.app / teach / why_do_we_have_seasons`; video 762×561; four numbered steps beside it | dark |
| 4 | Why Miku | grid `1fr 1.4fr`; H2 + two paragraphs, second is a three-question list | dark |
| 5 | How learning works | grid `1fr 1.4fr`; H2 + one paragraph | dark |
| 6 | Inspired by learning by teaching | grid `1fr 1.4fr`; left H2 + `miku-thinking.png` 180px; right four paragraphs about Betty's Brain (contains the only outbound link) | **light** (`--color-accent-100`) |
| 7 | What the design borrows from | **Cornell-notes grid**: four rows of `1fr 4fr`; cue column = number + 22px/800 subtitle, separated by a **2px accent vertical rule**; notes column = 17px finding, 16px `#FFC4B8` "in Miku" line, 12px citation. Rows 01 and 03 have an accent-filled cue cell | dark |
| 8 | Learning hypotheses | H2 + lead; four rows of `78px 1.15fr 1fr` (label H1–H4 / claim 19px 800 / measure 15px with an uppercase "Measure" eyebrow), 2px rules at 14% between rows; closing caveat paragraph | `#1A140F` |
| 9 | Not another AI tutor | grid `1fr 1.4fr` head with `miku-confused.png` 120px; then two ruled blocks: the traditional flow (muted) and Miku's reversed flow (accent arrows), each a flex row with 14px gap | **light** (`--color-accent-100`) |
| 10 | Methodologies | H2 + lead; 2×2 grid of build notes (Interface / Agents / Checking the constraint / Record); closing status line | dark |
| 11 | What I am still exploring | grid `1fr 1.4fr`; numbered list of five questions, `44px 1fr` rows with 2px rules | dark |
| 12 | Why now | **accent poster**: background `#FF563C`, ink `#211A14`, padding `88px 64px`; 34px statement, 22px sub-statement at 72% ink, then a two-column 17px argument | accent |
| 13 | Finale | grid `1.25fr 1fr`, padding `88px 64px`; full-colour photo `miku-real.jpg` (do **not** grayscale it) with 12px caption; right: "One last thing" eyebrow + 30px line "Meet Miku (米酷)!" | dark |
| 14 | Footer | grid `1fr 1fr`, padding `56px 64px`; left wordmark + status line; right: outlined accent "Contact the team" button linking to the contact email | dark |

Exact copy for every section is in the HTML file — **use it verbatim**, including the citations (Chi et al., 1989; 1994 · Chase, Chin, Oppezzo & Schwartz, 2009 · Nelson & Narens, 1990 · Posner, Strike, Hewson & Gertzog, 1982).

## Design tokens

Page-level palette (overrides the Modernist light ground):

| Role | Value |
| --- | --- |
| Ground | `#211A14` |
| Deep ground (alt sections) | `#1A140F` |
| Ink | `#F2EAE0` |
| Ink 78 / 72 / 65 / 50 / 45% | `rgba(242,234,224,.78 / .72 / .65 / .5 / .45)` |
| Rule (major) | `2px solid rgba(242,234,224,.22)` |
| Rule (minor, list rows) | `2px solid rgba(242,234,224,.14)` |
| Accent | `#FF563C` |
| Accent soft (secondary note text) | `#FFC4B8` |
| Light section grounds | `var(--color-accent-100)` `#fff2ef`, `var(--color-accent-2-100)` `#fff2ef` |
| Dark text on light sections | `var(--color-neutral-700/800/900)`, headings `var(--color-accent-2-600)` `#c94b39`, H1 `var(--color-accent-800)` `#7c1405` |

Typography — **Archivo** (Google Fonts, weights 400/600/800), `-webkit-font-smoothing: antialiased`.

| Use | Size / weight |
| --- | --- |
| H1 | 76px / 800, line-height 1, letter-spacing −.03em |
| Section H2 | 44px / 800, line-height 1.05, −.025em |
| Statement (poster) | 34px / 800, 1.2 |
| Finale line | 30px / 800 |
| Tagline | 28px / 800, 1.25 |
| Flow labels, cue subtitles | 22–26px / 800, −.02em |
| Body large | 19px / 400, 1.6 |
| Body | 17px / 400, 1.65 |
| Small body | 15–16px / 1.6 |
| Eyebrow / label | 11–12px / 800, uppercase, letter-spacing .14–.16em |
| Caption, citation | 12px, ink 45% |

Spacing: 8px base. Section padding `80px 64px` (hero and poster `88px`, footer `56px`). Column gap `56px`; cue-column gap `40px`. Border radius: **0 everywhere**.

## Interactions & behavior
- **Header + footer buttons** — `mailto:` the contact address. Current value: `zoezhou0912@gmail.com`.
- **Video** — HTML5 `<video controls>`, source `assets/miku-demo.mp4`, poster frame optional. Autoplay is a flag in the design (off by default); if enabled it must be `muted` + `loop` + `playsinline`.
- **Mascot bob** — hero image, `@keyframes` translateY 0 → −10px → 0, 5s ease-in-out infinite. Respect `prefers-reduced-motion` and disable it.
- **Links** — default `#FF563C`, hover `#FFC4B8`; Betty's Brain link is underlined. Focus: `2px solid #FF563C`, offset 2px. Selection: `rgba(255,86,60,.32)`.
- **Buttons** — primary is a solid accent fill with dark ink; footer button is a 2px accent outline. Add a hover state one ramp step darker (`#dd2b0f`) and a pressed state (`#ae1800`); labels stay flush left.
- No routing, no forms, no state beyond the video element. Static page.

## Assets
All in `design/assets/`:
- `miku-happy.png` — mascot, hero + footer mark (transparent PNG)
- `miku-thinking.png` — mascot, Betty's Brain section
- `miku-confused.png` — mascot, "Not another AI tutor"
- `miku-real.jpg` — photograph of the real dog, finale section. **Full colour, never grayscale.**
- `miku-demo.mp4` — product demo video shown in the browser frame

Fonts: Archivo from Google Fonts (`@import` at the top of `styles.css`); self-host it for production.

## Deployment
- Static Next.js app on **Vercel** is the shortest path (the Miku prototype itself is speced for Vercel).
- Custom domain: add the domain in the Vercel project's Domains tab, then at the registrar point the apex `A` record / `ALIAS` and a `www` `CNAME` at the values Vercel gives. Force HTTPS and redirect `www` → apex (or the reverse, consistently).
- Add `<title>`, meta description, Open Graph image (a still from the demo or the hero mascot), favicon from `miku-happy.png`, and `lang="en"`.
- Compress `miku-demo.mp4` (H.264 + a WebM alternate) and lazy-load it; it is the heaviest asset on the page.

## Files
- `design/Miku Landing.dc.html` — the design reference (source of truth for copy and styles)
- `design/styles.css` — Modernist design-system tokens the page builds on
- `design/assets/*` — images and video listed above
