# mazek.github.io — personal site (www.marcinmazurek.com)

Jekyll site published by GitHub Pages from `master` (legacy build, no Actions).

## Adding a new project

Follow all of these steps; past projects broke the homepage when one was skipped.

1. **Location:** put the page at `projects/<slug>.html` (English `projects/`, never `projekty/` or a new top-level folder).
   Assets go next to it, prefixed with the slug: `projects/<slug>-preview.png`, `projects/<slug>_pakiet.zip`, `projects/<slug>-something.pdf`.
   Reference them with relative paths (`<slug>-preview.png`), not `../`.
2. **Homepage listing:** append an entry at the **END** of `_data/projects.yml` (never at the top — articles and older projects come first):
   ```yaml
   - title: "Project name"
     url: /projects/<slug>.html
     description: "One or two sentences in English; note languages, e.g. (EN/PL)."
   ```
   Articles of the "Local Sovereign AI" series go to `_data/articles.yml` instead (title format `#7 Title`).
3. **Back link:** every project page needs a link back to its own spot on the homepage, at the top of its header:
   ```html
   <a class="home-link" href="/#<slug>" style="font-size:13px;color:inherit;opacity:.65;text-decoration:none;white-space:nowrap">← marcinmazurek.com</a>
   ```
   The homepage gives each list item `id="<slug>"` automatically (file name without `.html`), so `/#<slug>` scrolls to it and highlights it. Never link back with `../` or plain `/`.
4. **Downloads:** every file you add (PDF, ZIP, STL…) must be linked from the page; check that each `src`/`href` target exists.
5. **Moving a published page:** leave a small redirect page (meta refresh + canonical + `noindex`) at the old URL.

## Homepage

- `index.html` renders two columns: Articles (`_data/articles.yml`) and Projects (`_data/projects.yml`).
- Styles: `_sass/_layout.scss` (homepage-only rules under `.home`), base sizes in `css/main.scss`. Keep the homepage compact.

## Local build

```sh
BUNDLE_PATH=/tmp/gems bundle install && BUNDLE_PATH=/tmp/gems bundle exec jekyll build
```
Sass `@import` deprecation warnings are expected and harmless.

## Git

Pull before starting (other sessions push to `master` too). Commit and push only when asked.
