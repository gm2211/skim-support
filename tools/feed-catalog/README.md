# Discover feed catalog

`discover/catalog.json` is the directory of live feeds by topic that Skim's Discover shows on
desktop and iOS. The `Rebuild Discover feed catalog` workflow regenerates it every Monday, and
whenever `sources.json` or `build.mjs` change, by fetching every candidate feed and keeping the
ones that parse, are not podcasts, and posted recently. GitHub Pages serves it at
https://gm2211.github.io/skim-support/discover/catalog.json.

`build.mjs` and `sources.json` are copies of `tools/feed-catalog/` in the app repo, which also
bundles a snapshot as the offline fallback. To add feeds, edit `sources.json` here (the app picks
it up within a day) and copy it back to the app repo before the next release.

```bash
node tools/feed-catalog/build.mjs --out discover/catalog.json --report discover/report.json
```
