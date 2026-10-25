# Oqen

A minimal, static Astro landing page for the independent game studio Oqen, at **https://oqen.org**. Custom SVG lettering, responsive layout, no client JavaScript, no remote fonts, and no tracking.

## Local development

Use Node.js 24 (`nvm use` if you use nvm).

```sh
npm ci
npm run dev
```

`npm run build` produces `dist/`. `npm run preview` serves that production build locally.

## Publish to GitHub Pages

1. Push this project, including `package-lock.json`, to the `main` branch of your GitHub repository.
2. In **Settings → Pages → Build and deployment**, set **Source** to **GitHub Actions**.
3. Under **Custom domain**, enter **oqen.org** and save. Do this before updating DNS. `public/CNAME` is included for portability, but Actions deployments still require this repository setting.
4. At your domain's DNS provider, add these four `A` records for `@` (the root domain):

   | Type | Name | Value |
   | --- | --- | --- |
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |

5. Optionally add a `CNAME` record for `www` pointing to `<your-github-owner>.github.io` (replace the placeholder with your GitHub user or organization name; exclude the repository name).
6. Open **Actions** to confirm the deployment succeeds. If the initial push happened before Pages was enabled, run **Deploy to GitHub Pages** manually.
7. Once the domain check and certificate are ready, enable **Enforce HTTPS** in Pages settings. DNS and certificate provisioning can take up to 24 hours.

The workflow builds and deploys automatically on subsequent pushes to `main`. The Astro `site` is already `https://oqen.org`; a repository `base` path is unnecessary for this custom domain.

References: [Astro GitHub Pages deployment](https://docs.astro.build/en/guides/deploy/github/) and [GitHub custom domain setup](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

## Edit

- Page copy, wordmark, and styling: `src/pages/index.astro`
- Browser icon: `public/favicon.svg`
- Domain and build settings: `astro.config.mjs`
- Deployment: `.github/workflows/deploy.yml`
