# Rabbithole Docs

Documentation for [Rabbithole](https://app.rabbithole.gg) and the campaign product behind it, built on [Mintlify](https://mintlify.com).

## Structure

| Tab | Audience | Directory |
| --- | --- | --- |
| Rabbithole | People earning on the app | `rabbithole/` |
| Campaigns | Protocols running a campaign | `campaigns/` |
| Developers | Teams integrating campaign data and claims | `developers/` |
| API Reference | Generated from the live OpenAPI spec | `api-reference/` + `docs.json` |

See [AGENTS.md](AGENTS.md) for terminology, style, and the list of pages whose content is expected to change.

## Local development

```bash
npm i -g mint
mint dev
```

Preview at `http://localhost:3000`. Run `mint broken-links` before opening a PR.

## Publishing

Pushes to `main` deploy automatically through the Mintlify GitHub app.
