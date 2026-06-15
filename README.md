# Stellaria — FE Test

Assessment project containing two deliverables: a 300×600 animated HTML5 banner and a 600px responsive HTML email. Both are built using clean, hand-written HTML, CSS, and JS with no external frameworks or dependencies.

---

## DEMO

https://stellaria-test.vercel.app/

---

## 🚀 How to run

To test the project locally, run any static file server from the root directory:

```bash
npx serve
```

Then open:

```text
http://localhost:3000
```

in your browser to access the main launcher page (`index.html`), which links to both builds.

---

## Testing matrix

Everything below was checked in a Chromium-based preview (resized viewports + dark-mode emulation). The other browsers and email clients are built to their documented rules but weren't opened in the actual client.

### HTML5 Banner

**Chromium (Chrome/Edge)**

Verified. All 3 frames animate correctly, text counters work, and the ISI panel scrolls independently. Holds on the final frame without looping.

**Safari (WebKit) & Firefox (Gecko)**

Uses only standard properties (`transform`, `opacity`, `rAF`) and both scrollbar syntaxes (`-webkit-` + `scrollbar-width`). Not opened in Safari/Firefox directly, but nothing here is engine-specific.

**Accessibility**

Verified `prefers-reduced-motion` compliance (instantly jumps to the final frame) and correct `aria-hidden` toggles.

### HTML Email

**Modern Webmail (Gmail Web, Outlook.com)**

Inline styles, table layout, transparent PNGs. Built to spec; not tested in the actual Gmail / Outlook.com inboxes.

**Mobile (iOS Mail, Gmail App)**

Single column collapses via a `max-width` media query; checked at 375px in the preview. Not opened in the real iOS Mail / Gmail apps.

**Desktop Clients (Outlook 2016+)**

Built for it with a VML `roundrect` fallback for the CTA button, PNG images (no SVG), `bgcolor` attributes alongside CSS, a PixelsPerInch fix, and cell padding instead of CSS margins.

Recommended next step: Pass through Litmus / Email on Acid before an actual production deployment.

---

## 🛠️ Known issues & trade-offs

### Spec Discrepancies

The brief contained small contradictions between the text spec and the provided code assets (`copy.js / tokens.css`). I treated the code tokens and design comps as the source of truth (e.g., used "The only support pill..." for F1 instead of the typography scale label, fixed the capsule extension to PNG to prevent a 404, and used "Learn More" from the copy deck).

### Typography

The comps use a monospace font for specific data tags, while the spec noted "Helvetica only". I compromised by using a safe font stack (`monospace, Helvetica, Arial`) to match the design while keeping a solid fallback.

### Production Assets

Email image paths are currently relative for local testing. They must be swapped with absolute `https://` hosted URLs before production deployment.

### Banner Weight

The capsule image takes up 183 KB out of the total 204 KB banner weight. It was resampled to 460px to save ~260 KB, but could be optimized further with modern formats (WebP/AVIF) if the ad network allows it.

---

## Time spent

~3.5 hours total, split roughly as follows:

| Task                                                                                                           | Time    |
| -------------------------------------------------------------------------------------------------------------- | ------- |
| QA reconciliation (analyzing the brief, code assets, and isolating spec errors)                                | 30 mins |
| Deliverable 01 (HTML5 banner structure, CSS layout, and writing the rAF animation script)                      | 75 mins |
| Deliverable 02 (HTML email layout, nesting tables, building Outlook/VML fixes, and exporting transparent PNGs) | 60 mins |
| Final visual alignment, browser testing, and documentation                                                     | 45 mins |

---

## AI / LLM usage

This project was built with the assistance of Claude (Claude Code). The tool was utilized for:

### Asset Auditing

Cross-referencing the text spec against the raw design tokens and copy files to spot the planted QA contradictions early.

### Asset Preparation

Converting the source vector SVGs into web-safe transparent PNGs to ensure they display correctly on dark backgrounds across standard email clients.

### Review Loop

Troubleshooting alignment issues during browser testing (e.g., adjusting text wrapping on the CTA button).

All code was manually reviewed, adjusted, and visually verified against the original design comps.

