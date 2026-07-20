# masonjgray-site

Astro 5 static site for masonjgray.com.

## Commands

```bash
npm run dev        # dev server at localhost:4321
npm run build      # production build to dist/
npm run preview    # preview production build locally
npx astro check    # type-check (no npm script wrapper — run explicitly)
```

## Content collections

Defined in `src/content.config.ts`:

- **`blog`** — Markdown/MDX files in `src/content/blog/`. Frontmatter: `title`, `description`, `pubDate`, `updatedDate?`, `heroImage?`.
- **`publications`** — Markdown files in `src/content/publications/`. Frontmatter: `title`, `authors`, `year`, `venue?`, `doi?`, `featured` (default false), `draft` (default false).

- **`projects`** — Markdown files in `src/content/projects/`. Frontmatter: `title`, `description`, `tags` (string array), `status` (`"active"` / `"archived"` / `"complete"`, default `"active"`), `githubUrl?` (url), `demoUrl?` (url), `featured` (default false).

All three collections are consumed by Astro pages:
- `src/pages/blog/[...slug].astro` — individual blog post
- `src/pages/blog/index.astro` — blog listing
- `src/pages/publications.astro` — full publication list (all non-draft sorted by year)
- `src/pages/cv.astro` — CV page (all non-draft, sorted by year)
- `src/pages/projects.astro` — project card grid (featured first)
- `src/pages/index.astro` — homepage (only `featured` + non-draft publications)

## Design

Everforest Dark color scheme applied in `src/styles/global.css`. CSS custom properties for all palette colors — use `var(--*)` or `rgb(var(--*))` as shown in existing components. The accent palette uses muted green/blue tones — avoid adding high-saturation colors.

## Site config

- `site` set to `https://masonjgray.com` in `astro.config.mjs`
- Output mode: `static` (no SSR)
- Integrations: `@astrojs/mdx`, `@astrojs/sitemap`
- Visual Studio Code: recommended extensions are `astro-build.astro-vscode` and `unifiedjs.vscode-mdx`

## CI

Pushing to `main` on GitHub auto-deploys via Astro's built-in adapter. No manual CI workflows.

## Style

- **No em dashes.** Use commas, semicolons, or other punctuation instead.
- The author frequently uses "e.g.", "i.e.", and semicolons where grammatically correct.

## No tests, no lint, no typecheck scripts

This repo has no `lint`, `typecheck`, or `test` scripts. Build verification = `npm run build`.
