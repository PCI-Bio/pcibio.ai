# pcibio.ai — the PCI AI product site

Static site, served by Vercel from the `main` branch of this repository. No build step: every file here is served as is.

- **Source of truth for the pages** is `docs/site/` in the `pci-platform` repository (design system, copy,
  illustrations, the demo video builder). This repository is the deploy copy plus `vercel.json`, `sitemap.xml`,
  `robots.txt` and the rendered demo video under `video/`.
- Pages: Overview (`index.html`), Platform (`platform.html`, with the demo video and chapters), Safety & data
  (`trust.html`), Education (`education.html` + `learn-p53`, `learn-mmr`, `learn-controls`, `learn-ai`, `learn-cases`),
  Start a pilot (`pilot.html`), Privacy & terms (`privacy.html`), `404.html`.
- `vercel.json`: clean URLs (`/platform`, not `/platform.html`), redirects from the previous site's `/education/...`,
  `/research/...`, `/login` and `/register` URLs, security headers (CSP allows only this origin; fonts are self-hosted),
  revalidate-on-visit caching for pages and images, one-year caching for the font files.

## Vercel settings
Framework preset **Other**, no build command, no install command, output directory **`.`** (the repository root),
production branch **`main`**. Every pull request gets a preview URL; merging to `main` deploys to production.
Domains: `pcibio.ai` (primary) and `www.pcibio.ai` (redirect to the primary). DNS is at GoDaddy and already points
at Vercel (A record `76.76.21.21`), so attaching the domain to this project needs no DNS change beyond the TXT record
Vercel asks for when a domain moves between teams.

## Updating the site
1. Change the pages in `pci-platform/docs/site/` (and rebuild the video with `docs/demo-video/build.py` if it changed).
2. Copy `docs/site/*` over this tree (keep `vercel.json`, `sitemap.xml`, `robots.txt`, `README.md`), drop the new
   render into `video/`, add any new page to `sitemap.xml`.
3. Commit on a branch, open a pull request, check the Vercel preview, merge.

Research use only — not for use in diagnostic procedures. The company is PCI (Precision Cellular Immunology, LLC).
