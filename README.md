# layer-versatiles-style

The [@versatiles/style](https://github.com/versatiles-org/versatiles-style)
MapLibre style generator for the Shortbread vector-tile schema, bundled locally
for the OpenCharly versa image.

The `versatiles-style` candy installs nodejs + npm and lands the browser-ready
`@versatiles/style` bundle under `/opt/versatiles-style/` (GitHub release tarball
first, npm-install fallback). The package generates
`colorful()` / `eclipse()` / `graybeard()` / `neutrino()` / `shadow()` /
`satellite()` style JSON for maps backed by Shortbread. Installing it locally
lets the notebook's MapLibre HTML import the styles from a local file instead of
a runtime CDN (unpkg.com). The bundle is re-served as static JS by the
versatiles-frontend layer at `/style/versatiles-style.js`.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `versatiles-style` |
| Install path | `/opt/versatiles-style/` |
| Bundle | `versatiles-style*.js` (browser-ready) |
| Build deps | `nodejs`, `npm` (arch / fedora) |
| Re-exported at | `/style/versatiles-style.js` by the versatiles-frontend layer |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-versa-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-versatiles-style:v2026.243.0508'
```

Then, from a notebook iframe, import the generators from the re-exported bundle:

```html
<script src="http://127.0.0.1:28002/style/versatiles-style.js"></script>
```

The candy's `plan:` asserts a non-empty `versatiles-style*.js` bundle under the
install path, the `nodejs` package, `node --version` reporting a version, and the
install directory.

## Layout

- `charly.yml` — the `versatiles-style:` candy entity (the `require:`, the
  nodejs/npm packages, the two-tier install `run:` step, the `check:`
  assertions) and the embedded `versatiles-style-skill:` skill entity.
- `CHANGELOG/` — per-CalVer release history.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-versa:versatiles-style`
- `/charly-versa:versa` — the image composing this layer
- `/charly-versa:versatiles` — the tile-server backend the generated styles point at after URL patching
- `/charly-versa:versatiles-frontend` — re-exports this bundle at `/style/`
- `/charly-versa:shortbread` — the tile schema the styles render
- `/charly-versa:notebook-osm` — the shortbread MapLibre cell that imports `colorful()`
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
