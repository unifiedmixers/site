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

## DNS reality check (updated 2026-10-08)

The zone carries cloudflared tunnels (`llm`, `vllm`, `ms-neo4j` — each on its
own explicit record). A wildcard `*.unifiedmixers.org` to the Neo4j tunnel
existed until 2026-10-08, when the owner ruled it out: no more self-service
subdomains for the tunnel operator. **Every subdomain — docs, api, app, or a
new tunnel hostname for anyone — gets its own explicit record, minted by the
zone owner.** Unknown names are NXDOMAIN by design.

The footer carries the Impressum link on purpose — § 5 TMG applies the moment
a page markets something under the umbrella. Don't remove it during redesigns.
