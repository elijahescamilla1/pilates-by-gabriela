# PLAN.md — Pilates by Gabriela site fixes

Point Claude Code at this file: `claude` in the repo, then say
"work through PLAN.md, top to bottom, and commit after each item."
Check off `- [ ]` boxes as you complete them.

## Project context (read first)

- Single file: `index.html` holds everything. CSS is in an inline `<style>`
  block, JS in an inline `<script>`. No build step.
- External assets: Google Fonts, and the `media/` folder (images + 9 `<video>`).
- Reveal animations: elements use a `data-reveal` attribute and an
  `IntersectionObserver` (threshold 0.18) that fades them in on scroll.
- Pricing buttons: three `<button data-package="...">` with values `intro`,
  `private`, `duet`. All currently link to the Square site root.
- Deploy: push to `main`; GitHub Pages redeploys in ~1-2 min.
- Do not introduce a framework or build tooling. Keep it one static file.

## Inputs needed from me (ask before doing these)

- Three Square product URLs for intro / private / duet (item 5)
- Final wording for the intro card (item 6) and third testimonial (item 10)
- A 1200x630 social share image (item 8)
- Poster still frames for hero videos if not already in `media/` (item 2)

---

## Tier 1 — must fix

- [x] **1. Blank hero on load.** Hero content uses `data-reveal` + opacity:0
  and only appears after the observer fires, so a hard refresh flashes blank.
  Make content visible by default: add a `js` class to `<html>` from JS first
  thing, and only apply the hidden "from" state under `html.js [data-reveal]`.
  Immediately reveal any `[data-reveal]` already in the viewport on load.
  Honor `prefers-reduced-motion: reduce` (show all, no transition). Verify a
  hard refresh shows the full hero with zero scrolling; leave lower-page
  reveals looking the same.

- [x] **2. Hero video poster + overlay.** Videos show a blank gradient while
  loading and a heavy tint hides the movement. Add `poster` stills to each
  hero `<video>`; ensure `autoplay muted loop playsinline preload="metadata"`;
  lighten the overlay opacity so footage is visible but text stays legible.
  Show me which CSS rule controls the overlay before changing it.

- [x] **3. Mobile check.** Confirm hero, video carousel swipe, pricing cards,
  and nav collapse hold up at 390px wide and on a real phone.

## Tier 2 — should fix

- [x] **4. Text contrast (WCAG AA).** Darken the light-tan eyebrow labels
  ("VENICE BLVD · LOS ANGELES", "BEYOND THE STUDIO") and low-contrast body
  copy until body text hits 4.5:1 and large text 3:1. List each color changed
  with old/new hex and the ratio.

- [ ] **5. Deep-link Shop now buttons.** Map each `data-package` value
  (intro/private/duet) to its specific Square product URL via a small JS
  lookup; fall back to the Square root if missing. (Needs the 3 URLs.)

- [ ] **6. Clarify Intro vs Private pricing.** Both show $90. Update the
  New Client Intro copy to make clear what it includes vs a standard private
  (e.g. one-time first session, assessment + goals). Draft two options if I
  don't provide wording.

- [x] **7. Add Open Graph / Twitter tags.** No `og:`/`twitter:` tags exist.
  Add `og:title`, `og:description`, `og:image` (absolute URL, ~1200x630),
  `og:url`, `og:type=website`, and `twitter:card=summary_large_image`. Base
  text on the existing title/meta description. (Favicon already present.)

## Tier 3 — polish

- [x] **8. Pricing card layout.** Rebalance vertical spacing so content sits
  more centered inside the arch cards; keep equal heights and the "Most
  popular" treatment.

- [ ] **9. Third testimonial.** Add a third quote with matching markup so the
  row balances; note the source (Google/Square) if applicable.

- [ ] **10. Optional trust block.** Studio hours, a one-line cancellation
  note, or a short FAQ near the location/booking area, matching existing type.

## Final QA — before delivery

- [ ] **11. Full pass.** Click every nav anchor, CTA, and social icon and
  confirm destinations. Confirm hero shows on hard refresh, layout holds at
  390px, and there are no console errors.
- [ ] **12. Live check.** Test the deployed URL in incognito and on a phone.
