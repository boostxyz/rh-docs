# Open questions carried over from the preview drafts

Each item was a purple review flag in the preview site. Resolve before publishing the page.


## campaigns/pricing.mdx

- OQ-16: tier breakpoints and rates below are a proposal, not signed off. See OPEN-QUESTIONS.md for the constraints that apply before this page ships.

## developers/concepts/claiming.mdx

- OQ-6: confirm whether userPosition.claimable and rewards.forUser().claimable still disagree with claims.get(), or whether that is now fixed.
- OQ-8: confirm whether the root publication cadence can be published as a specific interval.
- OQ-10: confirm cliff availability. campaign-modes.mdx lists it as coming soon, and no live campaign currently runs it.
- OQ-13: confirm whether the 60-day window is universal and whether it is exposed anywhere in the API.

## developers/guides/show-user-rewards.mdx

- OQ-6: confirm whether userPosition.claimable and rewards.forUser().claimable still disagree with claims.get().

## developers/guides/claim-rewards.mdx

- OQ-7: confirm whether the post-claim API lag is expected caching behaviour or a bug to fix.

## developers/sdk.mdx

- OQ-9: confirm the public changelog and deprecation commitment for the SDK.

## developers/contracts.mdx

- OQ-5: confirm the canonical supported reward-chain list rather than the observed one.
- OQ-11: verify and publish the exact getCampaign / claimed ABI fragments.

## developers/overview.mdx

- OQ-1: confirm the canonical developer support channel (docs currently say Discord).
- OQ-2: document the actual request process and turnaround for a partner refId.
