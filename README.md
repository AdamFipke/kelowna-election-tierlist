# Kelowna 2026 Election Notes

A small, independently written guide to candidates in Kelowna's 2026 municipal election. Built with Astro, MDX, and Tailwind CSS; pages render statically without client-side JavaScript.

## Pages

- `/mayor/` — Mayoral candidates (TODO)
- `/councillor/` — Councillor candidate notes
- `/school-trustees/` — School trustee candidates (TODO)

Page content lives in `src/pages/` as `.mdx` files. Shared layout and accessibility styles live in `src/layouts/SiteLayout.astro` and `src/styles/global.css`.

Set `SITE_URL` to the deployed site's canonical origin (for example, `https://your-domain.example`) in the build environment. Astro uses it for canonical/Open Graph URLs and the sitemap; when it is unset, the site avoids emitting incorrect `example.com` canonical metadata.

## Commands

Run commands from the project root:

| Command | Action |
| --- | --- |
| `pnpm dev` | Start Astro's local development server |
| `pnpm build` | Build the site to `dist/` |
| `pnpm preview` | Preview the production build locally |
| `pnpm astro check` | Check Astro and TypeScript diagnostics |
| `pnpm deploy` | Build and deploy to Cloudflare |
