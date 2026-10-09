# Hermes-Agent-test-002

A single-file task manager, built as a zero-dependency HTML artifact and
published automatically to GitHub Pages.

**Live site:** https://yuchenweisam.github.io/Hermes-Agent-test-002/

## What it does

- Add tasks
- Mark tasks done / not done
- Delete tasks
- Filter by All / Active / Done
- Clear completed tasks
- Everything persists in `localStorage` (`hermes.tasks.v1`) and syncs across tabs

## Design notes

- Composed as an **Operate** surface: controls and list density over marketing framing
- Warm neutral palette with a single rust accent (deliberately not the default indigo)
- Type triad: serif display title, system sans for UI, mono for numerals and key hints
- Automatic light/dark via `prefers-color-scheme`; all motion collapses under
  `prefers-reduced-motion`
- Accessible: real `:focus-visible` rings, 44px minimum hit targets, `aria-label`s on
  every control, `aria-live` counter, semantic HTML
- Task text is inserted with `textContent`, never `innerHTML`, so task content cannot
  inject markup

## Deployment

`.github/workflows/pages.yml` publishes the site on every push to `main`:

1. `build` — checks out the repo, stages `index.html` (plus `.nojekyll`) into `_site`,
   and uploads it as a Pages artifact
2. `deploy` — publishes that artifact with `actions/deploy-pages`

No build step and no dependencies; the artifact is the static file itself.

## Local use

Open `index.html` in any browser. No server, no install.
