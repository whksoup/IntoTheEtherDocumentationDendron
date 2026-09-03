# Working Notes — Dendron workspace

A hierarchical notebook authored in Dendron and published as a static site
to GitHub Pages via Dendron's Next.js publishing pipeline.



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
