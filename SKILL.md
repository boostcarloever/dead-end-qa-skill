---
name: dead-end-qa
description: Adversarial pre-publication QA for any web app or site. Assumes every clickable, promised, or visually implied thing fails until proven otherwise. Run before publishing or calling a build done; produces a severity-graded report with completed user journeys.
---

# Dead End QA Agent

Every site or app must be reviewed by a dedicated Dead End QA agent before publication. The agent is adversarial: it assumes that anything clickable, promised, or visually implied may fail until it proves otherwise.

Drive the real app with `agent-browser` (load the `agent-browser` and `dogfood` skills). Do not sign off on a single screenshot.

The automated checker discovers every directory containing an `index.html`. A newly added project therefore enters QA automatically, and the build fails if that project does not also include its own `AGENTS.md` instructions.

## Mission

Find every place where a visitor can become confused, trapped, dropped into email, sent to an unfinished experience, or shown a promise with no credible next step.

## Required checks

1. **Navigation and links**
   - Click every navigation item, CTA, card, logo, badge, text link, and footer link.
   - Verify every anchor reaches a real section and leaves the target visible below sticky navigation.
   - Reject empty links, `#`, `javascript:` URLs, missing files, wrong-site links, and silent clicks.
   - Confirm the browser back button returns to the expected state.

2. **Conversion journeys**
   - Follow the primary journey from first screen to completed application or booking.
   - A prefilled email is a temporary contact route, not a completed conversion funnel.
   - Verify success, error, duplicate-submission, validation, spam-protection, and confirmation states for forms.
   - Confirm package selection and campaign attribution survive the journey.

3. **Trust journeys**
   - Every certification or verification mark must open a verification destination or be visibly labeled as illustrative.
   - Claims about testing, batches, clinicians, payments, applications, apps, and order visibility must lead to evidence or an honest demo state.
   - Prototype, pilot, proposed, and production capabilities must not be blurred together.

4. **Responsive and visual QA**
   - Test at 390 px, 430 px, 768 px, 1024 px, and 1440 px widths.
   - Check image focal points, faces, hands, products, captions, overlays, text wrapping, and horizontal overflow.
   - Confirm `figure` elements have no browser-default margin and important photos do not rely on one universal center crop.
   - Test keyboard navigation, visible focus, reduced motion, zoom, and screen-reader landmarks.

5. **Technical completeness**
   - Verify all local assets, canonical URLs, metadata, structured data, favicon, social image, `robots.txt`, `sitemap.xml`, and `llms.txt`.
   - Test the published home page and required support files for HTTP success.
   - Check console errors, failed requests, custom 404 behavior, and low-bandwidth loading.
   - Confirm analytics and consent behavior when analytics is enabled.

## Severity

- **P0:** unsafe, misleading, privacy-sensitive, or regulated claim with no valid boundary.
- **P1:** primary navigation, conversion, verification, or mobile experience is broken.
- **P2:** secondary journey, accessibility, metadata, or trust detail is incomplete.
- **P3:** polish issue that does not block understanding or action.

## Required report

For every issue, record the site, viewport, element or selector, expected result, actual result, severity, evidence, and recommended owner. A passing report must also state which user journeys were completed end to end. "The page loaded" is not a journey.

Run the static checker first when the project has one:

```bash
npm run qa:dead-ends
```

Use strict mode before a production-domain launch:

```bash
npm run qa:dead-ends:strict
```

If the project has no checker, add a minimal one (scan for `href="#"`, `href=""`, `javascript:`, missing local files) as `qa:dead-ends` before running the manual checks.
