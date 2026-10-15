# Project context

This is a small Astro site about candidates in Kelowna's 2026 municipal election. It is intentionally understated and primarily editorial: avoid corporate messaging, promotional visuals, and unnecessary interface complexity.

## Site structure and content

- Astro runs with the Cloudflare adapter; page content uses the installed MDX integration.
- Main pages are `src/pages/mayor.mdx`, `src/pages/councillor.mdx`, and `src/pages/school-trustees.mdx`.
- The homepage at `src/pages/index.astro` permanently redirects to `/councillor/`.
- For MDX pages, use the shared layout in frontmatter, e.g.:

  ```yaml
  ---
  layout: '@/layouts/SiteLayout.astro'
  title: Page title
  description: Concise page description for search results.
  ---
  ```

  Astro supplies `title` and `description` directly as layout props. Do not wrap MDX page content in the layout component or read those props from `Astro.props.frontmatter`.
- The `@/*` alias maps to `src/*` in `tsconfig.json`; prefer it for project imports.
- Treat candidate assessments as the site's author's opinions. Preserve supplied wording and claims unless asked to edit them; structural Markdown changes are fine.

## Styling and navigation

- Tailwind CSS v4 is installed through `@tailwindcss/vite` in `astro.config.mjs`. Prefer Tailwind utilities in Astro components and page markup. Keep `src/styles/global.css` focused on resets, typography, accessibility, and Markdown/MDX prose styling.
- Keep the visual style restrained, readable, and mobile-friendly, using the warm off-white and muted green palette already defined in `global.css`.
- The shared navigation is in `src/components/Header.astro`. It uses a native `<details>` disclosure with an animated hamburger on mobile and a separate always-visible sidebar on desktop. Keep the mobile dropdown anchored beneath the header; avoid an unpositioned top-layer popover, which previously appeared detached from the menu button.
- Keep navigation as server-rendered links, with descriptive accessible names and `aria-current="page"` for the current page. Avoid React or client-side scripting unless a real requirement justifies it. Respect reduced-motion preferences for animations.
- Astro link prefetching is enabled in `astro.config.mjs`; page navigation links include `data-astro-prefetch`.

## SEO and accessibility

- `SITE_URL` is read by `astro.config.mjs` and is used for sitemap and canonical/Open Graph URLs. Set it to the real deployed origin in the build environment; do not restore a placeholder such as `https://example.com`.
- Use meaningful page titles and descriptions, semantic landmarks and headings, keyboard-visible focus, and a skip link. Keep the core content and navigation links in server-rendered HTML.

## Development

When starting the dev server, use background mode:

```sh
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

This environment may not expose `pnpm` in the default shell. If needed, run package commands through fish's login environment, for example `fish -lc 'pnpm exec astro build'`.

## Documentation

Full documentation: <https://docs.astro.build>

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)
