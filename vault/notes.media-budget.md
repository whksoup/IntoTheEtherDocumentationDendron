---
id: d2d6721c-74a0-4ce6-aa40-40502d0a2626
title: A budget for images and video
desc: "GitHub Pages caps a published site at 1 GB, so video gets embedded, not committed."
updated: 1788417991064
created: 1788417991064
tags: [meta, media, performance]
---

Git stores every version of every binary you commit forever. A repository
that accumulates screenshots recompressed a few times gets slow to clone and
never gets smaller, because deleting the file leaves the history intact.

## Images

Live in `vault/assets/images/`, referenced with normal markdown image syntax.
Convert to WebP, cap the long edge at 1600 px, keep files under about 300 KB,
and always write real alt text.

```md
![Replace this with a real description.](assets/images/placeholder.webp)
```

## Video

Host it somewhere built for it and embed the player with raw HTML, which
Dendron's publish pipeline passes through:

```html
<div class="video-embed">
  <iframe src="https://www.youtube-nocookie.com/embed/VIDEO_ID"
          title="What it shows" loading="lazy" allowfullscreen></iframe>
</div>
```

A three-minute clip at decent quality can eat several percent of the site's
entire 1 GB allowance — see [[GitHub Pages limits|sources.github-pages-limits]].
Self-hosting is reasonable only for a silent loop under about 5 MB.
