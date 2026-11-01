# Tequipy API Docs (Mintlify)

Mintlify documentation site for the Tequipy Integration API. The API reference is
auto-generated from `api-reference/openapi.yaml`, so updating that file updates the docs.

## Structure

```
tequipy-docs/
├── docs.json                  # Mintlify config (theme, nav, colors)
├── authentication.mdx         # Auth guide
└── api-reference/
    └── openapi.yaml           # Your OpenAPI spec → auto-generated reference
```

## Preview locally

```bash
npm i -g mint        # install the Mintlify CLI
cd tequipy-docs
mint dev             # serves at http://localhost:3000
```

To check for broken links: `mint broken-links`.

## Deploy

1. Push this folder to a GitHub repo.
2. Go to https://dashboard.mintlify.com, sign in, and connect the repo.
3. Install the Mintlify GitHub App when prompted — docs redeploy on every push to
   the default branch.
4. (Optional) Add a custom domain like `docs.tequipy.com` in the dashboard under
   Settings → Custom Domain, then point a CNAME at Mintlify.

## Updating the API reference

Replace `api-reference/openapi.yaml` with a new export of your spec and push. No
other changes needed — Mintlify regenerates every endpoint page automatically.

## Sandbox guides

The `Sandbox` group in `docs.json` starts at `sandbox/overview.mdx` and links to
the Simulation API contract, five workflow guides, state diagrams, integration
questions, manual processes and troubleshooting. Postman collections and their shared
environment live in `downloads/sandbox/`. Keep exported tokens empty.

When changing a guide, compare its actions, parameters, allowed states and side
effects with the current core-service implementation and update the corresponding
collection. Changes to the generated OpenAPI reference do not update these guides.
Run `mint validate` and `mint broken-links` before publishing. Use a prepared
sandbox company and a read-write token for live scenario verification; these runs
create records and can send notifications.
