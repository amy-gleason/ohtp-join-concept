# OHTP join page — CMS-branded concept: rationale

Files: `index.html` (self-contained HTML/CSS mockup), `desktop-1440.png`, `mobile-390.png`, `assets/` (official assets only).
Brand source: *CMS Brand Strategy & Graphic Standards Guide*, Sept 2026 (page numbers are the guide's printed page numbers). The audit (`../ohtp-join-audit.md`) issue numbers are shown as **A1–A7**.

**Office name.** The live page, the Federal Register notice (June 11, 2026) and cms.gov all use **Office of Health Technology and Products (OHTP)**. The brief's "Office of Health Technology Policy" looks like a typo, so the concept uses "and Products".

## Main user task
An experienced technologist (engineer, product manager, designer, procurement specialist, or similar) decides whether CMS is worth applying to, and then **sends their information through the Qualtrics form**. Everything else on the page helps them make that decision. The page answers their questions in this order: what the work is, what happens after I apply, what I need, what it pays, and what benefits and time off I get.

## (a) Design choices mapped to brand rules

| Design choice | Rule it satisfies | Fixes |
|---|---|---|
| No OHTP symbol, wordmark, monogram or favicon. The office name appears only as plain text in the in-page nav bar and the H1. | p.7: never recreate the logo; ask MultimediaServices for a distinctive brand. p.12: units use the component logo OC develops for them. p.13: OC won't approve unique logos for limited-scope items. | A1 |
| The header uses the official **CMS.gov logo** file from cms.gov's `cms_evo` theme (`/themes/custom/cms_evo/logo.svg`), shown unaltered at 160–180px wide. Clear space is set by `--cms-logo-clearspace` at 32px, which is at least the height of the "C". | p.8: min 120px, clear space of "x" = height of C, no bleed. p.9: don't alter, stretch, recolor or combine. | A1, A4 |
| cms.gov chrome: USWDS banner ("An official website of the United States government"), cms.gov header with utility nav, and a cms.gov footer with the same link groups, the official **HHS logo** (cms.gov `hhslogo.png`), the "managed and paid for by CMS" line, the address and social links. | p.4–5: units tie closely to CMS. p.10: the HHS logo is used with CMS. Federal web requirements (21st Century IDEA). | A4, A7 |
| Palette is limited to **CMS Blue #015390** (headings, buttons, bands, footer), **CMS Gold #f3ce3b** (accent rules, bullet dots, large stat numbers on blue only) and **CMS Bright Blue #009ad0** (non-text accents only: note rules, nav hover underline), plus neutrals. The navy #002238, orange #e04a1c, ocean #0071bc and every other custom color are removed. | p.15: two primary colors plus a secondary accent. The secondary "adds visual interest". | A2 |
| Type is **Lexend** for headings and **Public Sans** for body, matching cms.gov `cms_evo`. Archivo, Newsreader and IBM Plex Mono are removed. No Optima is needed because the name line is never set without the logo. | p.9: don't change the logo typeface. p.12: Optima is only for a standalone name line. cms.gov web typography. | A3 |
| Calmer copy. The H1 is the page's own title, "Join the Office of Health Technology and Products". "Ready to make change? Start here." and "Do you feel called? Be part of the change." are replaced. Section headings are factual ("What you'll need", "Pay", "Benefits", "Time off"). | p.6: reassuring, helpful, stable, trustworthy, with fairness and accuracy. | A5 |
| Written as "Health Insurance Marketplace®". | p.6 (program names), p.5 | A6 |
| The "cool" comes from scale, whitespace and rhythm in the spirit of NDS: an 84px display H1, an oversized **$197,200** pay stat, a full-bleed CMS Blue program strip and time-off band, 120px section padding on desktop, a 12-column-style 7/5 hero split, and gold 4–8px rules as the only ornament. | p.15: restrained palette. p.6: stable and trustworthy. | — |
| Motion: the hero gold rule draws in, and sections fade up about 24px once. CSS + IntersectionObserver only. Content is visible without JS. Everything is disabled under `prefers-reduced-motion`. | WCAG 2.2 2.3.3 and 2.2.2. p.6: calm, stable tone. | — |
| Photography is a **labeled placeholder** for a real CMS team photo, with no stock imagery. | Authenticity and trust (p.4). Needs OC approval. | — |
| Components follow USWDS/CMS Design System patterns: `usa-banner`, `usa-button`, `usa-process-list`, `usa-summary-box`, `usa-card-group`. Custom blocks (stat, stat band, CTA, program strip) are thin layouts built from the same tokens. | Consistency (p.4). Dev PM direction. | — |

## (b) Contrast pairs used (WCAG 2.x relative luminance)

| Foreground | Background | Ratio | Use | Result |
|---|---|---|---|---|
| Ink #1b1b1b | White | 17.22 | body text | AA/AAA |
| Base #4a4f55 | White | 8.27 | secondary text, kickers | AA/AAA |
| Base #4a4f55 | Mist #f2f4f7 | 7.50 | secondary text on tinted sections | AA/AAA |
| Ink #1b1b1b | Mist #f2f4f7 | 15.63 | body on tint | AA/AAA |
| CMS Blue #015390 | White | 7.95 | headings, links, focus ring | AA/AAA |
| CMS Blue #015390 | Mist #f2f4f7 | 7.22 | headings/links on tint | AA/AAA |
| White | CMS Blue #015390 | 7.95 | buttons, bands, footer | AA/AAA |
| CMS Gold #f3ce3b | CMS Blue #015390 | 5.19 | large stat numbers only (≥28px bold), focus ring on dark | AA (also passes for normal text) |
| Ink #1b1b1b | CMS Gold #f3ce3b | 11.24 | reserved: `usa-button--accent-warm` (defined, not used in the mockup) | AA/AAA |
| CMS Bright Blue #009ad0 | White | 3.21 | **non-text only** (rules, hover underline): passes 1.4.11 at 3:1 | Fails as body text, so not used for text |
| CMS Bright Blue #009ad0 | Mist #f2f4f7 | 2.92 | decorative left rule on the process notes only (the text beside it carries the meaning) | decorative, exempt |
| **CMS Gold #f3ce3b** | **White** | **1.53** | **never used for text on white.** Gold appears on white only as decorative rules | Fails, so avoided |
| CMS Bright Blue | CMS Blue | 2.47 | not used | — |

Other checks:
- Focus is a 3px outline with 2px offset: CMS Blue on light backgrounds and Gold on dark.
- Targets are at least 24×24px (2.5.8). Buttons and nav links are 40–56px tall.
- There is a skip link, and landmarks for the banner, header, nav (global and "On this page"), main and footer.
- Heading order is H1 → H2 → H3 with no skips.
- Decorative images use `alt=""`. The logos have alt text: "CMS.gov" and "U.S. Department of Health and Human Services".
- axe-core 4.x (wcag2a/aa, wcag21aa, wcag22aa, best-practice) found **0 violations** on the desktop render.
- The mobile 390px view has no horizontal overflow.
- A manual screen-reader pass (NVDA/VoiceOver) is still needed for full Section 508 sign-off.

## (c) Items that still need OC sign-off
1. **Office identification.** The office name is set as text with no lockup. If OC wants the official component logo (CMS logo with "OFFICE OF HEALTH TECHNOLOGY AND PRODUCTS" centered beneath in blue, all caps, with no "&", per p.12), it has to come from MultimediaServices@cms.hhs.gov. We have not created one. The concept has no slot for it today, but the in-page nav title could take it.
2. **Logo choice.** The header uses the CMS.gov web logo, the same file cms.gov uses (its blue is #0d2499, not #015390). Confirm this is right for a cms.gov page rather than the full CMS logo with the swoosh from p.7. Also confirm that showing the HHS logo only in the footer is acceptable under the p.10 rule that HHS is "more prominent". That is how cms.gov does it today.
3. **Logo use approval** (p.14): Logos@cms.hhs.gov needs a sample at least two weeks before launch, if OC requires this for an internal web page.
4. **Photography.** The hero is a placeholder. OC needs to approve the real CMS staff photo, its releases and its alt text.
5. **Gold.** It is used only as accent rules, bullet dots and large numbers on CMS Blue. Confirm this amount of gold is acceptable.
6. **Motion.** One-time fade-up and the rule draw, off for reduced motion.
7. **Copy changes:**
   - The H1 now uses the page title.
   - The new closing heading is "Ready to apply? Send us your information." with the supporting line "Our talent team will review it and look for the best fit across CMS." This is proposed copy.
   - The intro heading reuses the original audience sentence: "Your work helps older adults, people with disabilities, low-income families, and children."
   - Kicker labels were added ("Careers at CMS", "Pay and benefits").
   - The pay label was reworded to "The top of the General Schedule pay scale in 2026." from "In 2026, General Schedule pay goes up to $197,200."
   - "The work supports" program strip.
   - Marketplace® is corrected.
8. **Hosting.** The audit (A7) recommends moving from github.io to a cms.gov Drupal page so it inherits the official chrome. OC and the web team need to confirm the URL, for example `cms.gov/about-cms/work-with-us/careers/ohtp`.
9. **Social links.** The footer uses text links. The current page and cms.gov differ on Facebook (/CMSGov vs /medicare) and on X/Twitter, so OC should confirm which accounts to use.

## (d) Token and component notes for Drupal (Front-End and Back-End)
**Tokens.** All tokens are CSS custom properties in `:root`, named after USWDS theme tokens:
- Colors: `--cms-color-primary` = USWDS `primary`, `--cms-color-accent-warm` and `--cms-color-accent-cool`, plus `--cms-color-ink`, `--cms-color-base`, `--cms-color-base-lighter`, `--cms-color-base-lightest` and `--cms-color-white`.
- Spacing: `--cms-spacing-1`…`-15`, in 8px units.
- Type: `--cms-type-2xs`…`--cms-type-display`.
- Fonts: `--cms-font-heading` and `--cms-font-body`.
- Focus: `--cms-focus-*`.

In `cms_evo`, map these to the existing theme settings and Sass tokens (`$theme-color-primary: #015390`, etc.) rather than shipping a new stylesheet. The fonts already ship with cms.gov, so drop the Google Fonts link.

**Global regions** (not editable per page): `usa-banner`, `cms-header` and `cms-footer`, using the existing `cms_evo` templates. Don't rebuild them.

**Block:** `cms-localnav`, an "On this page" menu. It holds the office name as plain text, a menu of anchor links and an Apply link. It is sticky and hides the anchors below 1024px.

**Paragraph types (suggested):**

| Paragraph type | Fields |
|---|---|
| `hero` | kicker, H1, lede, CTA link, CTA note, media (image + alt) |
| `inline_list` (program strip) | label, list items (taxonomy reference to CMS programs) |
| `text_with_tags` (intro) | statement, body, tag list |
| `process_list` | heading, kicker, repeating step (title, body), notes (2× text) |
| `text_with_summary_box` (accommodations) | heading, body, box heading, box list |
| `checklist` (requirements) | heading, items |
| `stat` (pay) | number, label, body, link |
| `card_group` (benefits) | heading, intro, repeating card (title, body, optional link) |
| `stat_band` (time off) | heading, repeating stat (value, label), link. Dark variant |
| `cta` | heading, body, button link, fine print (2× text) |

**Section wrapper.** `cms-section` takes modifiers `--tint` and `is-dark`. Expose these as a "background" select on each paragraph: white / mist / CMS Blue.

**Motion.** Add the `.cms-reveal` class in the paragraph template. The JS is about 10 lines and can go in a Drupal library attached to the node type. No dependency is needed.

**Apply links.** These keep the existing `?source=` tracking parameters (join-nav, join-hero, join-closing).

## Open questions for the PM
1. Will the page live on cms.gov (Drupal, `cms_evo`) or stay on github.io? This decides whether we build the chrome or inherit it.
2. Does OC want an official OHTP component logo requested from Multimedia Services, or text-only identification?
3. Can we get a real team photo (with consent and release), and who owns alt text and approval?
4. Is the Qualtrics form final, and does it carry its own accessibility and privacy notices (PIA/SORN statement)? Do the `source` parameters still feed reporting?
5. Is there a list of current openings or a USAJOBS link to add? The current page only collects interest.
6. Who signs off on the copy edits listed in (c)7, OC, OHTP leadership or both?
7. Should the page get a Spanish version or a "Language assistance" link to match cms.gov?
