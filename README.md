# Dead End QA

An adversarial pre-publication QA skill for Claude Code. It assumes every clickable, promised, or visually implied thing on your site fails until proven otherwise, then hands you a severity-graded report (P0–P3) with the user journeys it completed end to end.

Run it before you publish anything, or before you call a build done.

## Install

```bash
npx skills add boostcarloever/dead-end-qa-skill --skill dead-end-qa -g -y
```

Or paste that line into Claude Code and ask it to run it for you.

## Use

Ask Claude Code:

> QA this site with dead-end-qa before we publish.

The skill makes Claude:

- click every link, button, card, and footer item, and reject the ones that go nowhere
- walk the primary conversion journey start to finish (a prefilled email is not a funnel)
- check that every trust mark or claim leads to evidence or is labeled as illustrative
- test five viewports from 390px to 1440px, plus keyboard, focus, and reduced motion
- verify metadata, 404 behavior, console errors, and failed requests
- grade everything P0 (embarrassing — fix before anyone sees it) through P3 (polish)

A passing report must state which journeys were completed end to end. "The page loaded" is not a journey.

## Pairs well with

A browser-driving skill or tool, so Claude tests the real app instead of signing off on a screenshot.

## License

MIT
