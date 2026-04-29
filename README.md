# Dubrefjord blog — favicon + 404 drop-in

These files slot directly into your Minimal Mistakes Jekyll repo.
Preserve the directory structure exactly as shown below; the paths
are what Liquid `{{ '/assets/...' | relative_url }}` references resolve to.

```
your-jekyll-repo/
├── 404.md                              <- this file (custom 404 page)
├── _includes/
│   └── head/
│       └── custom.html                 <- favicon link tags
└── assets/
    └── images/
        ├── favicon.ico                 <- multi-res 16/32/48
        ├── favicon-16x16.png
        ├── favicon-32x32.png
        ├── favicon-48x48.png
        ├── apple-touch-icon.png        <- 180x180
        ├── android-chrome-192x192.png
        ├── android-chrome-512x512.png
        └── site.webmanifest
```

## How the favicons are wired up

Minimal Mistakes' default `_includes/head.html` ends with
`{% include head/custom.html %}`. That means every page automatically
picks up the link tags in `_includes/head/custom.html` — no further
config needed.

## How the 404 page works

GitHub Pages automatically serves `/404.html` for any unmatched URL,
which Jekyll generates from `404.md` because of the front matter
`permalink: /404.html`.

To preview locally:

```bash
bundle exec jekyll serve
# then visit http://localhost:4000/this-page-does-not-exist
```

## How the favicons were made

The PNGs were rendered from the cover slide of the Langsec deck
(slide 1, top-right corner mark) at 600 DPI, cropped to the logo
bounding box with a small padding, then resampled with Lanczos to
each target size on a `#1A1C34` (deep brand navy) background.

If you ever want to regenerate with a different background or padding,
the source crop sits at master 1024×1024 and downsamples cleanly
to all required sizes.
