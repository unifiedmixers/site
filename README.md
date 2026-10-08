# unifiedmixers/site

The product page for https://unifiedmixers.org and https://www.unifiedmixers.org.

Plain static HTML — one file, no build step, no JavaScript, no external assets.
Keep it that way.

## Deploy

Direct-upload Pages project `unifiedmixers` (not git-connected):

```powershell
$env:CLOUDFLARE_API_TOKEN = '<token with Cloudflare Pages: Edit>'
$env:CLOUDFLARE_ACCOUNT_ID = '<the account id — dashboard homepage sidebar>'
cd site
npx --yes wrangler@4 pages deploy . --project-name unifiedmixers --branch main --commit-dirty=true
```

Note: this file is served at /README.md — direct-upload mode ignores
`.assetsignore`. Keep anything private out of it.

## DNS reality check (2026-10-08)

The zone also carries cloudflared tunnels, including a wildcard
`*.unifiedmixers.org` CNAME pointing at the Neo4j tunnel. `www` and the apex
are specific records that win over the wildcard — but **any new subdomain
(docs, api, app) must get its own record**, or the wildcard swallows it.

The footer carries the Impressum link on purpose — § 5 TMG applies the moment
a page markets something under the umbrella. Don't remove it during redesigns.
