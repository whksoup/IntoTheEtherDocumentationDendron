# Working Notes — Dendron workspace

A hierarchical notebook authored in Dendron and published as a static site
to GitHub Pages via Dendron's Next.js publishing pipeline.

## First-time local setup

1. Install the **Dendron** extension in VS Code, then open this folder —
   Dendron recognizes `dendron.yml` and loads `vault/` automatically.
2. Edit `dendron.yml`:
   - `siteUrl` and `assetsPrefix` — see the two cases below.
   - `title`, `description`, `author`.
3. Install the publishing CLI and pull the Next.js template:
   ```bash
   npm init -y            # already done — package.json is checked in
   npm install @dendronhq/dendron-cli@latest
   npx dendron publish init
   ```
   This clones a Next.js site into `.next/` and installs its dependencies.
   It's a large, one-time pull; the CLI is unmaintained software, so if this
   step fails, check the extension's Discord/issues before assuming your
   config is at fault.
4. Preview locally:
   ```bash
   npx dendron publish dev
   # http://localhost:3000
   ```

## `siteUrl` / `assetsPrefix` — pick one

- Repo named `USER.github.io` (a user/org site, served at the domain root):
  ```yaml
  siteUrl: https://USER.github.io
  ```
  (leave `assetsPrefix` unset)
- Any other repo name (a project site, served at a sub-path):
  ```yaml
  siteUrl: https://USER.github.io
  assetsPrefix: /REPO_NAME
  ```

## Deploying

1. Push this repository to GitHub.
2. Create a `pages` branch once, so GitHub Pages has something to point at:
   ```bash
   git checkout -b pages
   git push -u origin HEAD
   git checkout main
   ```
3. In the repo's **Settings → Pages**, set the source to the `pages` branch,
   `/ (root)` folder.
4. Push to `main`. `.github/workflows/publish.yml` builds the Next.js export
   and force-pushes the static output to `pages`. The first run is slow
   (Next.js is generating assets from scratch); later runs are incremental.

## Writing

- New note under `notes.*`, `sources.*` or `topics.*`: use Dendron's lookup
  panel (`Ctrl/Cmd+L`) and type the full dotted path, e.g.
  `notes.your-new-idea`.
- Link between notes with wikilinks: `[[Display text|notes.your-new-idea]]`.
  Backlinks and the graph view are automatic — nothing to maintain.
- A note only publishes if its top-level hierarchy is listed under
  `publishing.siteHierarchies` in `dendron.yml` (currently `notes`, `sources`,
  `topics`) and it doesn't carry `published: false` in its frontmatter.

## Layout

```
dendron.yml                 workspace + publishing config
package.json                pins the dendron-cli dependency
vault/
  root.md                   workspace root note (not published standalone)
  notes.md                  index note for the notes hierarchy
  notes.<slug>.md            individual notes
  sources.md                index note for the sources hierarchy
  sources.<slug>.md          individual sources
  topics.md                  index note for the topics hierarchy
  topics.<slug>.md           individual topic maps
  assets/images/              images, referenced with markdown ![]()
.github/workflows/publish.yml   Next.js export → pages branch, on every push to main
```
