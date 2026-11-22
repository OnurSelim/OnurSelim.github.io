# Website redesign: academicpages → Barron-style single page

## Goal

Replace the current academicpages (Jekyll) site with a single static HTML page in the style of
[Jon Barron's template](https://github.com/jonbarron/jonbarron_website), similar to
[karaozgur.com](https://karaozgur.com/).

Site stays at `https://onurselim.github.io`, served from this repo (`OnurSelim/OnurSelim.github.io`).

## Why

- Current site is barely customised (last edit Oct 2022; posts/publications are still theme samples).
- One `index.html` is easier to edit than Jekyll markdown + config, previews by opening the file,
  and needs no Ruby/Jekyll build.

## Decisions

- **Reuse this repo**, don't create a new one: the root URL `onurselim.github.io` only works from a
  repo named `OnurSelim.github.io`, and Pages is already configured here.
- **Keep the old site recoverable** via a git tag before deleting anything.

## Steps

1. Tag current state: `git tag academicpages-backup && git push origin academicpages-backup`.
2. Remove Jekyll files (`_config*.yml`, `_pages/`, `_posts/`, `_publications/`, `_talks/`, `_teaching/`,
   `_portfolio/`, `_includes/`, `_layouts/`, `_sass/`, `_data/`, `_drafts/`, `Gemfile`, `package.json`,
   `markdown_generator/`, `talkmap*`, theme `assets/`, `CHANGELOG.md`, `CONTRIBUTING.md`).
3. Add:
   - `index.html` — the whole site
   - `assets/` — `prof_pic.jpg`, `logos/`, `publication_preview/`, `cv.pdf`
   - `.nojekyll` — empty file so GitHub serves files as-is
4. Preview locally (open `index.html`, or `python -m http.server`).
5. Push to `master` when happy; Pages redeploys automatically.

## Page sections

- **Header / nav**: name, one-line tagline; links to About, News, Publications, Service, CV (PDF).
- **About**: photo, short bio, links (email, Google Scholar, GitHub, LinkedIn, X).
- **Research highlights**: horizontal scrolling cards (optional).
- **News**: dated one-liners, newest first.
- **Education**, **Research experience**, **Industry experience**: entries with institution logos.
- **Publications**: preview image, title, authors, venue, TL;DR, links (paper / code / project page).
- **Service & recognition**: reviewing, talks, teaching, awards.
- **Footer**: credit to Jon Barron's template.

## Content needed

- [ ] Bio (a few sentences) and tagline
- [ ] Profile photo
- [ ] Contact / profile links
- [ ] Education and experience entries (+ logos)
- [ ] Publications (or Google Scholar link to pull from) + preview images
- [ ] News items
- [ ] Service, talks, teaching, awards
- [ ] CV PDF

## Updating the site later

Edit `index.html` (copy an existing block, change the text), add images under `assets/`, commit, push.
