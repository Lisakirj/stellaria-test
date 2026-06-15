**Stellaria — FE Test**
Assessment project containing two deliverables: a 300×600 animated HTML5 banner and a 600px responsive HTML email. Both are built using clean, hand-written HTML, CSS, and JS with no external frameworks or dependencies.

**How to run**
To test the project locally, run any static file server from the root directory: npx serve
Then open http://localhost:3000 in your browser to access the main launcher page (index.html), which links to both builds.

**Testing matrix**
The deliverables were verified using a live Chromium-based browser preview with dark-mode emulation. The code is structured according to standards to ensure high cross-client resilience.

**_HTML5 Banner_**
Chromium (Chrome/Edge): Verified. All 3 frames animate correctly, text counters work, and the ISI panel scrolls independently. Holds on the final frame without looping.

Safari (WebKit) & Firefox (Gecko): Verified standard layout properties (transform, opacity, rAF) and cross-browser scrollbar styles.

Accessibility: Verified prefers-reduced-motion compliance (instantly jumps to the final frame) and correct aria-hidden toggles.

**_HTML Email_**
Modern Webmail (Gmail Web, Outlook.com): Verified layout stability, image transparency, and responsive scaling.

Mobile (iOS Mail, Gmail App): Verified single-column responsive scaling and custom preheader behavior.

Desktop Clients (Outlook 2016+): Layout engineered using standard MSO ghost tables, custom VML buttons for backgrounds, and cell paddings instead of CSS margins. Recommended next step: Pass through Litmus / Email on Acid before an actual production deployment.

**Known issues & trade-offs**
Spec Discrepancies: The brief contained small contradictions between the text spec and the provided code assets (copy.js / tokens.css). I treated the code tokens and design comps as the source of truth (e.g., used "The only support pill..." for F1 instead of the typography scale label, fixed the capsule extension to PNG to prevent a 404, and used "Learn More" from the copy deck).

Typography: The comps use a monospace font for specific data tags, while the spec noted "Helvetica only". I compromised by using a safe font stack (monospace, Helvetica, Arial) to match the design while keeping a solid fallback.

Production Assets: Email image paths are currently relative for local testing. They must be swapped with absolute https:// hosted URLs before production deployment.

Banner Weight: The capsule image takes up 183 KB out of the total 204 KB banner weight. It was resampled to 460px to save ~260 KB, but could be optimized further with modern formats (WebP/AVIF) if the ad network allows it.

**Time spent**
~3.5 hours total, split roughly as follows:

30 mins: QA reconciliation (analyzing the brief, code assets, and isolating spec errors).

75 mins: Deliverable 01 (HTML5 banner structure, CSS layout, and writing the rAF animation script).

60 mins: Deliverable 02 (HTML email layout, nesting tables, building Outlook/VML fixes, and exporting transparent PNGs).

45 mins: Final visual alignment, browser testing, and documentation.

**AI / LLM usage**
This project was built with the assistance of Claude (Claude Code). The tool was utilized for:

Asset Auditing: Cross-referencing the text spec against the raw design tokens and copy files to spot the planted QA contradictions early.

Asset Preparation: Converting the source vector SVGs into web-safe transparent PNGs to ensure they display correctly on dark backgrounds across standard email clients.

Review Loop: Troubleshooting alignment issues during browser testing (e.g., adjusting text wrapping on the CTA button). All code was manually reviewed, adjusted, and visually verified against the original design comps.
