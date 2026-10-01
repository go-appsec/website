# Toolbox documentation site

Astro + Starlight + Galaxy, built as a standalone static site. This package does not change the Go toolkit or start its server.

## Develop

Use Node.js >=22.12.0 and pnpm 11.3.0 (declared in `package.json`).

```bash
pnpm install
pnpm dev
pnpm check
pnpm build
pnpm preview
```

## Hosting

The site lives at the repository root and is configured for `https://goappsec.com/`, with Astro's `base` set to `/`. Canonical URLs, social URLs, assets, search, and the sitemap use that location. `public/CNAME` records the intended GitHub Pages custom domain.

`pnpm build` writes the static site to `dist/`. Publishing automation is proposed in a separate pull request.

Before publishing with GitHub Actions, a maintainer must select **Settings → Pages → Build and deployment → Source → GitHub Actions**, configure the custom domain, and point its DNS to GitHub Pages. Owning the domain alone does not configure hosting.

Local development and preview use the root path, for example `http://localhost:4321/`.

## Content accuracy

Pages summarize the main README, contributor guidance, SDK contract, and source at the checked-out revision. The installed CLI help and advertised MCP schemas are the detailed references for a running version.

The [go-appsec GitHub avatar](https://avatars.githubusercontent.com/u/251776565) is bundled unchanged for the header logo, favicon, and right-hand homepage image. GitHub serves it at 460×460 pixels. Dark surfaces use `#151b23`, highlights use `#df6009`, and light-theme accents use `#0a3253`.
