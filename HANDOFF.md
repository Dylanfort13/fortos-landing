# FortOS Landing Page — Handoff for Next Session

*Updated by Claude, 2026-04-12. Read this before touching any file.*

---

## Who is Dylan

Dylan is building **FortX Web** — an autonomous AI web agency. He is a visual, non-technical founder. He works with Claude Code as his primary dev tool. He judges work visually, fast. When something is off he'll say "still not good" — that means look harder at the reference, not just at the code.

He runs everything from **Windows 11**, uses **Cursor** as his editor, and his projects live on the Desktop.

---

## Current State — LANDING PAGE IS COMPLETE

The landing page is **done and live**. Do not make visual changes unless Dylan explicitly asks.

**Live URL:** https://dylanfort13.github.io/fortos-landing/
(Shortcut file: `Open Live Site.url` in this folder)

**GitHub repo:** https://github.com/Dylanfort13/fortos-landing
**Branch:** `main`
**Deployed via:** GitHub Pages (auto-deploys on push to main)

---

## What This Project Is

The **FortOS public landing page** — a marketing/waitlist page for the FortOS product (Dylan's autonomous web agency platform). It is a static HTML file — no framework, no build step.

**The actual platform** (Next.js 15 + Payload CMS v3) lives at:
`C:\Users\Dylan\Desktop\FortOS\platform\`

---

## File Structure

```
landing-page/
├── HANDOFF.md              ← you are here
├── index.html              ← the landing page (COMPLETE)
├── fortos-qualify.html     ← qualification form (second page after access form)
├── fortos-dashboard.html   ← project tracking dashboard
├── Open Live Site.url      ← shortcut to live GitHub Pages URL
└── assets/
    ├── image-pack-1/
    │   ├── 1.png  — steam engine  (hero)
    │   ├── 2.png  — oysters       (quote section)
    │   ├── 3.png  — dolphin       (Freelancer card)
    │   └── 4.png  — sperm whale   (Agency card)
    └── image-pack-2/
        ├── 1.png  — microscope    (Find pillar)
        ├── 2.png  — quill/inkwell (Sell pillar)
        ├── 3.png  — compass       (Build pillar)
        ├── 4.png  — telephone     (Support pillar)
        └── 5.png  — dolphin alt   (unused)
```

---

## Landing Page — Design Summary

Six sections, single HTML file, no framework.

| # | Section | Background | Notes |
|---|---------|------------|-------|
| 1 | Hero | `#010b15` navy | Steam engine flush to bottom, fade animations |
| 2 | History Is Rhyming Again | `#f1f4f7` cream | Left-aligned text in centered block |
| 3 | The 4 Pillars | `#010b15` navy | 2×2 grid, intro text above, images as-is (no invert) |
| 4 | Solo or Big Team | `#f1f4f7` cream | Dolphin left-cropped, whale full display |
| 5 | They See You. Not Us. (exclusive band) | `#010b15` navy | Narrow centered band |
| 6 | Request Your Access | `#f1f4f7` cream | 2-col: copy left, form box right |
| 7 | Carnegie Quote + Footer | `#010b15` navy | Oysters left, quote right; fortOS wordmark below |

**Fonts:** Cormorant Garamond (Google Fonts), all weights 300/400. Body and headings all serif — no sans-serif anywhere.

**Colours:**
- `--navy: #010b15`
- `--cream: #f1f4f7`
- `--body-on-light: rgba(1,11,21,0.72)`
- `--body-on-dark: rgba(241,244,247,0.70)`
- `--muted-on-light: rgba(1,11,21,0.42)`
- `--muted-on-dark: rgba(241,244,247,0.38)`

**Key CSS decisions (do not change without reason):**
- Kicker overtexts use `clamp(1.2rem, 2.2vw, 1.6rem)`, `font-weight: 400`, `margin-bottom: 1rem`
- Kicker selectors use parent+class specificity (e.g. `.pillars-intro .pillars-intro-kicker`) to beat container `p` rules — **do not simplify or this breaks**
- Dolphin: `position: absolute; height: 160px; left: -55px` inside `overflow: hidden` wrapper — tuned by pixel
- Mobile hero: `min-height: 80svh`, image pushed to bottom via `margin-top: auto`
- Scroll fade: `IntersectionObserver` on all major elements, class `.fade` / `.fade.in`
- Section rhythm: `--sec: 9rem` desktop, `6rem` mobile via `@media (max-width: 680px)`

**Two-page flow:**
1. `index.html` — landing page with email capture form
2. `fortos-qualify.html` — qualification questionnaire
- First name passes between pages via `sessionStorage` key `fortos_first`
- Qualify page back-link points to `index.html`

---

## NEXT STEP — Publishing with Proper Domain

The landing page is currently live on GitHub Pages at the default GitHub subdomain. The next step is to connect it to Dylan's real domain using the full tool stack:

### Publishing pipeline to complete:

1. **GitHub → already done** — repo is at `github.com/Dylanfort13/fortos-landing`, main branch auto-deploys to GitHub Pages

2. **Vercel** — Connect the GitHub repo to a Vercel project for production-grade hosting (CDN, HTTPS, preview deploys). Steps:
   - Create new Vercel project → import from GitHub → select `Dylanfort13/fortos-landing`
   - Framework preset: **Other** (static HTML, no build command)
   - Output directory: `/` (root)
   - Deploy

3. **Cloudflare** — Point the domain DNS to Vercel. Steps:
   - Add custom domain in Vercel project settings
   - In Cloudflare DNS: add CNAME record pointing to Vercel's provided hostname
   - Set SSL/TLS to "Full" in Cloudflare
   - Vercel handles the SSL cert automatically

4. **Test** — Confirm live at the real domain, both `index.html` and `fortos-qualify.html` load correctly

### Reference files for the tool stack:
- Stack map: `C:\Users\Dylan\Documents\FortX web\Tool html AI\stack-map.html`
- Project dashboard: `fortos-dashboard.html` (in this folder)

---

## Design Reference (if visual changes ever needed)

PDF slices at: `C:\Users\Dylan\Desktop\FortOS\site landing asset\slice_1.png` through `slice_6.png`

Design spec for **dashboard/app UI** (NOT the landing page):
`C:\Users\Dylan\Documents\FortX web\Tool html AI\fortx\FORTX COMMAND CENTER — Design Spec Addendum.md.txt`

---

## The Broader FortOS Platform

Located at: `C:\Users\Dylan\Desktop\FortOS\platform\`

- Next.js 15 + Payload CMS v3
- `npm run dev` → `http://localhost:3000`
- Admin at `http://localhost:3000/admin`
- SQLite in demo mode (no external services for local)
- Production needs: Neon DB, Resend, Cloudflare API token, Hetzner VPS or Vercel

Docs inside the platform folder:
- `NEEDS_FROM_DYLAN.md` — production deployment checklist
- `DEMO_SETUP.md` — local demo setup guide
- `ARCHITECTURE.md` — system architecture

---

## Working With Dylan

- He is visual. Show don't tell.
- He moves fast. Don't over-explain.
- He delegates judgment: "add anything you judge useful" means you have latitude.
- When he says "not good" it means visually off, not broken.
- He uses `! <command>` to run shell commands in chat.
- His preferred stack: Claude Code (AI dev) + Cursor (review) + GitHub + Vercel + Cloudflare.

---

*Last updated: 2026-04-12 by Claude (claude-sonnet-4-6)*
