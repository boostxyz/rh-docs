# Rabbithole docs — agent instructions

This is the Mintlify documentation site for Rabbithole (app.rabbithole.gg) and the campaign product behind it. `AGENTS.md` is the single source of repo guidance; `CLAUDE.md` is not used here.

## Layout

- `docs.json` — site config and navigation. Four tabs: **Rabbithole** (end users), **Campaigns** (protocols running a campaign), **Developers** (SDK and integration guides), **API Reference** (generated from the live OpenAPI spec at `https://api-tbi.boost.xyz/v1/openapi.json`; do not hand-write endpoint pages).
- `rabbithole/` — user-facing pages about the app: earning, tiers, raffle, referrals, FAQ.
- `campaigns/` — the product concepts (reward model, lifecycle, modes, activation), pricing, partner referrals, launch process, glossary.
- `developers/` — quickstart, concepts, guides, SDK, contracts, errors.
- `images/rabbithole/` — app screenshots. `logo/` — wordmark (light/dark) and glyph.
- `.claude/preview-open-questions.md` — unresolved review flags inherited from the draft developer pages. Resolve or remove before publishing the page they belong to.

## Terminology

- The product is **Rabbithole**. The reward mechanism is a **campaign**. Use "campaign" in user- and protocol-facing pages.
- **Time-Based Incentives (TBI)** is the internal and SDK name. Mention it once in the Campaigns introduction and use it freely in developer pages where it matches the SDK, API, and contract names (`@boostxyz/tbi-sdk`, `api-tbi.boost.xyz`, TBI Manager).
- **Hold to Earn** is the in-app name for the campaign list.
- **Boost** is the company that operates the platform. "The team" or "the Rabbithole team" is fine in prose; Boost stays in contract, SDK, and API names.
- Tiers are Bronze, Silver, Gold, Platinum, Diamond. Raffle **entries**, not tickets, in prose.
- Support and contact go through Discord (`https://discord.gg/JTCqaekdm`), not email.

## Style

- Title Case for page titles and H2/H3 headings (matches the bulk of the existing content).
- Active voice, second person for user-facing pages.
- Mintlify components: `<Note>`, `<Warning>`, `<Tip>`, `<Steps>`, `<CardGroup>`, `<Frame>`, `<AccordionGroup>`, `<CodeGroup>`.
- Screenshots go in `<Frame>` with a descriptive `alt`.
- Escape `<`, `{`, and `}` in prose; MDX treats them as JSX.

## Things that change and must not be hard-coded as permanent

- **Raffle mechanics and tier boundaries** are being rebuilt (announced in-app, September 2026). Keep the warning on `rabbithole/raffle.mdx` until the new rules ship, then rewrite the page.
- **Pricing** on `campaigns/pricing.mdx` is a proposal under review.
- Numbers observed in the live app (tier entry counts, prize size, cut-offs) are examples of the current configuration, not commitments.

## Validation

```bash
mint dev            # local preview at http://localhost:3000
mint broken-links   # every internal link and image must resolve
mint openapi-check https://api-tbi.boost.xyz/v1/openapi.json
```

Run `mint broken-links` before opening a PR.
