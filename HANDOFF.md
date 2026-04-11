# FortOS Landing Page — Handoff for Next Session

*Written by Claude, 2026-04-11. Read this before touching any file.*

---

## Who is Dylan

Dylan is building **FortX Web** — an autonomous AI web agency. He is a visual, non-technical founder. He works with Claude Code as his primary dev tool. He judges work visually, fast. When something is off he'll say "still not good" — that means look harder at the reference, not just at the code.

He runs everything from **Windows 11**, uses **Cursor** as his editor, and his projects live on the Desktop.

---

## What This Project Is

We are building the **FortOS public landing page** — a marketing/waitlist page for the FortOS product, which is Dylan's autonomous web agency platform (Next.js + Payload CMS, already built, lives at `C:\Users\Dylan\Desktop\FortOS\platform\`).

**This landing page is separate from the platform.** It's a static HTML file — no framework, no build step. Just open in browser.

**Goal after the landing page:** Publish it live using the full tool stack (GitHub → Vercel → Cloudflare domain). This is a test run of the publishing pipeline before doing it for real client sites.

---

## The Design Reference — READ THIS CAREFULLY

Dylan built the design in Canva. The PDF is at:
`C:\Users\Dylan\Desktop\FortOS\landing-page\site.pdf` (he may have moved it here)

**I rendered the PDF into slices** so you can see it without running pdftoppm. They are at:
`C:\Users\Dylan\Desktop\FortOS\site landing asset\slice_1.png` through `slice_6.png`

Or install PyMuPDF and re-render:
```python
pip install pymupdf pillow
python -c "
import fitz
from PIL import Image
doc = fitz.open('path/to/site.pdf')
page = doc[0]
pix = page.get_pixmap(dpi=120)
pix.save('page_1.png')
"
```

### Exact section breakdown (from the PDF slices):

**Section 1 — Hero (dark navy `#020c1a`)**
- `fortOS` small centered at very top (acts as logo)
- Large serif heading centered: **"The Engine That Runs Your Agency While You Sleep"**
- Smaller italic body: "Plug in your brand. Our AI agents find the leads, close the deals, build the sites, and handle the support."
- Steam engine illustration (`assets/image-pack-1/1.png`) centered below the text, shown at natural opacity on dark background (NOT inverted — the faint light tones work as-is on dark navy)
- No email form in the hero in the PDF — but add one below the image for the actual web version

**Section 2 — History Is Rhyming Again (light cream `#eff1f4`)**
- Italic small text at top: "A pattern repeating itself"
- Very large serif heading left-aligned: **"History Is Rhyming Again"**
- Body paragraphs, left-aligned, generous line spacing
- "years behind" is underlined in the PDF
- Three paragraphs total
- Lots of whitespace — this section breathes

**Section 3 — The 4 Pillars (dark navy)**
- "The 4 pillars" centered in large serif
- Horizontal rule beneath it
- 2×2 grid layout
- Each cell: illustration (inverted — white line art on dark) + pillar name heading + short description
- Image assignment from the PDF:
  - **Find**: microscope (`assets/image-pack-2/1.png`) — inverted
  - **Sell**: quill + inkwell (`assets/image-pack-2/2.png`) — inverted
  - **Build**: compass/drafting tools (`assets/image-pack-2/3.png`) — this image appeared mostly white to me but renders fine when inverted on dark bg
  - **Support**: candlestick telephone (`assets/image-pack-2/4.png`) — inverted

**Section 4 — Solo or big team (light cream)**
- Centered heading: **"Solo or big team"**
- Centered italic sub: "It does not matter."
- Centered body paragraphs
- Then 2-col grid left-aligned:
  - Left: dolphin (`assets/image-pack-1/3.png`) → **Freelancer** heading + body — natural grayscale (no filter) on light bg
  - Right: sperm whale (`assets/image-pack-1/4.png`) → **Agency** heading + body — natural grayscale

**Section 5 — Request Your Access (light cream)**
- 2-col layout:
  - Left: italic small "Some revolutions have a guest list…" + big heading **"Request Your Access"** + body paragraphs
  - Right: a bordered rectangle (navy border) = the form. Just email input + submit button inside.
- Below the form box, centered italic: "This is not a waitlist. It is a selection."

**Section 6 — Quote + Footer (pure black `#000000`)**
- Oysters illustration (`assets/image-pack-1/2.png`) on the LEFT — natural grayscale on black (beautiful contrast)
- Quote text on the RIGHT: *"The first man gets the oyster, the second man gets the shell."* — italic
- Attribution: `-Andrew Carnegie`
- Then below that (same black bg), just the `fortOS` logo centered in large serif, no other text

---

## Fonts

The PDF uses a **classic editorial serif** throughout — both headings and body. It looks like **Georgia** or something very close. The `fortOS` wordmark has a distinctive lowercase 'f' with a tail below baseline — this is characteristic of **Cormorant Garamond** (the 'f' has an extended descender in italic) or possibly Playfair Display.

Current implementation uses `Cormorant Garamond` from Google Fonts — this is close. If it still doesn't look right, try:
- `'Playfair Display', Georgia, serif`
- Or just `Georgia, 'Times New Roman', serif` (no Google Fonts dependency)

The body copy in the PDF uses the **same serif** at a smaller size/lighter weight — not a different sans-serif font. Everything is serif.

---

## Colours — EXACT VALUES (confirmed by Dylan)

| Token | Hex | Used for |
|-------|-----|----------|
| Dark | `#010b15` | Hero bg, Pillars bg, text on light sections |
| Light | `#f1f4f7` | History bg, Solo bg, Access bg, text on dark sections |
| Black | `#000000` | Quote + Footer bg |
| Body on light | `rgba(1,11,21,0.72)` | Body copy on `#f1f4f7` sections |
| Muted on light | `rgba(1,11,21,0.42)` | Kicker text, captions on light |
| Body on dark | `rgba(241,244,247,0.70)` | Body copy on `#010b15` sections |
| Muted on dark | `rgba(241,244,247,0.38)` | Captions on dark |

**Rule:** `#f1f4f7` = light colour = backgrounds on light sections AND text/illustrations on dark sections. `#010b15` = dark colour = backgrounds on dark sections AND text on light sections. Never mix them up.

---

## Image Assets

All images are vintage naturalist/scientific engravings (black on white).

```
assets/
├── image-pack-1/
│   ├── 1.png  — faint steam engine (industrial machinery) — hero image
│   ├── 2.png  — oysters illustration — Carnegie quote section
│   ├── 3.png  — dolphin — Freelancer card
│   └── 4.png  — sperm whale — Agency card
└── image-pack-2/
    ├── 1.png  — faint microscope — Find pillar
    ├── 2.png  — quill + inkwell — Sell pillar
    ├── 3.png  — compass/drafting tools — Build pillar (image appears very faint/light)
    ├── 4.png  — faint candlestick telephone — Support pillar
    └── 5.png  — dolphin (squarer frame, same animal as pack1/3)
```

**Image treatment rules:**
- On **dark navy** (pillars section): `filter: invert(1)` — turns black-on-white to white-on-dark. Shows as white line art.
- On **light cream** (solo/big team section): No filter. Natural grayscale. The white bg of the image blends into the cream page.
- On **pure black** (quote section): No filter. The white bg of the image reads as contrast against black.
- Hero steam engine: No filter, `opacity: 0.7` — the faint light tones sit naturally on dark navy.

---

## Current State of the Landing Page

File: `fortos-landing.html` in this folder.

**What's built:**
- All 6 sections with correct content
- Correct alternating dark/light/black backgrounds
- All images in place with correct treatments
- Mobile responsive
- Email form with validation
- Sticky nav (transparent → blurs on scroll)

**What Dylan said was still wrong** ("it's better but still not good"):
The design is structurally correct but likely has issues with:
1. **Typography sizing/weight** — headings may be too large or too bold compared to the PDF's restrained, quiet serif style. In the PDF the headings feel like printed editorial text, not web-hero text. Scale them back.
2. **Spacing** — The PDF has extreme whitespace, especially in the History and Solo sections. The sections feel like pages in a book, not web sections.
3. **The hero image** — In the PDF the steam engine sits quite close below the subtitle, fairly large (fills most of the width). The overall hero has less top/bottom padding than a typical "full viewport" hero.
4. **Font rendering** — The PDF was made in Canva with system fonts. Cormorant Garamond is close but may look different on screen. Consider testing with just `Georgia` to see if it looks more like the PDF.
5. **The form box** — In the PDF the form box is just an empty rectangle with thick border — minimal. No padding gymnastics.
6. **The pillars** — The images in the PDF are noticeably white/bright on dark. If pack2/3 (Build) is invisible, try a different icon or use a CSS-drawn icon.

**Recommended next step:**
Open the PDF slices (`slice_1.png` through `slice_6.png`) side by side with the browser. Go section by section. The gap between PDF and browser is likely in font sizing, whitespace scale, and image sizing.

---

## File Structure (this folder)

```
landing-page/
├── HANDOFF.md              ← you are here
├── fortos-landing.html     ← the landing page (work in progress)
├── fortos-dashboard.html   ← project tracking dashboard
└── assets/
    ├── image-pack-1/       ← Dylan moving these here
    │   ├── 1.png
    │   ├── 2.png
    │   ├── 3.png
    │   └── 4.png
    └── image-pack-2/       ← Dylan moving these here
        ├── 1.png
        ├── 2.png
        ├── 3.png
        ├── 4.png
        └── 5.png
```

---

## The Publishing Pipeline (after landing page is done)

The goal is to publish this page using the full stack. Steps:

1. `git init` in this folder (or the FortOS folder)
2. Create GitHub repo → push
3. Connect Vercel project to GitHub repo
4. Vercel auto-deploys on every push
5. Connect Cloudflare domain → point DNS to Vercel

The **stack-map** explaining this pipeline is at:
`C:\Users\Dylan\Documents\FortX web\Tool html AI\stack-map.html`

The **project dashboard** tracking all this is:
`fortos-dashboard.html` (in this folder) — open in browser, all state saves to localStorage.

**For this static HTML page:** Vercel can serve it as a static site. No Next.js, no database needed. Just the HTML file + assets folder → push → live.

---

## The Broader FortOS Platform

The actual product Dylan is building is the **FortX autonomous web agency platform**, located at:
`C:\Users\Dylan\Desktop\FortOS\platform\`

- Next.js 15 + Payload CMS v3
- Already built and runnable locally (SQLite demo mode)
- `npm run dev` → opens at `http://localhost:3000`
- Admin at `http://localhost:3000/admin`
- No external services needed for local demo
- For production needs: Neon DB, Resend (email), Cloudflare API token, Hetzner VPS or Vercel

Docs inside the FortOS folder:
- `NEEDS_FROM_DYLAN.md` — production deployment checklist
- `DEMO_SETUP.md` — local demo setup guide
- `ARCHITECTURE.md` — system architecture

---

## Webdesign Skills Files — Where They Are & Which to Use

Dylan has prepared design specification files that act as a reference library for Claude. They live at:

```
C:\Users\Dylan\Documents\FortX web\Tool html AI\fortx\
├── FORTX COMMAND CENTER — Design Spec Addendum.md.txt
└── FORTX COMMAND CENTER — Build Blueprint.md.txt
```

### What each file contains

**Design Spec Addendum** — A full CSS design system for **premium dark SaaS UI**: glassmorphic cards, ambient lighting, status dots, pill badges, buttons, table styles, metric cards, toast notifications, scrollbar, form inputs. It defines the FortX brand visual language for *app/dashboard UIs* (dark bg, FortX orange accent `#f0763c`, Inter font, layered depth).

**Build Blueprint** — Architecture + feature spec for the FortX Command Center (a local ops dashboard that connects GitHub, Vercel, Cloudflare, Neon via API). Not directly relevant to the landing page.

### Which file applies to this project

**For the landing page: NEITHER.** The landing page has its own design from the Canva PDF — it's editorial/print-inspired (cream/navy, vintage engravings, serif type) not a SaaS dashboard.

**When to use the Design Spec Addendum:** Any time you're building a UI component that is part of the FortX Command Center dashboard, the FortOS admin/portal, or any internal tool for Dylan. That file IS the design system for anything dashboard-like. Read it before writing a single line of CSS for those projects.

**For the landing page specifically:** Follow the PDF slices (`slice_1.png` → `slice_6.png`) and the design notes in this HANDOFF. The only colours are `#010b15`, `#f1f4f7`, `#000000`. The only font is a classical serif (Cormorant Garamond or Georgia). No orange, no glass, no dark SaaS.

---

## Working With Dylan

- He is visual. Show don't tell. When in doubt, open the PDF reference.
- He moves fast. Don't over-explain.
- He delegates judgment: "add anything you judge useful" means you have latitude.
- When he says "not good" it means visually off, not broken. Look at the reference again.
- He uses `! <command>` to run shell commands in chat.
- His preferred stack: Claude Code (AI dev) + Cursor (review) + the tool stack above.

---

*Last updated: 2026-04-11 by Claude (claude-sonnet-4-6)*
