# Rabbithole docs — agent instructions

This is the Mintlify documentation site for Rabbithole (app.rabbithole.gg) and the campaign product behind it. `AGENTS.md` is the single source of repo guidance; `CLAUDE.md` is not used here.

## Layout

- `docs.json` — site config and navigation. Four tabs: **Rabbithole** (end users), **Campaigns** (protocols running a campaign), **Developers** (SDK and integration guides), **API Reference** (generated from the live OpenAPI spec at `https://api-tbi.boost.xyz/v1/openapi.json`; do not hand-write endpoint pages).
- `rabbithole/` — user-facing pages about the app: earning, tiers, raffle, referrals, FAQ.
- `campaigns/` — the product concepts (reward model, lifecycle, modes, activation), pricing, partner referrals, launch process, glossary.
- `developers/` — quickstart, examples (complete React + wagmi components, one per partner use case), concepts, guides (endpoint-level, curl + TypeScript), SDK, contracts, errors. Examples link down to the guide that explains their endpoints; do not duplicate endpoint detail in an example.
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

- **Raffle and tier rules** were rebuilt in September 2026 (four-week raffle, claim-based weekly tiers, weekly USDC pool). Prizes are announced per raffle and are not committed on-chain, so do not document prize amounts as fixed. Tier thresholds, multipliers, and the 500 USDC weekly pool are current configuration.
- **Pricing** on `campaigns/pricing.mdx` is a proposal under review.
- Numbers observed in the live app (tier entry counts, prize size, cut-offs) are examples of the current configuration, not commitments.

## Animated components (snippets)

Interactive pieces ported from the landing site live in `snippets/*.mdx` and are styled by `style.css` (scoped under `.rh-anim`, with dark-mode tokens under `html.dark`). The Mintlify snippet compiler is strict; every one of these was learned the hard way:

- Use `.mdx` files, not `.jsx`. The local CLI never resolves `.jsx` snippets.
- One self-contained `export const Component = () => { ... }` per concern. Helpers, constants, and data must live **inside** the component body. Sibling exports in the same file are not in scope at runtime.
- No blank lines inside an `export` block. MDX ends the block at the first blank line and the rest becomes prose.
- No grouping parentheses in expressions: `(a + b) * c`, `!(x in y)`, `(v / t).toFixed()` all crash the code printer. Hoist into named constants and reorder arithmetic instead.
- No `//` comments outside an export block. They render as text.
- Hooks (`useState`, `useEffect`, `useRef`) are injected. No imports, no npm packages, no `useLayoutEffect` or `useId`.
- Import into a page with `import { X } from "/snippets/x.mdx"` directly under the frontmatter.
- The local CLI must be current: `pnpm add -g mint@latest --config.node-linker=hoisted && mint update`. The hoisted flag is required with pnpm 11: `@mintlify/link-rot` imports `react` without declaring it, so the default isolated layout crashes on launch with `ERR_MODULE_NOT_FOUND`. Kill dev servers by PID; `mint dev` restarts otherwise stack on new ports.

## Validation

```bash
mint dev            # local preview at http://localhost:3000
mint broken-links   # every internal link and image must resolve
mint openapi-check https://api-tbi.boost.xyz/v1/openapi.json
```

Run `mint broken-links` before opening a PR.
